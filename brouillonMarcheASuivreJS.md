# JS

On a fait la boucle sur les articles dans le HTML

- recipes n'est pas défini donc on créer dans script la constante
- ```const recipes = []```  /un tableau vide
- Pour voir si ça fonctionne on remplit notre tableau

## Etape 0 : Déclarer la variable `recipes`
let recipes = []

##  Etape 1 appeler l'API Directus

  ### 1.1 récupérer l'URL du endpoint (on a la clé)
  Il faut prendre la fin du endpoint
  
  ``` const endpoint = import.meta.env.VITE_API_BASE_URL + "items/recipes ```
  
  ### 1.2 faire une requête HTTP au endpoint (on a à la chose à ouvrir)
  C'est seulement pour le POST dont on a besoin du Header / Pour le GET on a seulement besoin de fetch(endpoint)
 
  ``` fetch(endpoint)```

## Etape 2 Récupéré les recette à partir de la réponse de l'API

  ### 2.1 récupéré la réponse de l'API et la convertir en objet
  ```
    .then (jeson=> { recipes =json.data }) 
  ```

## Etape 3 Mettre les recettes dans la variable `recipes`
  On ecrase le tableau vide avec les données de l'API

  fetch est asynchrone donc il va faire le each avant de recevoir la réponse, donc :
  Etape 4 : on créer une assync function

  ```
    async function get recipes() {
    const endpoint = import.meta.env.VITE_API_BASE_URL + "items/recipes
    const response = await faetch(endpoint)
    const json = await response.json()
    return json.data
  ```


export let 

## Final 
Fichier Recipes.svelte
-  La partie Script
```
<script>
    import {link} from "svelte-spa-router"

    import RecipeCard from "../components/RecipeCard.svelte";

    async function getRecipes() {
    // 1. appeler l'API de Directus
        // 1.1 récupérer l'URL du endpoint
        const endpoint = import.meta.env.VITE_API_BASE_URL + "items/Recipes?fields=*,categories.Categories_id.name"

        // 1.2 faire une requête HTTP au endpoint
        const response = await fetch(endpoint)
        
    // 2. récupérer les recettes à partir de la réponse de l'API
        // 2.1 récupérer la réponse de l'API et la convertir en objet
        const json = await response.json()

        console.log(json.data)

    // 3. retourner les recettes
        return json.data
    }

    // 4. mettre les recettes dans la variable recipes
    const recipes = getRecipes()

</script>
```
- La partie HTML
```
{#await recipes}
      <p>Chargement des recettes...</p>
  {:then recipes}
      {#each recipes as recipe}
          <RecipeCard recipe={recipe} />
      {/each}
  {/await}
```
On crée le component RecipeCard 
- La partie script
  ```
<script>
    import {link} from "svelte-spa-router"
    export let recipe
</script>
  ```
- La partie HTML
``` 
<img class="recipes" src="{recipe.picture}" alt="première recette" />
    <h3>{recipe.name}</h3> <!--recipe title-->
    <p>{recipe.users}</p> <!--author name-->
    {#each recipe.categories as category}
        <p>{category.Categories_id.name}</p>
    {/each}
    <div class="wrapper">
        <a class="button" href="/recipes" aria-label="Accéder à l'entièreté de la recette" use:link>Voir plus</a>
    </div>
```
