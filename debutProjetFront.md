# Marche à suivre pour le front

- "mobile first" ? = On commence toujours par coder la plateforme qui sera le plus le plus utiliser, puis avec le CSS on fera le responsive
- On code la partie HTML
- Puis on code la partie CSS / SCSS de la partie HTML

**2 manière de faire :** 
- Soit on code une partie d'HTML (header par exemple) et on code sa partie de CSS par la suite
- Soit on code tout le HTML et lorsque tout est terminé, on code le CSS par la suite.

##  HTML sémantique

On utilise un maximum de balise différente aevc un minimum de div pour avoir un site accessible et avoir un meilleur référencement pour le SEO.

On commence par la balise HTML :

- Changer le svg (logo que l'on voit sur l'onglet de notre site)
- Changer le title (titre de notre site)
- Changer la langue (langue la plus utiliser sur notre site)

Étant donnée qu'avec Svelte nous avons des components pour les parties de code qui seront réutilisés dans plusieurs page. Nous pouvons commencer par coder le ```Header.svelte``` et le ```Footer.svelte``` : 

*Exemple de Header :*
```
<header  role="banner">
    <div class="navbar">
        <nav role="navigation">
            <ul>
                <li><a href="/" use:link>Home</a></li>
                <li><a href="/recipes" use:link>Recipes</a></li>
                <li><a href="/reviews" use:link>Reviews</a></li>
                <li><a href="/aboutus" use:link>About us</a></li>
                <li><a href="/logform" use:link>Log form</a></li>
            </ul>
        </nav>
        <div class="logo">O'cook</div>
        <div class"search">
            <label for="site-search">Search the site:</label>
            <input type="search"/>
            <button>Search</button>
        </div>
    </div>
</header>
```

Ensuite on fait le HTML de nos autres pages, Home, About us etc.

## CSS responsive

On utilisera qu'une seule fois les pixels pour initialiser notre taille au site. Ensuite nous utiliserons que les **rem**.

Dans notre CSS on commence par mettre :
- Le CSS utile pour tout notre site :
  - le selecteur universel * :
  ```
  * {
    bordure : 1px rouge; utile pour le débogage CSS
    box-sizing: border-box;
    list-style: none; Pour que nos listes ne ressemble pas à des listes
    text-decoration: none; Pour que les liens ne soit plus souligner
    }
  ```
  - le sélecteur de pseudo-classe ```:root``` = ```html``` :
  ```
  :root {
  background-color: white;
	/* Maintenant si on fait met une taille : 500px/16px = 31,25rem tout s'armonise en conséquence donc on ne met plus d'autre px dans le reste du projet*/
	font-size: 16px;
    /* Toutes les couleurs utilisées sur le site */
    --color-text: #00330d;
    --background-body: #ffffff;
      }
  ```
- Ensuite on fait des parties de CSS 
  - On commente chaque partie : Partie Header, partie Home, partie About us etc
    
Si on est sur un projet Svelte, on peut faire le CSS utile seulement à la page, dans le fichier de celle-ci, en dessous du HTML dans des balises ```style```.

Si on souhaite utiliser du SCSS on met ```<style lang="scss">```

- On fait en sorte de ne pas se répéter, on peut donc écrire notre CSS de cette manière :
```
h1, h2, h3, h4, h5, h6 {
    text-align: center;
    color: var(--color-text);
    text-transform: uppercase;
} 
```
- Les média queries
  ```@media screen and (max-width: 768px) { /*Mobile*/} ```
