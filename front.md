# Marche à suivre pour le front

- "mobile first" = On commence toujours par coder en mode téléphone, puis avec le CSS on fera le responsive
- On code la partie HTML
- Puis on code la partie CSS / SCSS de la partie HTML

**2 manière de faire :** 
- Soit on code une partie d'HTML (header par exemple) et on code sa partie de CSS par la suite
- Soit on code tout le HTML et lorsque tout est terminé, on code le CSS par la suite.

##  HTML sémantique

On utilise un maximum de balise différente aevc un minimum de div pour avoir un site accessible et avoir un meilleur référencement pour le SEO.

On commence par la balise HTML, qui dans notre cas se trouve dans :
- ```index.html```, fichier qu'on ne touche pas sauf pour :
    - Changer le svg (logo que l'on voit sur l'onglet de notre site)
    - Changer le title (titre de notre site)
    - Changer la langue  (langue la plus utiliser sur notre site)

Étant donnée qu'avec Svelte nous avons des components pour les partie de code qui seront réutilisés dans plusieurs page. Nous pouvons commencer par coder le ```Header.svelte``` et le ```Footer.svelte``` : 

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
  soit le selecteur universel * :
  ```
  * {
    bordure : 1px rouge; utile pour le débogage CSS
    box-sizing: border-box;
    list-style: none; Pour que nos listes ne ressemble pas à des listes
    text-decoration: none; Pour que les liens ne soit plus souligner
    }
  ```
  
