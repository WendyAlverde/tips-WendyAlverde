# Svelte

## index.html

### Carte des réseaux sociaux

Dans une application utilisant Vite (vu la présence de vite.config.js), les fichiers du dossier public sont servis à la racine du site, sans le préfixe /public/. Il faut donc écrire le lien de l'image, de cette manière : content="https://www.expertise-automobile-ieta.fr/logoIetaBgGood.jpg"

```HTML
<meta property="og:title" content="Expertise Automobile IETA - Évaluations et Conseils" />
<meta property="og:description" content="Obtenez une expertise automobile fiable avec IETA. Contactez-nous pour une évaluation précise." />
<meta property="og:image" content="https://expertise-automobile-ieta.fr/images/preview.jpg" />
<meta property="og:url" content="https://expertise-automobile-ieta.fr" />
<meta property="og:type" content="website" />

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="Expertise Automobile IETA - Évaluations et Conseils" />
<meta name="twitter:description" content="Obtenez une expertise automobile fiable avec IETA. Contactez-nous pour une évaluation précise." />
<meta name="twitter:image" content="https://expertise-automobile-ieta.fr/images/preview.jpg" />
```
- Tester sur Facebook : https://developers.facebook.com/tools/debug/
- Tester sur Twitter : https://threadcreator.com/tools/twitter-card-validator
- Tester sur LinkedIn : https://www.linkedin.com/post-inspector/

## Expression régulière (regex)

### Téléphone
```Svelte
let tel = ''; // Définition d'une variable tel avec laquelle on fait le lien dans l'input grâce a = bind:value={tel}

function formatPhoneNumber() {
    let value = tel.replace(/\D/g, ''); // Supprime tout les caractères numériques
    if (value.length > 10) value = value.slice(0, 10); // Limite la longueur du numéro à 10 chiffres
    tel = value.replace(/(\d{2})(?=\d)/g, '$1.'); // Applique le format souhaité à savoir un point tout les deux chiffres
}
```

#### /\D/g
- ```/``` : Les barres obliques encadrent l'expression régulière.
- ```D``` : Cela signifie "non-chiffre" (non-digit). Cela correspond à tout caractère qui n'est pas un chiffre (0-9).
- ```g``` : Le drapeau g signifie global, ce qui permet de rechercher toutes les occurrences dans une chaîne, et pas seulement la première.

.replace(/\D/g, "" = remplace tous les caractères non numériques par une chaîne vide, ne laissant que les chiffres.

#### /(\d{2})(?=\d)/g, '$1.'
- ```(\d{2})``` :
  - ```\d``` : Correspond à un chiffre (0–9).
  - ```{2}``` : Spécifie que l'on veut exactement 2 chiffres consécutifs.
  - ```()``` : Capture ces deux chiffres en tant que groupe (groupe capturant 1).
- ```(?=\d)``` :
  - ```(?=...)``` : C'est une assertion de regard en avant positive (positive lookahead). Cela vérifie qu'un chiffre suit immédiatement, mais sans l'inclure dans la correspondance.
  - ```\d``` : Vérifie la présence d'un chiffre après les deux chiffres capturés.
- ```'$1.'```
  - ```$1``` : Représente le premier groupe capturé, c'est-à-dire les deux chiffres trouvés par (\d{2})
  - ```.``` : Ajoute un point après chaque paire de chiffres capturés.
 
L'objectif est de formater une chaîne en ajoutant un point après chaque paire de chiffres, sauf à la fin si un seul chiffre reste.

### Email version 1

```Svelte
let email = '';
let errorMessage = '';

function validateEmail() {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
    errorMessage = "Veuillez entrer une adresse email valide.";
    } else {
    errorMessage = '';
    }
}
```
#### /^[^\s@]+@[^\s@]+\.[^\s@]+$/

- ```^``` : Ancre de début qui signifie que la correspondance doit commencer au tout début de la chaîne.
- ```[^\s@]+``` : Une séquence d'un ou plusieurs caractères qui ne sont ni des espaces blancs ni le caractère @.
  - ```[ ]``` : Définit une classe de caractères, c'est-à-dire un ensemble de caractères possibles.
  - ```^``` (dans ```[^]```) :    : Inverse la classe, indiquant les caractères interdits.
  - ```\s``` : Représente les espaces blancs (espace, tabulation, saut de ligne).
  - ```@``` : Spécifie que le caractère @ n'est pas autorisé ici.
  - ```+``` : Indique une ou plusieurs occurrences des caractères valides (autorisés par la classe inversée).
- ```@``` : Correspond exactement au symbole @. Cela s'assure qu'une adresse email contient ce caractère.
- ```[^\s@]+``` : Répète la même logique pour la partie après le @, avant le point ., indiquant un domaine valide sans espaces ni @.
- ```\.``` : Correspond exactement au point . (doit être échappé avec \ car le point a un sens spécial en regex).
-  ```[^\s@]+``` : Encore une fois, une séquence de caractères qui ne sont ni des espaces ni @ (cette fois pour la partie après le point, comme com, org, etc.).
-  ```$``` : Ancre de fin, signifiant que la correspondance doit se terminer ici.

#### on:blur={validateEmail}

- Lorsqu’on quitte le champ, la fonction ```validateEmail``` vérifie le format avec une expression régulière stricte (```emailRegex```).

#### disabled={!!errorMessage}

- Le bouton **Envoyer** est désactivé tant que l'eamil n'est pas valide

### Email version 2

```Svelte
let email = '';
let errorMessage = '';

function validateEmail() {
    const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    
    if (!emailRegex.test(email)) {
        errorMessage = "Veuillez entrer une adresse email valide.";
    } else {
        errorMessage = '';
    }
}
```
- ```[a-zA-Z0-9._%+-]+```  (avant le ```@```) :
  - Accepte uniquement des lettres (a-z, A-Z), des chiffres (0-9), et les caractères ., _, %, +, -.
  - N'autorise pas d'espaces ou de caractères spéciaux comme @, ce qui empêche un @ avant l'emplacement prévu.
- ```@[a-zA-Z0-9.-]+``` (après le ```@```) : Accepte un seul @ suivi de caractères valides pour les noms de domaine (lettres, chiffres, tirets, et points).
- ```\.[a-zA-Z]{2,}$``` (fin de l'adresse) : Vérifie que l'adresse se termine par un TLD (comme .com, .org, .fr), avec au moins 2 lettres après le dernier point.

## Accordéon

### Sur la page contenant l'accordéon

La section, le titre puis l'appel du Composant
```Svelte
<script>
    // Import composants
    import Accordion from '../components/Accordion.svelte';
    export let title = "FAQ";
</script>

<section class="faq">
    <h2>{title}</h2>
    <Accordion />
</section>
```

### Sur le Composant Accordeon

```Svelte
<script>
    const questions = [
        // Contenu sous forme de liste
        {
            title: 'Pourquoi faire appel à un expert en automobile ?',
            content: [
                'L’expertise automobile répond à plusieurs besoins techniques et pratiques :',
                {
                    type: 'list',
                    items: [
                        'A : L’expert.',
                        'Z : Cela.',
                        'E : Véhicules.',
                        'R : Garantir.',
                    ]
                }
            ]
        },
        // Contenu sous forme de paragraphe
        {
            title: "Je viens d'acquérir un véhicule d'occasion, il est affecté d'avaries, quels sont mes recours ?",
            content: 'En cas ...'
        },

    let openIndex = null;
    
    const toggleAccordion = (index) => {
        openIndex = openIndex === index ? null : index; // Ferme si la même section est cliquée  
    };

    // Accessibilité
    const handleKeydown = (event, index) => {
    if (event.key === 'Enter' || event.key === ' ') {
        toggleAccordion(index);
        }
    };
</script>

<div class="accordeon" >
    {#each questions as question, index}
        <!-- J'ai ajouté l'événement on:click sur cette div afin de permettre de cliquer n'importe où dans l'accordéon pour le fermer.  -->
        <!-- Si cela pose problème, vous pouvez déplacer l'événement sur la div située en dessous. -->
        <!-- La navigation clavier est prise en charge avec tabindex="0" et on:keydown. -->
        <div class="accordeon-item" role="button" tabindex="0" aria-expanded={openIndex === index ? 'true' : 'false'} aria-controls={`panel-${index}`} on:keydown={(e) => handleKeydown(e, index)} on:click={() => toggleAccordion(index)}>
            <div class="accordeon-item-header">
                <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                <h3>{question.title}</h3>
            </div>

            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
                    <!-- Si l'élément est une simple chaîne de caractères, l'affiche dans un paragraphe -->
                    {#if typeof question.content === 'string'}
                        <p>{question.content}</p>
                    <!-- Si l'élément est un tableau, on boucle dessus -->
                    {:else if Array.isArray(question.content)}
                        {#each question.content as contentItem}
                            <!-- Si l'élément est une chaîne de caractères, l'affiche dans un paragraphe -->
                            {#if typeof contentItem === 'string'}
                                <p>{contentItem}</p>
                            <!-- Si l'élément est une liste, on l'affiche dans une liste non ordonnée -->
                            {:else if contentItem.type === 'list'}
                                <ul>
                                    {#each contentItem.items as item}
                                        <li>{@html item}</li>
                                    {/each}
                                </ul>
                            {/if}
                        {/each}
                    {/if}
                </div>
            {/if}
        </div>
    {/each}
</div>
```
