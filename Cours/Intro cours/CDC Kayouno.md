
# Cahier des charges de Kayouno

### Expression du besoin :

En 2025, nous avons constater une grosse demande de Kayoux. Nous avons alors penser a cibler les fanatique de casino et de kayou en mélangeant les deux. Viens alors l'idée du site de vente de Cailloux un peu farfelu basé sur l'aléatoire. 

### Objectif :

Notre but est de répondre a cette demande croissante de cailloux avec du fun en livrant un cailloux aléatoire ce qui peut créer la surprise. De plus, un système de rareté de cailloux est présent ce qui créer de l'espoir a chaque achat

### Techno :

- Laravel (blade)
- MariaDB
- VPS (nginx) 

### Fonctionnaliter :

- paiment de cailloux, reception aléatoire
- Mystery box (3 box) à choisir.
- Rareter de cailloux 1 à 5 étoiles + jackpot
- Profil aléatoire avec donnée bancaire aléatoire
- Chronocailloux Frais de port en fonction de la rareter du cailloux 
- jackpot ultra rare 0.01% de drop ULURU


### Def Mystery box :

- 1   10 euros
- 2   800 euros
- 3   1000560 euros

### Def rareter :
##### 1 box :
- 1 60%
- 2 20%
- 3 10%
- 4 4%
- 5 0.5%
- jackpot 0.01%

##### 2 box :
- 1  20 %
- 2  40 %
- 3  15 %
- 4  8%
- 5  3 %
- jackpot 0.01%

##### 3 box :
- 1  4 %
- 2 10%
- 3  25%
- 4  50 %
- 5  10 %
- jackpot 0.03%

##### Def Frais de port :

- 1   3 euros
- 2   15euros
- 3   45 euros
- 4    100 euros
- 5    1000euros
- Jackpot   3 000 000 000 euros 

# User story :

###### Connexion du user : 

- le user se rend sur la page de connexion, rentre ses données et après validation, connexion réussi mais un profil aléatoire est mis.

###### Paiement du user :

- le user choisi sa Mystery box jusqu'au paiement réussi et voit dans ses notifs le cailloux aléatoire qu'il va recevoir ainsi que les frais de port déterminer a la rareté du cailloux.

##### Reception du user :

- le user reçoit la notif qui l'oblige a payer les frais de port sous risque de prison a vie




## PAGES :

	1 Home + mystery box
	2 paiement
	3 panier
	 4 présentation des mystery box
	 opt 5 login 


## Forfaits :

#### Normal : 2/3 jours (1200 euros)
	- Home page + mystery box 
	- paiement (peut être sécurisé)
	- panier
	- mail de confirmation et de suivi
	
#### Pro : 25 jours (10 000 euros)
	- Home page + mystery box 
	- paiement (sécurisé)
	- panier
	- mail de confirmation et de suivi
	- chatbot
	- Compte sécurisé
	- design complet et réactif
	- réfacto
	- Monnaie interne
	- marché interne d'achat revente 
	- Utilisation d'un template