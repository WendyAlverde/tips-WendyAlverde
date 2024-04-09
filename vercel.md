# Déploiement avec Vercel

## Les images

- Mettre les images dans src/assets
- Dans les fichiers qui ont des images faire un import de l’image comme suis : ```import ocooklogo from "../../assets/images/logos/ocook-logo-blue.webp"```
- Puis dans cette même page, il faut appeler l’image en js : ```<img src={ocooklogo} alt="O'cook-logo">```


## Le déploiement

- add new => project
- Choix du compte et repo git
- Choix de la Root Directory : ocook
- Build and Output Settings : 
	- Build Commande : Override puis npm run build
	- Install Command : Override puis npm install
