# Performance du site

Explication des temps de chargements : https://www.yeswedev.bzh/blog/performance-site-internet#:~:text=La%20performance%20d'un%20site%20web%20correspond%20%C3%A0%20l'optimisation,interactions%20simples%20et%20r%C3%A9actives%2C%20etc%E2%80%A6

## Images

### Convertir jpg/png en webp

- Pour convertir une image directement dans VSC (les exemples sont fait avec JPG mais ce sont les mêmes commandes pour PNG) : 
  - Installer webp : ```sudo apt-get install webp```
  - Pour une image : ```cwebp DSC01651.JPG -o DSC01651.webp```
  - Pour convertir toutes les images du dossier d'un coût, ça garde en mémoire celle en jpg : ```for i in *.JPG; do cwebp "$i" -o "${i%.JPG}.webp"; done```

- Si on veut que tous les navigateurs puissent lire la photo, on peut mettre ça dans le code (ne sont pas pris en compte sur les anciennes version de certains navigateurs et ceux qui sont obsolète) : 
```
<picture>
    <source srcset="/images/photo.webp" type="image/webp">
    <source srcset="/images/photo.jpg" type="image/jpeg">
    <img src="/images/photo.jpg" alt="Description de l'image">
</picture>
```
Le navigateur lira donc d'abord le webp et si il n'est pas pris en compte par le navigateur ça appelera l'image en jpg.

### Redimention

- Installer ImageMagick : ```sudo apt-get install imagemagick```
- Utiliser la commande : ```mogrify -resize 800x800 *.JPG```. Ca change la taille de toutes les images. Sinon changer l'étoile par le nom de la photo.

## Codes

- Minify : Extention Prettier - Code formatter pour minifier le code


