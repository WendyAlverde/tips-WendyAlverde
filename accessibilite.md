# Accessibilité

## Attributs de balises HTML

### role="dialog" et aria-modal="true"

Ces attributs sont utilisés pour indiquer qu'une zone est un dialogue modal.
Ils aident les technologies d'assistance à comprendre que cette zone est prioritaire et que le reste de la page est momentanément inaccessible.

- role="dialog" : Indique que l'élément est une boîte de dialogue.
- aria-modal="true" : Signale que le contenu en dehors de ce dialogue ne doit pas être accessible.
*Ces attributs ne fonctionnent pas sur un bouton*

ex : utilisation pour un burger / une modal

## Contrastre de couleur

- Contraste suffisant : Pour du texte normal, le rapport de contraste minimal recommandé est de 4.5:1, et pour du texte large (au moins 18 pt ou 14 pt en gras), il est de 3:1.
- Accessibilité en modes clair/sombre : Si tu proposes plusieurs thèmes (clair/sombre), assure-toi que les deux versions ont un contraste correct.
- Contrastchecker : https://webaim.org/resources/contrastchecker/
- Contrast Finder : https://app.contrast-finder.org/
- Userway : Montre en temps réel se que peux représenter le contraste de couleur sur du texte normal, un input, une case à cocher et un bouton : https://userway.org/fr/verificateur-de-contraste/?fg=000000&bg=ffffff

## Les sites et extentions pour essayer l'accessibilité

### Les sites

- Facil'iti : Adaptation d'affichage selon le profil de l'utilisateur (daltonisme, dyslexie, fatigue visuelle, ...) : https://www.facil-iti.fr/
- Apec utilise Facil'iti et ACEO pour les malentendant : https://app.acce-o.fr/client/apec, https://www.apec.fr
- 

### Les extentions

- Colorblindly, simule les condition de daltonisme : https://chromewebstore.google.com/detail/colorblindly/floniaahmccleoclneebhhmnjgdfijgg?hl=fr

## Les sites références

- Le site d'Horbourg-Wihr : Utilise une option accessibilité : https://www.horbourg-wihr.fr/
- Acceo Tadeo : Mode dyslexie et contraste de site : https://www.acceo-tadeo.fr/
