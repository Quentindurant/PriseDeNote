- Créer 2 tables, avec 4 colonnes chacunes : ![Créer 2 tables](./Pasted%20image%2020251029142854.png)
- 1 relation de la table A vers la table B :
- 1 colonne devra être un boolean randomisé vrai/faux :
- 2 colonnes noms / prénoms (je select from pour vérifier le resultat) :

## MYSQL :

## Etape 3

- Insérer 5 millions de lignes pour chaque table (randomisées en terme de contenu) : 17,594 sec + 27,863 sec  
  ![Insert 5M 1](./Pasted%20image%2020251029142728.png) ![Insert 5M 2](./Pasted%20image%2020251029142854.png)

- Requêter toutes les lignes 0,275 sec  
  ![All rows 1](./Pasted%20image%2020251029143059.png) ![All rows 2](./Pasted%20image%2020251029143118.png) ![All rows 3](./Pasted%20image%2020251029143310.png) ![All rows 4](./Pasted%20image%2020251029143315.png)

- Requêter tous les boolean true : 2.432 sec  
  ![True 1](./Pasted%20image%2020251029143451.png) ![True 2](./Pasted%20image%2020251029143456.png) ![True 3](./Pasted%20image%2020251029143519.png) ![True 4](./Pasted%20image%2020251029143521.png)

- Requêter tous les boolean false : 1.839 sec  
  ![False 1](./Pasted%20image%2020251029143905.png) ![False 2](./Pasted%20image%2020251029143908.png) ![False 3](./Pasted%20image%2020251029144016.png) ![False 4](./Pasted%20image%2020251029144020.png)

- Requêter toutes les lignes en ordonnant par ordre alphabétique DESC sur le nom : 2.024 sec  
  ![Order DESC 1](./Pasted%20image%2020251029144137.png) ![Order DESC 2](./Pasted%20image%2020251029144140.png) ![Order DESC 3](./Pasted%20image%2020251029144143.png) ![Order DESC 4](./Pasted%20image%2020251029144145.png)

- Requêter toutes les lignes en ordonnant par ordre alphabétique ASC sur le nom : 2.122 sec  
  ![Order ASC 1](./Pasted%20image%2020251029144247.png) ![Order ASC 2](./Pasted%20image%2020251029144249.png) ![Order ASC 3](./Pasted%20image%2020251029144251.png) ![Order ASC 4](./Pasted%20image%2020251029144254.png)

- Requêter toutes les lignes avec les jointures : 14.838 sec  
  ![Join 1](./Pasted%20image%2020251029144610.png) ![Join 2](./Pasted%20image%2020251029144616.png)

## Etape 4

- Faire un update sur toutes les lignes pour changer le boolean à false : 17,3659 sec  
  ![Update boolean 1](./Pasted%20image%2020251029144756.png) ![Update boolean 2](./Pasted%20image%2020251029144801.png)

- Faire un update sur toutes les lignes pour changer la FK en faisant un "+1" à chaque fois, et si c'est à 5000000 on la repasse à 1. : 38,157 sec  
  ![Update FK](./Pasted%20image%2020251029145049.png)

## Etape 5

- Créer des index sur les colonnes `nom` et `boolean` des deux tables. : 12,563 sec
- Recommencer les mêmes requêtes et noter les nouveaux temps
  - Requêter toutes les lignes 0.153 sec
  - Requêter tous les boolean true : 0
  - Requêter tous les boolean false : 1,017 sec
  - Requêter toutes les lignes en ordonnant par ordre alphabétique DESC sur le nom : 0.52 sec
  - Requêter toutes les lignes en ordonnant par ordre alphabétique ASC sur le nom : 0.63 sec
  - Requêter toutes les lignes avec les jointures : Total query runtime: 50 msec

---

## POSTGRE

- Créer 2 tables, avec 4 colonnes chacunes : 37 msec  
  ![PG create](./Pasted%20image%2020251029141537.png)
- 1 relation de la table A vers la table B : 37 msec
- 1 colonne devra être un boolean randomisé vrai/faux : 4 msec
- 2 colonnes noms / prénoms (je select from pour vérifier le resultat) : 2 msec

## Etape 3

- Insérer 5 millions de lignes pour chaque table (randomisées en terme de contenu) = Inserted row id: 7 secs 828 msec  
  ![PG insert](./Pasted%20image%2020251029141607.png)
- Requêter toutes les lignes Total query runtime: 1 secs 444 msec  
  ![PG all rows](./Pasted%20image%2020251029141715.png)
- Requêter tous les boolean true : Total query runtime: 800 msec  
  ![PG true](./Pasted%20image%2020251029141740.png)
- Requêter tous les boolean false : Total query runtime: 737 msec  
  ![PG false](./Pasted%20image%2020251029141753.png)
- Requêter toutes les lignes en ordonnant par ordre alphabétique DESC sur le nom : Total query runtime: 5 secs 609 msec  
  ![PG desc](./Pasted%20image%2020251029141802.png)
- Requêter toutes les lignes en ordonnant par ordre alphabétique ASC sur le nom : Total query runtime: 3 secs 219 msec  
  ![PG asc](./Pasted%20image%2020251029141825.png)
- Requêter toutes les lignes avec les jointures : Total query runtime: 5 secs 927 msec  
  ![PG join](./Pasted%20image%2020251029141858.png)

## Etape 4

- Faire un update sur toutes les lignes pour changer le boolean à false — Query took  
  ![PG update boolean](./Pasted%20image%2020251029142105.png)
- Faire un update sur toutes les lignes pour changer la FK en faisant un "+1" à chaque fois, et si c'est à 5000000 on la repasse à 1. — successfully in 33 msec  
  ![PG update FK](./Pasted%20image%2020251029142124.png)

## Etape 5

- Créer des index sur les colonnes `nom` et `boolean` des deux tables. : 4 secs 70 msec  
  ![PG index](./Pasted%20image%2020251029142135.png)
- Recommencer les mêmes requêtes et noter les nouveaux temps
  - Requêter toutes les lignes — Total query runtime: 1 secs 226 msec  
    ![PG all rows 2](./Pasted%20image%2020251029142144.png)
  - Requêter tous les boolean true : 0
  - Requêter tous les boolean false — 1 secs 519 msec  
    ![PG false 2](./Pasted%20image%2020251029142156.png)
  - Requêter DESC — Total query runtime: 1 secs 518 msec  
    ![PG desc 2](./Pasted%20image%2020251029142210.png)
  - Requêter ASC — Total query runtime: 1 secs 493 msec  
    ![PG asc 2](./Pasted%20image%2020251029142220.png)
  - Requêter jointures — 5 secs 927 msec  
    ![PG join 2](./Pasted%20image%2020251029142237.png)

---

## SQLITE

## Etape 3

- Insérer 5 millions de lignes pour chaque table (randomisées en terme de contenu) = Inserted row id: 38 sec  
  ![SQLite insert](./Pasted%20image%2020251029152009.png)
- Requêter toutes les lignes — Total query runtime: 16 sec  
  ![SQLite all rows](./Pasted%20image%2020251029152049.png)
- Requêter tous les boolean true : 8,659 sec  
  ![SQLite true](./Pasted%20image%2020251029152137.png)
- Requêter tous les boolean false : 8,652 sec  
  ![SQLite false](./Pasted%20image%2020251029152159.png)
- Requêter DESC — Total query runtime: 18,651 sec  
  ![SQLite desc](./Pasted%20image%2020251029152251.png)
- Requêter ASC — Total query runtime: 18,762 sec  
  ![SQLite asc](./Pasted%20image%2020251029152347.png)
- Requêter avec les jointures — Total query runtime: 4,684 sec  
  ![SQLite join](./Pasted%20image%2020251029152524.png)

## Etape 4

- Faire un update sur toutes les lignes pour changer le boolean à false — Query took 1 : 10.990 sec  
  ![SQLite update boolean](./Pasted%20image%2020251029153109.png)
- Faire un update sur toutes les lignes pour changer la FK en faisant un "+1" à chaque fois, et si c'est à 5000000 on la repasse à 1. : 4.252 sec  
  ![SQLite update FK](./Pasted%20image%2020251029153137.png)

## Etape 5

- Créer des index sur les colonnes `nom` et `boolean` des deux tables. : 4.256 sec  
  ![SQLite index](./Pasted%20image%2020251029152635.png)
- Recommencer les mêmes requêtes et noter les nouveaux temps
  - Requêter toutes les lignes — Total query runtime: 16.928 sec  
    ![SQLite all rows 2](./Pasted%20image%2020251029152724.png)
  - Requêter tous les boolean true :  
    ![SQLite true 2](./Pasted%20image%2020251029152802.png)
  - Requêter tous les boolean false : 8.534 sec  
    ![SQLite false 2](./Pasted%20image%2020251029152832.png)
  - Requêter DESC — Total query runtime: 19.126 sec  
    ![SQLite desc 2](./Pasted%20image%2020251029152916.png)
  - Requêter ASC — Total query runtime: 17.146 sec  
    ![SQLite asc 2](./Pasted%20image%2020251029152947.png)
  - Requêter jointures : 12.245 sec

---

## Etape 6

**SQLITE** → Pratique pour des petits projets sans configuration, rivalise avec MySQL en local mais moins adapté aux très grosses BDD.  
**MYSQL** → Intermédiaire, simple via phpMyAdmin, bien documenté, idéal projets moyens / perso.  
**PostgreSQL** → Robuste et performant, excellent pour requêtes complexes et usages pro (pgAdmin très complet), configuration plus lourde.
