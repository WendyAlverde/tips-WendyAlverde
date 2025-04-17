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

### Installation router

- ```npm install react-router-dom```

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

Structurer les dossiers comme ceci :
```bash
src/
├── assets/         # images, logos, etc.
├── styles/         # tes fichiers .scss
├── lib/
│   ├── components/ # tous les composants réutilisables
│   └── pages/      # chaque "page" de ton site (Accueil, Contact, etc.)
├── App.jsx         # composant racine qui appelle les pages
├── main.jsx        # point d’entrée React
```

Dans le dossier src :
  - Déplacer le fichier App.css dans le dossier styles
  - Changer le chemin dans App.jsx par ```import './styles/App.css';```

Si projet avec une base de données :
- Créer le fichier .env.example
- Créer le fichier .env avec l'adresse de la BDD (peut changer d'un pc à un autre)

Si travail en **scss**, changer les extentions css par scss

## Router

Si on importe un composant avec import Nom from './chemin', il doit y avoir export default Nom dans le fichier ciblé.

- Dans le fichier App.jsx :

```jsx
function App() {
	return (
		<BrowserRouter>
		<Header />
		<main>
			<Routes>
			  <Route path="/" element={<Home />} />
			</Routes>
		</main>
		<Footer />
		</BrowserRouter>
	);
}

export default App;
```

- Dans le fichier Home.jsx :

```jsx
function Home() {
    return (
        <section style={{ padding: "2rem" }}>
            <h1>Bienvenue !</h1>
            <p>Sur la page Home</p>
        </section>
    );
}

export default Home;
```

