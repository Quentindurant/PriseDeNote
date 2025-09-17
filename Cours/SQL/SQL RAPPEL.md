
SQL.sh

ordre des requettes :

SELECT *
FROM table
WHERE condition
GROUP BY expression  -> groupé par column
HAVING condition
{ UNION | INTERSECT | EXCEPT }
ORDER BY expression  -> trié dans un ordre (ascendant, déscendant)
LIMIT count
OFFSET start -> pour la pagination (ex : limte 20 offset 20 pour commencer la 2 eme page a la 20 valeur )

SELECT DISTINCT  -> éviter les doublons

### Description des instructions

- `SELECT DISCINCT` : supprime les doublons
- `WHERE` : permet de poser une condition - filtrer les résultats. Les opérateurs possibles utilisables avec la clause WHERE :

|Opérateur|Description|
|---|---|
|=|Égale|
|<>|Pas égale|
|!=|Pas égale|
|>|Supérieur à|
|<|Inférieur à|
|>=|Supérieur ou égale à|
|<=|Inférieur ou égale à|
|IN|Liste de plusieurs valeurs possibles|
|BETWEEN|Valeur comprise dans un intervalle donnée (utile pour les nombres ou dates)|
|LIKE|Recherche en spécifiant le début, milieu ou fin d'un mot|
|IS NULL|Valeur est nulle|
|IS NOT NULL|Valeur n'est pas nulle|

- `WHERE ... AND ...` : Permet d'ajouter plusieurs conditions
- `WHERE ... OR ...` : Permet d'ajouter plusieurs conditions optionnelles
- `WHERE ... IN ...` : Permet de filtrer sur une liste d'éléments
- `WHERE ... BETWEEN ...` : Permet de filtrer entre 2 valeurs
- `WHERE ... IS NULL ...` : Permet de filtrer sur les champs "NULL"
- `WHERE ... LIKE ...` : Permet de filtrer sur les chaines de caractères. Voici les utilisations possibles

|Modèle|Description|Exemples correspondants|
|---|---|---|
|`LIKE '%a'`|Recherche toutes les chaînes qui **se terminent par “a”**|`pizza`, `salsa`|
|`LIKE 'a%'`|Recherche toutes les chaînes qui **commencent par “a”**|`avion`, `arbre`|
|`LIKE '%a%'`|Recherche toutes les chaînes qui **contiennent “a”**|`chat`, `manger`|
|`LIKE 'pa%on'`|Recherche les chaînes qui **commencent par “pa” et se terminent par “on”**|`pantalon`, `pardon`|
|`LIKE 'a_c'`|Le caractère `_` représente **un seul caractère** (contrairement à `%`)|`aac`, `abc`, `azc`|

## Exemples de requêtes pour pratique sur la BDD WORLD

- `SELECT DISTINCT state_code FROM cities;` (1185)
- `SELECT * FROM cities WHERE state_code = "07";` (435)
- `SELECT * FROM cities WHERE state_code = "07" AND country_code = "AD";` (0)
- `SELECT * FROM cities WHERE state_code = "07" OR country_code = "AD";` (444)
- `SELECT * FROM cities WHERE latitude > 42 AND longitude > 1.5;` (53085)
- `SELECT * FROM cities WHERE latitude < 20 AND longitude > 50;` (15814)
- `SELECT * FROM cities WHERE latitude > 42 AND longitude > 1.5 OR latitude < 20 AND longitude > 50;` (68899)
- `SELECT * FROM cities WHERE (latitude > 42 AND longitude > 1.5) OR (latitude < 20 AND longitude > 50);` (68899)
- `SELECT * FROM cities WHERE country_code IN ("AD", "AE");` (49)
- `SELECT * FROM cities WHERE latitude BETWEEN 20 AND 30;` (10235)
- `SELECT * FROM countries WHERE wikiDataId IS NULL;` (47)
- `SELECT * FROM countries WHERE wikiDataId IS NOT NULL;` (203)
- `SELECT * FROM cities WHERE name LIKE 'a%';` (9002)
- `SELECT * FROM cities WHERE name LIKE '%a';` (25624)
- `SELECT * FROM cities WHERE name LIKE '%zw%';` (76)
- `SELECT * FROM cities WHERE name LIKE '%c_t%';` (1973)
  
  ## TP 1

En individuel, vous allez devoir continuer, ce fichier readme :

- Vous créez votre propre fichier, a part
- Vous traitez un maximum de cas de figure sur le site sql.sh
- Vous ne faites ni de jointure, ni de procédures stockées, ni de trigger

Vous allez devoir pour chaque instruction que l'on n'a pas vu :

1. expliquer l'instruction rapidement
2. en vous servant de la base de données "SAKILA", vous allez créer 1 à 3 cas defigure nécessitants une requete. Par exemple :"Récupérer tous les state_code de la table cities sans aucun doublon". Vous devrez ensuite écrire la requete SQL correspondante, par exemple : `SELECT DISTINCT state_code FROM cities;`. Notez le nombre de résultats obtenus par exemple (1185).



## TP1

- GROUPE BY :
	- SELECT rental_duration, rental_rate FROM `film` GROUP BY rental_duration;
	- ça évite les doublons comme le SELECT Distinct. On doit utiliser having et pas where. ![[Pasted image 20250916122815.png]]

- HAVING : 
	- SELECT rental_duration, rental_rate FROM `film` GROUP BY rental_duration HAVING rental_rate <3;
	- là le HAVING est un where qui nous permet de mettre une condition a notre groupe by (sum(), count(), avg())
	- ![[Pasted image 20250916122924.png]]

- CASE : 
	- permet d'utilise des condition comme dans un language rapide directement sur le SGBD ce qui va etre plus rapide qu'un appel extérieur.

- UNION : 
	- Permet de mettre le résultat de deux requettes sans doublons
	- ![[Pasted image 20250916140443.png]]
- UNION ALL : 
	- c'est un UNION qui fais même les doublons

- INTERSECT :
	- Nativement pas sur Mysql mais permet d'afficher les résultat commun aux 2 requettes.
	- Alternative Mysql : 
		  SELECT DISTINCT value FROM `table1` WHERE value IN (SELECT value FROM `table2`  );
		  
	 ![[Pasted image 20250916141938.png]]

- ALLIAS (AS) : 
	- A peux près comme sur un linux, ça permet de changer le nom d'une colonne ou table mais TEMPORAIREMENT.  C'est donc plus explicite. La présence du AS n'est pas obligatoire mais est très conseillé
	- ![[Pasted image 20250916142830.png]]

- EXCEPT/MINUS : 
	- Permet d'avoir les résultat de la table 1 sans les résultats la table 2 et qui sont commun a la table 2 (MINUS: SQL, Oracle / EXCEPT : POSTGRE)
	- ![[Pasted image 20250916144043.png]]

- INSERT INTO:
	- Permet de rajouter des valeur dans la table 
	- INSERT INTO client (prenom, nom, ville, age)
	 VALUES
	 ('Rébecca', 'Armand', 'Saint-Didier-des-Bois', 24),
	 ('Aimée', 'Hebert', 'Marigny-le-Châtel', 36),
	 ('Marielle', 'Ribeiro', 'Maillères', 27),
	 ('Hilaire', 'Savary', 'Conie-Molitard', 58);


### Jointure

![[Pasted image 20250916151605.png]]


Info importante: La zonne commune a A et B n'est pas les données en commun en la table A et B mais les lignes de colonnes crées par la liaison des tables (PK et FK)

Table A :
┌────-─┐
│  A  │ ==PK==   |
├────-─┤
│ a1  │ ==pA1== |
│ a2  │ ==pA2==|
│ a3  │==PA3== |
└────-─┘

Table B :
┌─────-┐
│  B  │==FK==    |
├─────-┤
│ b2  │==fB2==  |
│ b3  │==fB3== |
│ b4  │==fb4== |
└─────-┘


# SQL JOINS — Récapitulatif visuel (Inclue le TP 2)


## LEFT JOIN inclusive
![LEFT JOIN inclusive](Pasted%20image%2020250916161140.png)  
Toutes les lignes de la table **A** avec les lignes non null  en relation de la table **B**.
	SELECT * FROM film AS A 
	LEFT JOIN language AS B 
	ON A.language_id = B.language_id;
	

---

## LEFT JOIN exclusive
![LEFT JOIN exclusive](Pasted%20image%2020250916160545.png)  
Toutes les lignes de la table **A** (dont les FK null de la table B) qui ne sont pas en relation avec la table **B**.
	SELECT * FROM film AS A
	LEFT JOIN language AS B 
	ON A.language_id = B.language_id 
	WHERE A.language_id IS NULL;

---

## RIGHT JOIN inclusive
![RIGHT JOIN inclusive](Pasted%20image%2020250916160621.png)  
Toutes les lignes de la table **B** avec les lignes non null  en relation de la table **A**.
	SELECT * FROM film AS A 
	RIGHT JOIN language AS B 
	ON A.language_id = B.language_id;

---

## RIGHT JOIN exclusive
![RIGHT JOIN exclusive](Pasted%20image%2020250916161359.png)  
Toutes les lignes de la table **B** (dont les FK null de la table B) qui ne sont pas en relation avec la table **A**.
	SELECT * FROM film AS A
	RIGHT JOIN language AS B 
    ON A.language_id = B.language_id 
	WHERE A.language_id IS NULL;

---

## FULL OUTER JOIN inclusive
![FULL OUTER JOIN inclusive](Pasted%20image%2020250916161521.png)  
Toutes les lignes des tables **A** et **B**, qu’elles soient en relation ou non.
	SELECT * FROM film AS A 
	OUTER JOIN language AS B 
	ON A.language_id = B.language_id; 
	(ne fonctionne pas car outer est inconnu en mysql)

---

## FULL OUTER JOIN exclusive
![FULL OUTER JOIN exclusive](Pasted%20image%2020250916161556.png)  
Toutes les lignes des tables **A** et **B**, sauf celles qui sont en relation (pas l’intersection).
	SELECT * FROM film AS A 
	OUTER JOIN language AS B 
	ON A.language_id = B.language_id; 
	WHERE A.language_id IS NULL;
	(ne fonctionne pas car outer est inconnu en mysql)

---

## INNER JOIN
![INNER JOIN](Pasted%20image%2020250916161757.png)  
Seulement les lignes qui sont en relation entre **A** et **B**.
	SELECT * FROM film AS A 
	INNER JOIN language AS B 
	ON A.language_id = B.language_id;
	« Affiche les films avec leur langue » → un film sans langue ne doit pas apparaître.
