# Styles

## Styliser une checkbox
```
  input[type=checkbox] {
      -webkit-appearance: none; /* Retire le style par défaut du navigateur */
      -moz-appearance: none; /* Retire le style par défaut du navigateur */
      -ms-appearance: none; /* Retire le style par défaut du navigateur */
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
