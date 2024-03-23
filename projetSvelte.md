# Les étapes à réaliser pour un nouveau projet Svelte

- Création dossier du projet
- Ouvrir VSC
- Ouvrir un nouveau terminal

## Créer un nouveau repository

- Aller sur le profil GitHub
- Aller sur l'onglet repositories puis new
- Choisir son profil en tant qu'Owner et donner le nom du projet initial
- GitHub donne les commandes à réaliser, pour plus d'explications :
  - Aller les chercher dans le fichier **git.md**

## Dans le terminal

- **npm create vite@latest nomdudossier -- --template svelte -y**
- **cd nomdudossier** 
- **npm install** 
- **npm install svelte-spa-router@~3.3.0**
- **npm install -D sass**
- **npm run dev** = pour lancer le serveur

## Vider les dossiers et fichiers inutiles

-	Vider le contenu de App.svelte
-	Renommer le fichier app.css en app.scss et le vider 
-	Changer la route de l’import dans le fichier main.js (app.css en app.scss)
-	Supprimer le fichier Counter.svelte
-	Dans le fichier jsconfig.json, à la ligne « checkJs » : true, remplacer par false.

## Créer les dossiers et fichiers utiles

- Dans le dossier lib, créer les dossiers pages et components
- Dans le dossier pages, créer nos Pages.sveltes
- Dans le dossier components, créer les composants Header.svelte et Footer.svelte (*exemple : lib/components/Footer.svelte*)

## Intégration HTML

- Dans App.svelte, faire les imports des pages ayant besoin des routes (Header.svelte et Footer.svelte) et de de Router dans une balise script :
```
<script>
  import Router from 'svelte-spa-router'
  import Header from './lib/components/Haeder.svelte'
  import Footer from './lib/components/Footer.svelte'
</script>
```
- Dans App.svelte dans les balises script en dessous des imports, ajouter une constante routes :
```
const routes = {
  "/": Home,
  "/portfolio": Portfolio,
  "/contact": Contact,
  "*": NotFound,
}
```
- En dessous des balises script, appeler les composants pour les instancier :
```
<div class="container">
  <Header />
  <Router {routes} />
  <Footer />
</div>
```
- Dans Header.svelte, faire la nav avec les liens qui mènent aux pages :
```
<header>
    <nav>
        <ul>
            <li><a href="/">Accueil</a></li>
            <li><a href="/portfolio">Portfolio</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
</header>
```
- Faire de même pour le fichier Footer.svelte :
```
<footer>
    <nav>
        <ul>
            <li> <a href="/contact">Contact</a></li>
        </ul>
    <nav>
</footer>
```

> [!WARNING]
> Penser à importer **TOUTES** les pages dans App.svelte pour que notre contenu s’affiche correctement sur la page web.
