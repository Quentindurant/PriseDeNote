### Structure de `clients`


```json
{
    "nom":"string",
    "prenom":"string",
    "est_actif":"boolean",
    "age":"int"
}
```

### Structure de `commandes`


```json
{
    "id_client":"int",
    "produit":"string",
    "quantite":"int",
    "est_validee":"boolean"
}
```

**Note** :En NoSQL,il n’y a pas de clé étrangère stricte :vous simulerez une relation avec id_client

## Étape 3 — Insertion massive


Insérez 1 millions de documents dans chaque collection,avec des valeurs aléatoires :

- nom et prenom → générés aléatoirement (ex :Faker.js,Python Faker,ou script maison)
- est_actif / est_validee → aléatoire (true/false)
- id_client → compris entre 1 et 1 000 000
- quantite → compris entre 1 et 10

![[Pasted image 20251030102409.png]]
3 minutes

## Étape 4 — Requêtes de test


Exécutez les requêtes suivantes et notez le temps d’exécution :

### 1. Lire toutes les lignes

```js
db.clients.find()
```

### 2. Lire tous les documents avec est_actif:true


```js
db.clients.find({ est_actif:true })
```

### 3. Lire tous les documents avec est_actif:false


```js
db.clients.find({ est_actif:false })
```

### 4. Trier tous les clients par nom DESC

```js
db.clients.find().sort({ nom:-1 })
```

### 5. Trier tous les clients par nom ASC


```js
db.clients.find().sort({ nom:1 })
```

### 6. Simuler une jointure entre clients et commandes


```js
db.clients.aggregate([
    {
        $lookup:{
        from:"commandes",
        localField:"_id",
        foreignField:"id_client",
        as:"commandes_client"
        }
    }
])
```

Observez la différence :la jointure n’existe pas nativement en NoSQL,elle est simulée via $lookup

## Étape 5 — Mise à jour de masse


### 1. Changer tous les booléens à false


```js
db.clients.updateMany({},{ $set:{ est_actif:false } })
db.commandes.updateMany({},{ $set:{ est_validee:false } })
```

### 2. Incrémenter tous les id_client de 1



```js
db.commandes.updateMany(
    {},
    [{ $set:{ id_client:{ $add:["$id_client",1] } } }]
)
```

## Étape 6 — Indexation

Créez des index :

```js
db.clients.createIndex({ nom:1 })
db.clients.createIndex({ est_actif:1 })
```

Rejouez toutes les requêtes de l’étape 4

Notez les nouveaux temps d’exécution et comparez avec les précédents.


J'AI TOUT FAIS EN SCRIPT DONC TIEN LES RESULTAT
![[Pasted image 20251030135119.png]]
![[Pasted image 20251030135124.png]]
![[Pasted image 20251030135127.png]]

![[Pasted image 20251030135044.png]]
## Etape 7


Rédigez un court paragraphe de conclusion :

- Quelles différences avez-vous observées entre MongoDB et les bases SQL (MySQL,SQLite,PostgreSQL) ? 
	- Personnelement, j'ai pas trop aimer l'expérience par rapport aux bases SQL. Je comprend le principe de 'ça va plus vite sans structure' mais pour moi, une bdd doit avoir une bonne structure. Après j'avais bien aimer Firebase quand ej l'avais utiliser mais là mongodb, j'ai pas aimer.
- Dans quels cas MongoDB est-il plus performant ?
	- je trouve que c’est mieux quand t’as beaucoup d’écritures ou de donnée qui changent souvent. C’est rapide pour stocker et lire des gros volume sans se prendre la tête avec un schéma fixe.
- Dans quels cas est-il moins adapté ?
	- Quand t’as besoin de vraies relations entre les données ou de requêtes complexes avec jointures. Pour tout ce qui est compta, gestion, c’est pas le top.
- Quels avantages et inconvénients avez-vous notés (syntaxe,flexibilité,contraintes) ?
	- La syntaxe JSON est simple et flexible, t’ajoutes des champs comme tu veux. Par contre, y’a peu de contraintes, donc tu peux vite foutre le bazar si t’es pas rigoureux.