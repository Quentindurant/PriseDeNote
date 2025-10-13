
## Rappel des bases


- Créé par Linus Torvalds en 2005
- Permet de réaliser du versionning (gestion de versions, gestion de l'historique)
- Permet le travail collaboratif (plusieurs personnes sur un même projet, et garantir l'intégrité du travail de chacun)

## Vocabulaire


- `Dossier courant` : C'est le dossier depuis lequel on exécute une commande.
- `Repository` : C'est un dossier qui "utilise" GIT : il dispose d'un sous-dossier caché ".git". Ils peuvent être distants ou locaux.
- `Repository local` : C'est le repository qui est sur une machine à laquelle vous avez généralement accès.
- `Repository distant` : C'est le repository qui est **hébergé et géré** par une plateforme spécialisée (Github, Gitlab, Gitea, etc...). Ils peuvent être publics (accessibles à tous) ou privés (accessibles uniquement à ceux qu'on souhaite).
- `Les branches` : Permettent de gérer plusieurs versions d'un même projet.

## Commandes


- `git init` : Permet de créer un repository local dans le dossier courant.
    
- `git remote add origin <url>` : Permet de relier un repository local à un repository distant
    
- `git clone <url> <folder>` : Permet de créer un repository local à partir du contenu d'un repository distant. Lie automatiquement les deux repository.
    
- `git add <param>` : Permet d'indexer les fichiers/dossiers passées dans `<param>`.
    
- `git remove <param>` : Permet de désindexer les fichiers/dossiers passées dans `<param>`.
    
- `git commit -m "<message>"` : Permet de sauvegarder un état d'indexation. Permet également de décrire le commit grâce au message qui est **obligatoire**. Ils sont datés.
    
- `git push` : Permet d'envoyer les commits du repository local sur le repository distant. Lors du premier push sur une branche, il faudra utiliser la commande `git push -u origin <branch>`. Si vous l'oubliez, GIT vous le rapellera.
    
- `git pull` : Permet de récupérer les commits du repository distant sur le repository local.
    
- `git status` : Permet de voir l'état de la branche actuelle du repository local.
    
- `git log` : Permet de voir l'historique des commits.

- `git branch` : Permet de lister les branches du repository local et de voir quelle est la branche active.
    
- `git branch <nom>` : Permet de créer une branche nommée sur le repository local.
    
- `git checkout <nom>` : Permet de rendre la branche `<nom>` active (= changer de branche 🙈).
    

rebase reset merge switch (checkout ???)


# GitFlow

Gitflow est une extension / un modèle de workflow Git conçu pour apporter de la rigueur à la gestion de version dans les projets d’envergure.

GitFlow repose sur le workflow de création de branches repartie en plusieurs fonctionnalité. 

| État / étape                                     | Branche concernée    | Actions & commandes principales                                             | But / rôle                                                                                                                                                                                                                                                                               |
| ------------------------------------------------ | -------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Initialisation**                               | `master` + `develop` | `git flow init`                                                             | Met en place les branches de base (master, develop) et les préfixes (feature/, release/, hotfix/) ([Les e-novateurs](https://les-enovateurs.com/gitflow-workflow-git-incontournableprojets-de-qualite "Gitflow – Le workflow Git incontournable pour des projets de qualité"))           |
| **Développement d’une fonctionnalité (feature)** | `feature/…`          | `git flow feature start <nom>` puis `git flow feature finish <nom>`         | Travail isolé pour chaque nouvelle fonctionnalité, fusion vers `develop` après validation ([Les e-novateurs](https://les-enovateurs.com/gitflow-workflow-git-incontournableprojets-de-qualite "Gitflow – Le workflow Git incontournable pour des projets de qualité"))                   |
| **Création d’une version (release)**             | `release/…`          | `git flow release start <version>` puis `git flow release finish <version>` | Préparation et tests avant mise en production ; fusion vers `master` + tag + retour vers `develop` ([Les e-novateurs](https://les-enovateurs.com/gitflow-workflow-git-incontournableprojets-de-qualite "Gitflow – Le workflow Git incontournable pour des projets de qualité"))          |
| **Correction urgente en production (hotfix)**    | `hotfix/…`           | `git flow hotfix start <nom>` puis `git flow hotfix finish <nom>`           | Permet de corriger rapidement un bug bloquant directement depuis `master`, et fusionne aussi dans `develop` ([Les e-novateurs](https://les-enovateurs.com/gitflow-workflow-git-incontournableprojets-de-qualite "Gitflow – Le workflow Git incontournable pour des projets de qualité")) |

<img width="1586" height="930" alt="image" src="https://github.com/user-attachments/assets/72bd5dc3-564a-40d4-aa35-c241e76c6d25" />


- Avantages :
	- historique de projet
	- grosse structure claire 
	- Travail en parallèle facile
	- séparation nette entre le développement et la prod

- limites :
	- demande de la rigueur 

# Changelog

est une pratique consistant à conserver un fichier organisé par nous (les développeurs)
qui répertorie toutes les modifications notables du projet

## Convention de nommage des versions

**Note** : c'est à vous de juger de la qualification des changements !

- Major : concerne des changements significatifs dans le projet. Comme par exemple :
    - changements incompatible avec les versions précédentes ;
    - changement de structure ;
    - changement sur la manière de concevoir le produit ;
    - etc...
- Minor : concerne des changements qui restent compatible avec la version majeure actuelle du projet.
    - ajout de fonctionnalités ;
    - changement d'éléments sans conséquences importantes
- Patch : concerne des correctifs
    - bugs ;
    - fautes d'orthographe ;
    - etc...

La construction du nom se fait de la sorte : `Major.Minor.Patch`.

## C'est un système qui exploite les branches


Chaque branche à un rôle bien définie : 2 branches principales : - `main` : branche de production - `develop` : branche de développement Système de branches temporaires et secondaires : - `feature` : se tire de `develop` pour une nouvelle fonctionnalité - `release` : se tire de `develop` & se merge sur `develop` & `main` pour implémenter une nouvelle version. - `hotfix` : se tire de `main` & se merge sur `develop` & `main` pour corriger des bugs **critiques** en production.

## Le Workflow


On part du principe que l'on vient de créer un repository tout neuf. Les étapes à mettre place sont :

1. Créer une branche de développement : `develop`
2. Mettre en place les 4 fichiers de documentation au sein du projet :
    - README.md
    - CHANGELOG.md
    - LICENSE
    - CONTRIBUTING.md

### Pour la réalisation d'une feature


1. La mettre en place
    - Faire une branche `feature/NOM_FEATURE` pour la fonctionnalité à développer
    - Merger la branche `feature/NOM_FEATURE` sur la branch `develop`
2. Créer une branche `release/vX.Y.Z` à partir de la branche `develop`
    - On teste et on corrige les éventuels bugs
    - On met à jour le changelog
3. On merge la branche `release/vX.Y.Z` sur la branche `main` & `develop`
4. On crée un tag avec le numéro de version sur le commit du merge vers `main`

### Pour la réalisation d'un hotfix

[](https://github.com/kevinniel/MDS-2526-B3-GIT_CICD/blob/main/gitflow.md#pour-la-r%C3%A9alisation-dun-hotfix)

1. On corrige un bug sur la branche `main`:
    - Faire une branche `hotfix/vX.Y.Z` pour la fonctionnalité à développer
    - Merger la branche `hotfix/vX.Y.Z` sur la branch `main` & `develop`
2. On crée un tag avec le numéro de version sur le commit du merge vers `main`
