
A. Bases & sélection (1–20)

Que fait SELECT DISTINCT ?
A Supprime les lignes NULL · B Supprime les doublons · C Trie par défaut · D Limite à 10
Réponse : B

Quel est l’ordre correct des clauses ?
A FROM → WHERE → SELECT → ORDER BY · B SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT · C SELECT → WHERE → FROM → GROUP BY · D SELECT → FROM → HAVING → WHERE
Réponse : B 
GitHub

Quelle requête affiche toutes les lignes d’une table cities ?
A SHOW cities · B DESCRIBE cities · C SELECT * FROM cities · D LIST cities
Réponse : C

Que renvoie SHOW DATABASES ?
A Les tables · B Les vues · C Les bases disponibles · D Les index
Réponse : C 
GitHub

Quelle commande « entre » dans une base nommée world en CLI MySQL ?
A USE world; · B ENTER world; · C OPEN world; · D SET DB world;
Réponse : A 
GitHub

Pour supprimer une base :
A DROP SCHEMA · B DELETE DATABASE · C DROP DATABASE · D REMOVE DB
Réponse : C 
GitHub

Pour voir les colonnes d’une table :
A SHOW TABLES · B DESCRIBE table · C EXPLAIN DATABASE · D LIST COLUMNS *
Réponse : B 
GitHub

Que fait TRUNCATE table ?
A Supprime la table · B Vide les données · C Compresse la table · D Fait un backup
Réponse : B 
GitHub

SELECT * FROM cities WHERE state_code = "07"; filtre selon :
A Nom du pays · B Code d’état · C Latitude · D Population
Réponse : B 
GitHub

SELECT sans ORDER BY garantit-il l’ordre d’affichage ?
A Oui · B Non · C Oui si MySQL · D Oui si table InnoDB
Réponse : B

Quelle clause limite le nombre de lignes ?
A TOP · B LIMIT · C TAKE · D SAMPLE
Réponse : B 
GitHub

Quelle clause saute un certain nombre de lignes ?
A SKIP · B OFFSET · C NEXT · D SEEK
Réponse : B 
GitHub

ORDER BY col DESC :
A Trie du plus petit au plus grand · B Trie du plus grand au plus petit · C Trie aléatoire · D Supprime les doublons
Réponse : B

Quelle requête renvoie les pays dont wikiDataId est NULL ?
A SELECT * FROM countries WHERE wikiDataId = NULL; · B ... IS NULL · C ... == NULL · D ... EQUAL NULL
Réponse : B 
GitHub

Quel mot-clé supprime les doublons entre deux jeux de résultats compatibles ?
A INTERSECT · B EXCEPT · C UNION · D MERGE
Réponse : C 
GitHub

CREATE DATABASE nom; appartient à :
A DCL · B DML · C DDL · D TCL
Réponse : C

DELETE FROM t; sans WHERE :
A Vide la table · B Supprime la table · C Crée un log seulement · D Ne fait rien
Réponse : A

Un alias de table se met avec :
A RENAME · B USING · C AS · D WITH
Réponse : C

SELECT 1=1; renvoie :
A TRUE · B 1 · C 0 · D NULL
Réponse : B (dans MySQL, TRUE ⇢ 1)

DESCRIBE cities; affiche :
A Le contenu · B Les colonnes et types · C Les index seulement · D Les triggers
Réponse : B 
GitHub

B. Filtres & opérateurs (21–40)

En SQL standard, « différent de » est :
A <> · B =/ · C !== · D ><
Réponse : A 
GitHub

Équivalent MySQL de « différent de » :
A != · B =/ · C ^= · D ~=
Réponse : A 
GitHub

IN sert à :
A Tester un intervalle · B Tester appartenance à une liste · C Faire une jointure · D Créer un index
Réponse : B 
GitHub

BETWEEN a AND b inclut :
A a uniquement · B b uniquement · C a et b · D Ni a ni b
Réponse : C 
GitHub

LIKE 'a%' correspond à :
A Chaînes finissant par ‘a’ · B Commençant par ‘a’ · C Contenant ‘a’ · D Égales à ‘a’
Réponse : B 
GitHub

LIKE '%a' :
A Début ‘a’ · B Fin ‘a’ · C Au moins deux ‘a’ · D Mot égal ‘a’
Réponse : B 
GitHub

LIKE '%a%' :
A Commence par ‘a’ · B Termine par ‘a’ · C Contient ‘a’ · D A exactement 1 ‘a’
Réponse : C 
GitHub

Dans LIKE, _ signifie :
A Zéro ou plus caractères · B Un seul caractère · C Alphabetique seulement · D Chiffre
Réponse : B 
GitHub

IS NULL vs = NULL :
A Identiques · B IS NULL est correct · C = NULL est correct · D Aucun
Réponse : B 
GitHub

Priorité AND vs OR :
A OR > AND · B AND > OR · C Égal · D Non défini
Réponse : B

Que fait WHERE a AND (b OR c) ?
A Même que WHERE (a AND b) OR c · B Filtre avec priorité sur a · C Même que WHERE a OR b OR c · D Aucune des réponses
Réponse : B (structure logique)

Pour vérifier une valeur dans une sous-liste fixe :
A WHERE col IN ('A','B') · B WHERE col BETWEEN ('A','B') · C WHERE col HAS ANY · D WHERE col ARRAY('A','B')
Réponse : A

Trouver latitudes entre 20 et 30 :
A WHERE latitude IN (20,30) · B WHERE latitude BETWEEN 20 AND 30 · C WHERE latitude = 20..30 · D WHERE latitude RANGE 20,30
Réponse : B 
GitHub

Condition vraie toujours :
A 1=0 · B 1=1 · C NULL=NULL · D A<>A
Réponse : B

WHERE col = NULL renvoie :
A Vrai · B Faux · C NULL (inconnu) · D 1
Réponse : C

Trouver wikiDataId non nul :
A WHERE wikiDataId != NULL · B WHERE NOT wikiDataId · C WHERE wikiDataId IS NOT NULL · D WHERE wikiDataId <> ''
Réponse : C 
GitHub

WHERE NOT (col IN (...)) est équivalent à :
A WHERE col NOT IN (...) · B WHERE col != ALL (...) · C WHERE col <> ANY (...) · D Aucun
Réponse : A

Chercher ‘pa…on’ (début pa, fin on) :
A LIKE 'pa%on' · B LIKE '%paon%' · C LIKE 'p%a%o%n' · D LIKE '_pa_on'
Réponse : A 
GitHub

Un filtre « liste vide » avec IN () :
A Renvoie tout · B Érreur ou faux pour toutes · C Vrai pour toutes · D Ignore
Réponse : B (selon SGBD, souvent erreur)

Pour combiner deux conditions alternatives :
A AND · B OR · C XOR · D NOR
Réponse : B

C. Agrégats & regroupements (41–60)

Fonction qui compte les lignes :
A SUM · B COUNT · C AVG · D MIN
Réponse : B

COUNT(col) ne compte pas :
A Zéros · B Doublons · C NULL · D Négatifs
Réponse : C

COUNT(*) compte :
A Lignes non NULL · B Lignes distinctes · C Toutes les lignes · D Lignes uniques
Réponse : C

Pour calculer la moyenne :
A AVG · B MEAN · C AVERAGE · D MED
Réponse : A

GROUP BY s’applique :
A Avant SELECT · B Après WHERE · C Après ORDER BY · D Après LIMIT
Réponse : B (flux logique SELECT/FROM/WHERE/GROUP/HAVING/ORDER/LIMIT) 
GitHub

Filtrer sur un agrégat se fait avec :
A WHERE · B HAVING · C QUALIFY · D WINDOW
Réponse : B 
GitHub

SUM(col) retourne :
A Max · B Somme · C Moyenne · D Médiane
Réponse : B

MIN(col) calcule :
A Minimum · B Maximum · C Moyenne · D Mode
Réponse : A

Pour trier le résultat groupé :
A GROUP BY ... DESC · B HAVING ... ORDER · C ORDER BY ... · D SORT BY GROUP
Réponse : C 
GitHub

SELECT country_code, COUNT(*) FROM cities GROUP BY country_code; retourne :
A Une ligne · B Une ligne par pays · C Toutes les villes · D Erreur
Réponse : B

HAVING COUNT(*) > 100 :
A Filtre les lignes avant agrégat · B Filtre les groupes · C Trie les groupes · D Remplace WHERE
Réponse : B

GROUP BY sans agrégat :
A Interdit · B Autorisé (équivaut à DISTINCT sur ces colonnes) · C Ajoute un index · D Crée une vue
Réponse : B

AVG(NULL, 2, 4) :
A 0 · B 2 · C 3 · D NULL
Réponse : B (NULL ignoré)

Ordre logique :
A SELECT→FROM→GROUP BY→WHERE · B FROM→WHERE→GROUP BY→HAVING→SELECT (exécution) · C WHERE→FROM→GROUP · D LIMIT→ORDER→SELECT
Réponse : B (ordre logique d’évaluation)

COUNT(DISTINCT col) :
A Interdit · B Compte valeurs uniques · C Compte NULL · D Tri asc
Réponse : B

SUM(CASE WHEN cond THEN 1 ELSE 0 END) calcule :
A Une somme de valeurs · B Un dénombrement conditionnel · C Une moyenne · D Un rang
Réponse : B

HAVING sans GROUP BY :
A Toujours erreur · B Autorisé selon SGBD (agit comme WHERE sur agrégats globaux) · C Équivaut à ORDER BY · D Supprime doublons
Réponse : B

GROUP BY 1,2 signifie :
A Grouper par colonnes 1 et 2 du SELECT · B Grouper par colonnes nommées 1 et 2 · C Erreur · D Grouper par littéraux 1 et 2
Réponse : A (notation positionnelle ; selon SGBD)

SUM(DISTINCT col) :
A Somme des valeurs uniques · B Somme normale · C Compte uniques · D Interdit
Réponse : A

ORDER BY intervient :
A Avant GROUP · B Après SELECT/HAVING · C Avant WHERE · D En premier
Réponse : B 
GitHub

D. Jointures (61–80)

Une jointure interne renvoie :
A Toutes les lignes · B Lignes correspondantes dans les deux tables · C Lignes de gauche seulement · D Lignes de droite seulement
Réponse : B

LEFT JOIN renvoie :
A Seulement les correspondances · B Toutes les lignes de droite · C Toutes les lignes de gauche + correspondances · D Lignes non correspondantes uniquement
Réponse : C

RIGHT JOIN renvoie :
A Lignes de droite + correspondances · B Lignes de gauche + correspondances · C Interne · D Cross
Réponse : A

Jointure croisée (CROSS JOIN) :
A Interne · B Produit cartésien · C Gauche · D Droite
Réponse : B

Condition de jointure s’écrit :
A ON · B USING ONLY · C WHERE JOIN · D MATCH
Réponse : A

Pour toutes les villes et leurs pays quand possible :
A cities INNER JOIN countries · B cities LEFT JOIN countries · C RIGHT JOIN · D CROSS JOIN
Réponse : B

Pour seulement les couples ville-pays existants :
A INNER JOIN · B LEFT JOIN · C RIGHT JOIN · D FULL OUTER JOIN
Réponse : A

Pour lignes non appariées à gauche :
A Ajouter WHERE right.id IS NULL après LEFT JOIN · B RIGHT JOIN · C CROSS JOIN · D WHERE 1=0
Réponse : A

Jointure sur plusieurs colonnes :
A Impossible · B ON a.id=b.id AND a.code=b.code · C WITH · D MAP JOIN
Réponse : B

USING(col) est un sucre syntaxique pour :
A ON t1.col = t2.col · B ON t1.col <> t2.col · C ON vide · D ON TRUE
Réponse : A

FULL OUTER JOIN renvoie :
A Interne · B Toutes les lignes des deux côtés · C Gauche seulement · D Droite seulement
Réponse : B

Pour éviter un produit cartésien involontaire :
A Omettre ON · B Écrire la condition ON .../WHERE ... · C Mettre DISTINCT · D Mettre GROUP BY
Réponse : B

Alias c pour cities :
A FROM cities AS c · B FROM cities -> c · C FROM c = cities · D ALIAS cities c
Réponse : A

Filtrer après jointure :
A ON · B HAVING · C WHERE (pour les lignes du résultat) · D PARTITION BY
Réponse : C

INNER JOIN + condition dans WHERE équivaut souvent à :
A LEFT JOIN · B Cross · C Jointure interne avec ON · D FULL
Réponse : C

Plusieurs JOIN s’évaluent :
A Dans n’importe quel ordre · B Selon l’optimiseur · C Gauche à droite strictement · D Droite à gauche
Réponse : B (optimiseur choisit un plan)

Schéma : countries(iso), cities(country_code) ; jointure :
A ... ON cities.country_code = countries.iso · B ... ON countries.country_code = cities.iso · C ... USING(iso,country_code) · D ... WHERE iso LIKE country_code
Réponse : A

Pour compter le nombre de villes par pays (tous les pays, y compris sans ville) :
A countries LEFT JOIN cities ... GROUP BY countries.iso · B INNER JOIN · C RIGHT JOIN · D CROSS
Réponse : A

Jointure conditionnelle sur intervalle (non-égalité) :
A Impossible · B ON t1.a BETWEEN t2.x AND t2.y · C ON t1.a = t2.a uniquement · D USING()
Réponse : B

NATURAL JOIN :
A Spécifie explicitement la condition · B Jointure automatique par colonnes de même nom · C Cross · D Anti-join
Réponse : B

E. Sous-requêtes & ensembles (81–95)

Une sous-requête dans WHERE s’écrit avec :
A IN (SELECT ...) · B GROUP BY (SELECT ...) · C ORDER BY (SELECT ...) · D LIMIT (SELECT ...)
Réponse : A

EXISTS (SELECT 1 FROM t2 WHERE t2.x=t1.x) teste :
A L’égalité stricte · B L’existence d’au moins une ligne · C Le comptage exact · D Le maximum
Réponse : B

NOT EXISTS (...) :
A Inverse EXISTS · B Compte les lignes · C Trie · D Remplace GROUP BY
Réponse : A

IN vs EXISTS :
A Identiques toujours · B EXISTS peut être plus performant selon le plan · C IN toujours meilleur · D IN ne supporte pas sous-requête
Réponse : B

UNION :
A Concatène avec suppression de doublons · B Concatène en gardant doublons · C Intersecte · D Soustrait
Réponse : A

UNION ALL :
A Supprime doublons · B Garde doublons · C Intersecte · D Classe
Réponse : B

INTERSECT :
A Union · B Différence · C Intersection · D Produit
Réponse : C

EXCEPT :
A Union · B Différence (A sans B) · C Intersection · D Produit
Réponse : B

SELECT * FROM A, B sans condition :
A Interne · B Cross (produit cartésien) · C Gauche · D Droite
Réponse : B

Filtrer le top 10 plus grandes latitudes :
A ORDER BY latitude DESC LIMIT 10 · B GROUP BY latitude LIMIT 10 · C HAVING latitude DESC LIMIT 10 · D LIMIT 10 BY latitude DESC
Réponse : A

Sous-requête scalaire dans le SELECT :
A Interdit · B Autorisé (retourne une valeur) · C Équivaut à JOIN · D Supprime doublons
Réponse : B

« Anti-join » logique :
A LEFT JOIN ... WHERE right.id IS NULL · B RIGHT JOIN ... WHERE left.id IS NULL · C CROSS JOIN · D FULL
Réponse : A

ANY / SOME :
A Testent « au moins une » valeur · B Testent toutes · C Tri · D Agrègent
Réponse : A

ALL :
A Teste « toutes » les valeurs · B Anti-join · C Tri · D Limite
Réponse : A

WITH cte AS (SELECT ...) SELECT ... :
A Crée une table permanente · B Vue matérialisée · C Expression de table commune (temporaire) · D Trigger
Réponse : C

F. DDL, contraintes & transactions (96–105)

Créer une table :
A MAKE TABLE · B CREATE TABLE · C NEW TABLE · D BUILD TABLE
Réponse : B 
GitHub

Modifier une table :
A CHANGE TABLE · B ALTER TABLE · C EDIT TABLE · D UPDATE TABLE
Réponse : B 
GitHub

Supprimer une table :
A DROP TABLE · B DELETE TABLE · C REMOVE TABLE · D TRUNCATE DATABASE
Réponse : A 
GitHub

Insérer une ligne :
A INSERT INTO t VALUES (...) · B ADD ROW t (...) · C PUT t (...) · D LOAD t (...)
Réponse : A 
GitHub

Mettre à jour :
A CHANGE t SET ... · B UPDATE t SET ... WHERE ... · C ALTER t ... · D MERGE t ...
Réponse : B 
GitHub

Supprimer des lignes :
A DROP FROM t WHERE ... · B DELETE FROM t WHERE ... · C REMOVE FROM t · D TRUNCATE FROM t
Réponse : B 
GitHub

Clé primaire :
A Un index non unique · B Colonne obligatoire non indexée · C Identifie de manière unique chaque ligne · D Un trigger
Réponse : C

Clé étrangère :
A Colonne calculée · B Référence une clé primaire d’une autre table · C Index texte · D Vue
Réponse : B

Contrainte d’unicité :
A UNIQUE · B PRIMARY · C FOREIGN · D CHECK INDEX
Réponse : A

Transaction atomique :
A S’exécute partiellement · B All-or-nothing · C Uniquement en lecture · D Sans journalisation
Réponse : B

G. Conception (MCD/MPD) & normalisation (106–112)

Dans un MCD, une association N-N devient au MPD :
A Une FK dans l’une · B Une table de jonction · C Deux triggers · D Une vue
Réponse : B

Redondance des données :
A Recommandée · B À éviter (risque d’incohérence) · C Sans effet · D Obligatoire
Réponse : B 
GitHub

Intégrité référentielle garantit :
A L’ordre d’insertion · B Cohérence des liens FK→PK · C Performance · D Chiffrement
Réponse : B

1FN impose :
A Valeurs atomiques · B Pas de NULL · C Pas de doublons · D Aucune FK
Réponse : A

2FN ajoute (sur clés composées) :
A Aucune dépendance partielle des attributs non-clés · B Pas de dépendances transitives · C Aucune FK · D Pas de NULL
Réponse : A

3FN impose :
A Pas de dépendances transitives des attributs non-clés vers la PK · B Index obligatoire · C Vue matérialisée · D Sharding
Réponse : A

Clé candidate :
A Toujours choisie comme PK · B Peut être PK, mais pas forcément · C N’existe pas en MPD · D Synonyme de FK
Réponse : B

H. Monde « WORLD » & requêtes d’exemple (113–118)

Exemple du dépôt pour liste des state_code uniques :
A SELECT state_code FROM cities; · B SELECT DISTINCT state_code FROM cities; · C SELECT DISTINCT state_code FROM countries; · D SELECT state_code FROM countries;
Réponse : B 
GitHub

Filtrer cities par deux pays :
A WHERE country_code IN ('AD','AE') · B WHERE country_code = AD OR AE · C WHERE country_code BETWEEN 'AD' AND 'AE' · D WHERE country_code LIKE 'AD|AE'
Réponse : A 
GitHub

Combiner deux filtres avec priorité (exemple du dépôt) :
A lat > 42 AND lon > 1.5 OR lat < 20 AND lon > 50 · B Même requête mais avec parenthèses pour lever toute ambiguïté
Quel est recommandé ?
A A · B B · C Les deux identiques toujours · D Ni l’un ni l’autre
Réponse : B 
GitHub

Pour latitudes BETWEEN 20 AND 30 :
A WHERE latitude BETWEEN 20 AND 30 · B WHERE latitude IN (20,30) · C WHERE latitude LIKE '20-30' · D WHERE latitude >= 20 OR latitude <= 30
Réponse : A 
GitHub

Champs NULL dans countries (exemple du dépôt) se détectent avec :
A = NULL · B IS NULL · C == NULL · D LIKE NULL
Réponse : B 
GitHub

Pour compter les villes par country_code :
A SELECT COUNT(country_code) FROM cities; · B ... GROUP BY country_code · C ... HAVING country_code · D ... ORDER BY country_code
Réponse : B

I. NoSQL — rappels (119–120)

Selon la page NoSQL du dépôt, le modèle NoSQL :
A Exige schéma strict tabulaire · B Vise flexibilité/échelle (documents, clé-valeur, etc.) · C Remplace SQL toujours · D N’a pas de cas d’usage
Réponse : B 
GitHub

Dans le contexte NoSQL, l’absence de clé primaire relationnelle stricte signifie souvent :
A Pas d’identifiant du tout · B Identifiant applicatif (ex. _id) et dénormalisation plus fréquente · C Pas d’index possible · D Pas de jointures autorisées par langage de requête
Réponse : B (généralités NoSQL, cohérent avec intro du dépôt)