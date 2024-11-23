# Styles

## Styliser une checkbox
```
  input[type=checkbox] {
      appearance: none;          // Retire le style par défaut du navigateur
      -webkit-appearance: none;   // Pour Safari
      -moz-appearance: none;      // Pour Firefox
      -ms-appearance: none;       // Pour Internet Explorer et ancien Edge
      height: 1rem; /* Ajuste la hauteur de la nouvelle checkbox */
      width: 1rem; /* Ajuste la largeur de la nouvelle checkbox */
      background-color: var(--filters);
      cursor: pointer; /* Montre que c'est cliquable */
  }

  input[type=checkbox]:checked {
      background: url('../../assets/logo/signe-de-la-croix-bleuBgFilters.png') no-repeat center center;
      background-size: contain;
      opacity: 1;
  }
```

## Styliser la croix de la barre de recherche
```
  input::-webkit-search-cancel-button {
      -webkit-appearance: none;  /* Retire le style par défaut du navigateur */
      height: 1rem; /* Ajuste la hauteur de l'image */
      width: 1rem; /* Ajuste la largeur de l'image */
      background: url('./assets/logo/signe-de-la-croix.png') no-repeat center center; /* Insère l'image de la croix */
      background-size: contain; /* Ajuste l'image à la taille du bouton */
      opacity: 1; /* Si tu veux une opacité pleine */
      cursor: pointer; /* Montre que c'est cliquable */
  }
```

## Styliser la flèche d'un dropdown
```
select {
    width: 6rem;
    border: none;
    background-color: var(--background);
    font-family: 'enjoyAndRelax';
    font-size: 1rem;
    padding: 0.5rem;
    cursor: pointer;
    // Changer la flèche du dropdown
    appearance: none;          // Retire le style par défaut du navigateur
    -webkit-appearance: none;   // Pour Safari
    -moz-appearance: none;      // Pour Firefox
    -ms-appearance: none;       // Pour Internet Explorer et ancien Edge
    background: url('../../assets/logo/select-bleu.png') no-repeat right;
    background-size: 0.8rem;
}   
```

## Styliser la scrollbar
```
textarea {
    min-height: 1.8rem;
    max-height: 12rem;
    min-width: 10rem;
    max-width: 15rem;
    border: none;
    background-color: #cdf5fa83;

    /* Personnalisation de la scrollbar */
    //Cible la barre de défilement.
    &::-webkit-scrollbar {
        width: 0.4rem; /* Largeur de la barre de défilement */
    }

    //Cible la poignée (partie qu'on déplace pour faire défiler)
    &::-webkit-scrollbar-thumb {
        background-color: var(--fringe-filter);
        border-radius: 0.2rem;
        cursor: grab;
    }
        
    &::-webkit-scrollbar-thumb:active {
        cursor: grabbing;
    }

    //Cible la piste sur laquelle la poignée se déplace
    &::-webkit-scrollbar-track { 
        background-color: var(--filters);
    }

    // Cible uniquement le coin de redimensionnement visible
    &::-webkit-resizer {
        background-color: var(--fringe-filter); /* Change la couleur */
        border-radius: 0.1rem; /* Donne une forme circulaire */
    }
}
```
