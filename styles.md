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
