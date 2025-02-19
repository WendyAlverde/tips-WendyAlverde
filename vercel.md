# Déploiement avec Vercel

## Les images

- Mettre les images dans src/assets
- Dans les fichiers qui ont des images faire un import de l’image comme suis : ```import logo from "../../assets/images/logos/logo-blue.webp"```
- Puis dans cette même page, il faut appeler l’image en js : ```<img src={logo} alt="logo">```


## Le déploiement

- add new => project
- Choix du compte et repo git
- Choix de la Root Directory : nom du dossier dans lequel se trouve notre projet
- Build and Output Settings : 
	- Build Commande : Override puis npm run build
	- Install Command : Override puis npm install

Aller dans l'onglet Domain
- add Domain

### Domaine sur OVH

- Se connecter à OVH
- Dans le tableau de bord, cliquez sur "Domaines" pour voir la liste de vos noms de domaine.
- Cliquez sur le nom de domaine que vous souhaitez configurer.
- Dans le menu à gauche, cliquez sur "Zone DNS" ou "DNS" pour accéder aux paramètres DNS de votre domaine.
- Ajouter une entrée à la zone DNS
  - Cliquez sur "Ajouter un enregistrement".
  - Choisissez le type d'enregistrement A.
  - Dans le champ "Sous-domaine", laissez vide (pour le domaine principal) ou mettez www (pour le sous-domaine).
  - Entrez l'IP fournie par Vercel : 76.76.21.21 ou 76.76.21.22 (adresse publiques utilisées par Vercel pour le routage de trafic vers les applications déployées
  - Modifier le champ CNAME

