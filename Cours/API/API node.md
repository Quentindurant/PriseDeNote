NPm -> outils de ligne de commande 'par défault de node'. On peut l'utiliser pour installer les package 

npm --version 



Initialiser un nouveau projet, et faite une copie de votre précédent travail. Tranformer votre server web HTTP en serveur Express. Ajouter les fonctionnalités suivantes :

- [x] Créez des nouvelles routes avec variables dedans
- [x] Le fichier principale doit s'appeller app.js et doit tourner sur le port 8080.
- [x] Utilisez des templates avec des includes dedans [via le module ejs].
- [x] Ajoutez dans une page, un formulaire pour se connecter et passer en mode admin. Le login et le password devront être "admin". Concervez les informations dans une session et faire apparaitre "Bienvenue _login_" dans toutes les pages.
- [x] Créer un bouton de déconnection.
- [x] Créer un menu de navigation avec plusieurs pages. Attention, je tiendrais compte de la qualité du site web.
- [x] Ajoutez une route pour télécharger un fichier YYYYMMDD_HHmmss.txt qui contient la date du téléchargement ... bref, vous aller devoir utiliser FS.
- [ ] Dans la navigation, mettre un lien visible vers une page d'erreur (et gérer une page 404 du coup)
- [x] Attention, votre site web doit être "joli" et contenir des balises HTML5 entre autre
- [x] L'installation doit se faire uniquement via la commande "npm install". Attention tout vos modules doivent être en installés en local (--save) et pas en globale (-g)
- [x] Ajoutez dans votre package.json , dans "scripts", la ligne suivante "start": "node app.js" (sauf si vous utilisez express generator)
- [ ] Ajoutez dans votre projet un fichier readme.md avec les instructions d'instalation.

Et vous vous souvenez du DAB ?

- Inclure une page avec une route dynamique qui prends un montant en dynamique
- Cette page doit utiliser votre module DAB et afficher le plus petite coupure poru le montant passer en paramètre
  
  
Déploiement        
  installation local /0,5 
	  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh 
	  \. "$HOME/.nvm/nvm.sh"
	  npx express-generator
  deploiement via fichier /1 
	  git clone    
  deploiement automatique /0,5    
	  git action
Express                    
  beauté du site web /0,5    
	  ok
  qualité du HTML /0,5
	  ~    
  engine template /1
	  express generator    
  use include in template /0,5  
	  include partials/head  
  regroupement des routes /1 
	  fichier route/ index.js   
  session /1 
	  auth   
  session cookie /1  
	  auth  
  404 /1  
	  non  
  url dynamic /1 
	  non   
CHAT            
  pseudo /0,5    
  message retravailler coté serveur /1    
  historique de conversation /1    
  clean Bad Word /1    
  mise en forme /1    
API        
  ORM /2    
  rest /3    
  connection google/facebook /1