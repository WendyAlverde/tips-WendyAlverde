# Les étapes à réaliser pour un nouveau projet REACT

## Créer un nouveau repository

- Aller sur le profil GitHub
- Aller sur l'onglet repositories puis new
- Choisir son profil en tant qu'Owner et donner le nom du projet initial
- GitHub donne les commandes à réaliser, pour plus d'explications :
  - Aller les chercher dans le fichier **git.md**

## Dans le terminal

### Si utilisation de Create React App

- Entrer la commande : ```npm init react-app nom-projet```
- cd ```nom-projet```
- code .
Du projet sur VSC :
- Ouvrir un nouveau terminal
- ```npm start```

### Si utilisation de Vite

- Entrer la commande : ```npm create vite@latest . -- --template react```  Le . dans vite@latest . indique qu’on installe dans le dossier actuel.
- Installer les dépendances : ```npm install```
- Installer Sass pour pouvoir utiliser SCSS : ```npm install -D sass```
- Lancer le projet : ```npm run dev```

## Vider les dossiers et fichiers inutiles

Dans le dossier public :
- Supprimer le favicon.ico, logo192.png et logo512.png
- Dans index HTML : 
  - Changer la langue
  - Le title
  - La description

Dans le dossier src :
-	Vider le contenu de App.css
-	Supprimer le logo.svg

## Créer les dossiers et fichiers utiles

Dans le dossier src :
  - Créer les dossiers styles et assets
  - Déplacer le fichier App.css dans le dossier styles
  - Changer le chemin dans App.js par ```import './styles/App.css';```

Si projet avec une base de données :
- Créer le fichier .env.example
- Créer le fichier .env avec l'adresse de la BDD (peut changer d'un pc à un autre)
