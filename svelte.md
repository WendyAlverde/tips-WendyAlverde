# Svelte

## Expression régulière (regex)

### /\D/g
- ```/``` : Les barres obliques encadrent l'expression régulière.
- ```D``` : Cela signifie "non-chiffre" (non-digit). Cela correspond à tout caractère qui n'est pas un chiffre (0-9).
- ```g``` : Le drapeau g signifie global, ce qui permet de rechercher toutes les occurrences dans une chaîne, et pas seulement la première.

.replace(/\D/g, "" = remplace tous les caractères non numériques par une chaîne vide, ne laissant que les chiffres.

### /(\d{2})(?=\d)/g, '$1.'
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
