
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




REQUETE DE BASE :

### Jouer avec les bases de données

- `SHOW DATABASES` : Permet de voir la liste des BDD
- `CREATE DATABASE <name>` : Permet de créer une BDD
- `USE <database>` : Permet de "rentrer" dans une BDD en CLI pour interagir avec
- `DROP DATABASE <name>` : Permet de supprimer une BDD

### Jouer avec les tables

- `CREATE TABLE <table>` : Permet de créer une table
- `ALTER TABLE <table>` : Permet de MAJ une table
- `DROP TABLE <table>` : Permet de supprimer une table
- `SHOW TABLES` : Permet de voir la liste des tables
- `DESCRIBE <table>` : Permet de décrire les colonnes d'une table
- `TRUNCATE <table>` : Supprime les données dans une table

### Jouer avec les données

- `INSERT INTO <table> (colonne1, colonne2, ...) VALUES ('valeur 1', 'valeur 2', ...)` : Permet d'insérer des données dans une table
- `UPDATE <table> SET colonne1 = 'nouvelle valeur' WHERE ...` : Permet de mettre à jour des données dans une table
- `DELETE FROM <table> WHERE ....` : Permet de supprimer des données dans une table

## TP 3

- Sélectionner tous les employés : SELECT * FROM employees;
- Sélectionner tous les employés par leurs noms et prénoms : SELECT first_name, last_name FROM employees;
- Sélectionner les noms distincts des employés : SELECT DISTINCT last_name FROM employees;
- Sélectionner les noms et prénoms distincts des employés : SELECT DISTINCT last_name , first_name FROM employees;
- Sélectionner les noms et prénoms des employés dont le nom est « alencar » : SELECT first_name, last_name FROM employees WHERE last_name = 'alencar';
- Sélectionner les employés dont le nom est « alencar » et de sexe masculin : SELECT last_name, gender FROM employees WHERE last_name = 'alencar' AND gender = 'M';
- Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « OR » : SELECT first_name FROM employees WHERE first_name ='Danai' OR first_name ='Leen';
- Sélectionner les employés dont le prénom « Danai » ou « Leen » en utilisant « IN » : SELECT first_name FROM employees WHERE first_name IN ('Danai','Leen');
- Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « OR » : SELECT first_name, last_name FROM employees WHERE last_name = 'alencar' AND (first_name = 'Danai' OR first_name = 'Leen');
- Sélectionner les employés dont le nom est « alencar » et le prénom « Danai » ou « Leen » en utilisant « IN » : SELECT first_name, last_name FROM employees WHERE first_name IN ('Danai','Leen') AND last_name = 'alencar';

- Sélectionner les employés dont le numéro d’employé est compris entre 50000 et 50150 : SELECT emp_no FROM `employees` WHERE emp_no > 50000 AND emp_no < 50150;
- Sélectionner les employés dont le nom est « alencar » et le numéro d’employé est compris entre 50000 et 60000 : SELECT emp_no, last_name FROM `employees` WHERE last_name = 'alencar' AND emp_no > 50000 AND emp_no < 60000; OU SELECT emp_no, last_name FROM employees WHERE last_name = 'alencar'
  AND emp_no BETWEEN 50001 AND 60000;
- Sélectionner les employés dont le nom est « alencar » et le prénom est « danai » ou le numéro d’employé est compris entre 50000 et 60000 : SELECT emp_no, last_name, first_name FROM employees WHERE last_name = 'alencar' AND first_name = 'danai' OR emp_no BETWEEN 50001 AND 60000 
- Sélectionner les employés dont le nom est « alencar » ou, le prénom est « danai » ou « leen » et le numéro d’employé est compris entre 50000 et 60000 : SELECT emp_no, first_name, last_name FROM employees WHERE last_name = 'alencar' OR (first_name IN ('Danai', 'Leen') AND emp_no BETWEEN 50000 AND 60000);

- Sélectionner les employés dont le prénom commence par un « T » : SELECT emp_no, first_name FROM employees WHERE first_name LIKE 'T%';
- Sélectionner les employés masculin dont la deuxième lettre du prénom est un « T » : SELECT emp_no, first_name, gender FROM employees WHERE gender = 'M' AND first_name LIKE '_T%'
- Sélectionner les employés dont le nom est « alencar » et le prénom « danai » ou le numéro d’employé commence par un 5 : SELECT emp_no, first_name, last_name FROM employees WHERE last_name = 'alencar' AND (first_name = 'Danai' OR emp_no LIKE '5%');
- Sélectionner les employés dont le prénom commence par un « T » et termine par un « B » : SELECT emp_no, first_name FROM employees WHERE first_name LIKE 'T%B';
- Sélectionner les employés dont le prénom commence par un « T », la 3ème lettre est un « R » : SELECT emp_no, first_name FROM employees WHERE first_name LIKE 'T_R%';
- Sélectionner les employés dont le prénom commence par un « T », la 3ème lettre est un « R » et le numéro d’employé est compris entre 50000 et 60000 : SELECT emp_no, first_name FROM employees WHERE first_name LIKE 'T_R%' AND emp_no BETWEEN 50000 AND 60000;
- Sélectionner les employés dont le prénom contient « TZV » : SELECT emp_no, first_name FROM employees WHERE first_name LIKE '%TZV%';
- Sélectionner les employés masculin ou dont le numéro d’employé est compris entre 50000 et 60000 et, le prénom contient « TZV » : SELECT emp_no, first_name, gender FROM employees WHERE gender = 'M' OR (emp_no BETWEEN 50000 AND 60000 AND first_name LIKE '%TZV%');
- Sélectionner les employés dont le prénom termine par « CAL» SELECT emp_no, first_name FROM employees WHERE first_name LIKE '%CAL';
- Sélectionner les employés dont le prénom termine par « CAL» de genre masculin et dont le numéro d’employé est compris entre 50000 et 60000 : SELECT emp_no, first_name, gender FROM employees WHERE first_name LIKE '%CAL' AND gender = 'M' AND emp_no BETWEEN 50000 AND 60000;
- Sélectionner les employés dont le prénom est « danai » ou « leen » et le nom se termine par « TH» ou dont le numéro d’employé est compris entre 50000 et 100000 : SELECT emp_no, first_name, last_name FROM employees WHERE (first_name IN ('Danai', 'Leen') AND last_name LIKE '%TH') OR emp_no BETWEEN 50000 AND 100000;
- Sélectionner les employés dont la date de naissance est null : SELECT emp_no, first_name, last_name, birth_date FROM employees WHERE birth_date IS NULL;

- Sélectionner le nombre d’employés par département : SELECT dept_no, COUNT(emp_no) FROM dept_emp GROUP BY dept_no;
- 
- Sélectionner le salaire maximum et minimum des employés : SELECT emp_no, MIN(salary), MAX(salary) FROM salaries
- Sélectionner le salaire maximum et minimum par employés : SELECT emp_no, MIN(salary), MAX(salary) FROM salaries GROUP BY emp_no;
- Sélectionner la moyenne de salaire par employés : SELECT emp_no, AVG(salary) FROM salaries GROUP BY emp_no;
- Sélectionner la moyenne de salaire par employés si leur numéro contient « 150 » : SELECT emp_no, AVG(salary) FROM salaries GROUP BY emp_no HAVING emp_no LIKE '%150%';
- Sélectionner le nombre d’employés par département avec un résumé général

- Sélectionner le nombre d’employés par département si leur numéro d’employé est compris entre 10000 et 50000 : SELECT dept_no, COUNT(emp_no) FROM dept_emp WHERE emp_no BETWEEN 10000 AND 50000 GROUP BY dept_no; 
- Sélectionner la moyenne, le minimum et le maximum des salaires par employé si leur numéro est compris entre 10005 et 10105 avec un résumé général : SELECT emp_no, MIN(salary), MAX(salary), AVG(salary) FROM salaries WHERE emp_no BETWEEN 10005 AND 10105 GROUP BY emp_no;
- Sélectionner le nombre d’employés par département pour les départements « d005 » et « d006 » : SELECT emp_no, dept_no FROM `dept_emp`WHERE dept_no = 'd005' OR dept_no ='d006';  --105824
- Sélectionner le nombre d’employés par département s’il est inférieur à 50000 : SELECT emp_no, dept_no FROM `dept_emp`WHERE emp_no < 50000; --44217
- Sélectionner la moyenne des salaires par employé si elle est comprise entre 40000 et 50000 : SELECT AVG (salary) FROM `salaries` WHERE salary BETWEEN 40000 AND 50000; --1
- Sélectionner la liste des employées en ordre alphabétique inversé de nom : SELECT first_name, last_name FROM `employees`ORDER BY last_name ASC; --299379
- Sélectionner la liste des employés en ordre alphabétique inversé de nom et en ordre alphabétique par prénom
- Sélectionner le nombre d’employés par département du plus petit au plus grand
- Sélectionner le salaire maximum et minimum des employés, utiliser des alias
- Sélectionner les 10 premiers employés
- Sélectionner les noms et prénoms des 10 premiers employés, utiliser des alias
- Sélectionner 10 employés à partir du 5ème
- Sélectionner les noms et prénoms des 10 premiers employés en ordre alphabétique par nom
- Sélectionner la somme des salaires pour les 10 premiers employés si la somme est inférieure à 50000
- Sélectionner la somme des salaires par employés si leur numéro est compris entre 10001 et 50000 et la somme est inférieure à 50000
- Sélectionner la somme des salaires pour les 10 premiers employés si leur numéro est compris entre 10001 et 50000 et la somme est inférieure à 50000
- Sélectionner les employés et afficher les catégories de département (d001 = « Département n°1 », d002 = « Département n°2 », …, d009 = « Département n°9 » et s’il n’y a pas de département) si le numéro d’employé est compris entre 10150 et 10200
- Sélectionner le nombre d’employés par département et afficher les catégories : supérieur à 50000 = « Élevé », supérieur ou égale à 20000 = « Correct », inférieur à 20000 = « Faible », utiliser des alias
- Sélectionner les moyennes des salaires par employés et afficher les catégories : supérieur à 100000 = « Très élevée », supérieur ou égale à 80000 = « Élevée », inférieur à 80000 = « Faible », utiliser des alias

### Requetes à faire obligatoirement avec des jointures

[](https://github.com/kevinniel/MDS-2526-B3-DW-SQL#requetes-%C3%A0-faire-obligatoirement-avec-des-jointures)

- Sélectionner les noms, prénoms et numéros des employés et leur département actuel (INNER JOIN)
- Sélectionner les prénoms, noms et titres actuels des employés (INNER JOIN)
- Sélectionner les noms, prénoms et salaires des employés en Juin 1989 (INNER JOIN)
- Sélectionner les noms, prénoms et départements actuels des managers (INNER JOIN)
- Sélectionner les noms, prénoms et dates de début d'emploi des employés avec leur département (INNER JOIN)
- Sélectionner les noms et départements des employés ayant le même département que les managers ayant été embauchés après le 1er Janvier 1996 (INNER JOIN et Sous-requêtes)
- Sélectionner les employés et leur date d'embauche dans les départements où le salaire moyen est supérieur à 80000 (INNER JOIN et Sous-requêtes)
- Sélectionner les employés et les départements (CROSS JOIN)
- Sélectionner les postes actuels des employés avec les noms des départements (CROSS JOIN)
- Sélectionner les dates d'emploi des employés et les noms des départements (JOIN et CROSS JOIN)
- Sélectionner les noms, prénoms, dates d’embauche et départements des employés même s’ils n’ont pas de département associé (LEFT JOIN)
- Sélectionner les noms, prénoms et titres des employés même s’ils n’ont pas de titre associé (LEFT JOIN)
- Sélectionner les noms, prénoms et salaires des employés depuis 1985 (LEFT JOIN)
- Sélectionner les noms, prénoms et départements des employés même s’ils n’ont pas de département associé (RIGHT JOIN)
- Sélectionner les noms, prénoms et salaires des employés depuis 1985 (RIGHT JOIN)
- Sélectionner les noms, prénoms et titres des employés même s’ils n’ont pas de titre associé (RIGHT JOIN)

### Requetes à faire obligatoirement avec des sous-requetes

[](https://github.com/kevinniel/MDS-2526-B3-DW-SQL#requetes-%C3%A0-faire-obligatoirement-avec-des-sous-requetes)

- Sélectionner les prénoms et noms des employés qui ne sont pas ou n’ont pas été managers, utiliser des alias
- Sélectionner les prénoms et noms des employés qui ont eu plus de 2 titres professionnels différents
- Sélectionner les numéros, prénoms et noms des employés qui ont eu un salaire compris entre 100000 et 150000
- Sélectionner les numéros, prénoms et noms des employés qui ont eu un salaire supérieur à 150000 et qui ne sont pas ou n’ont pas été managers
- Sélectionner les numéros des employés managers qui ont un salaire inférieur à 100000 et qui ont eu plus de 2 titres professionnels
- Sélectionner les noms des employés ayant été managers d'un département, utiliser des alias pour les résultats et l’appel des tables (EXISTS)
- Sélectionner les noms des employés pour qui il existe un salaire supérieur à 100000, utiliser des alias pour les résultats et l’appel des tables (EXISTS)
- Sélectionner les noms des employés féminins ayant occupé un poste de manager, utiliser des alias (EXISTS)
- Sélectionner les noms et prénoms des employés ayant eu un salaire supérieur à 100000, utiliser des alias (EXISTS)
- Sélectionner les numéros, noms et prénoms des employés nés le 1er janvier 1960 pour qui il existe exactement deux titres professionnels différents au cours de leur carrière, utiliser des alias (EXISTS)
- Sélectionner les employés dont la date d'embauche est supérieure ou égale à la dernière prise de poste de manager, utiliser des alias (ALL)
- Sélectionner l’identifiant de l’employé dont le salaire est le plus élevé, utiliser des alias (ALL)
- Sélectionner le titre le plus donné aux employés
- Sélectionner les identifiants des employés dont la période d'emploi est plus longue que celle des autres employés (ALL)
- Sélectionner les employés qui ont le titre le plus fréquemment donné (ALL)
- Sélectionner les titres des employés ayant au moins un salaire supérieur à 150000$, utiliser des alias (ANY)
- Sélectionner le nombre d’employés managers (ANY)
- Sélectionner les noms des employés ayant été dans au moins un département et ayant eu un salaire supérieur à 150 000$, utiliser des alias (ANY)
- Sélectionner les prénoms des employés ayant le titre « Senior Engineer » (ANY)
- Sélectionner le nombre de salariés ayant un salaire supérieur à la moyenne (ANY)