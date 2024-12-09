# Accéssibilité

## role="dialog" et aria-modal="true"

Ces attributs sont utilisés pour indiquer qu'une zone est un dialogue modal.
Ils aident les technologies d'assistance à comprendre que cette zone est prioritaire et que le reste de la page est momentanément inaccessible.

- role="dialog" : Indique que l'élément est une boîte de dialogue.
- aria-modal="true" : Signale que le contenu en dehors de ce dialogue ne doit pas être accessible.
*Ces attributs ne fonctionnent pas sur un bouton*

ex : utilisation pour un burger / une modal
