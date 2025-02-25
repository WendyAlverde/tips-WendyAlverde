# Déploiement avec Vercel

Prévoir 5h minimum

## Les images dans mon projet

- Mettre les images dans src/assets
- Dans les fichiers qui ont des images faire un import de l’image comme suis : ```import logo from "../../assets/images/logos/logo-blue.webp"```
- Puis dans cette même page, il faut appeler l’image en js : ```<img src={logo} alt="logo">```

## Le déploiement

- add new => project
- Choix du compte et repo git
- Choix de la Root Directory : nom du dossier dans lequel se trouve notre projet
- Build and Output Settings : 
	- Build Commande : Override puis npm run build (Avec utilisation de Svelte)
	- Install Command : Override puis npm install (Avec utilisation de Svelte)

Aller dans l'onglet Domain
- add Domain

### Domaine sur OVH

- Se connecter à OVH
- Dans le tableau de bord, cliquez sur "Domaines" pour voir la liste de vos noms de domaine.
- Cliquez sur le nom de domaine que vous souhaitez configurer.
- Dans le menu à gauche, cliquez sur "Zone DNS" ou "DNS" pour accéder aux paramètres DNS de votre domaine.

#### Ajouter une entrée A à la zone DNS
Si le type d'enregistrement A n'existe pas (sinon faite modifier l'enregistrement A et commencer à l'étape 3) :
  
  1- Cliquez sur "Ajouter un enregistrement" ou "Ajouter une entrée".
  
  2- Choisissez le type d'enregistrement A.
  
  3- Dans le champ "Sous-domaine", laissez vide (pour le domaine principal) ou mettez www (pour le sous-domaine).
  
  4- Entrez l'IP fournie par Vercel : 76.76.21.21 ou 76.76.21.22 (adresse publiques utilisées par Vercel pour le routage de trafic vers les applications déployées
  
  5- Cliquer sur Valider ou Ajouter

#### Ajouter une entrée CNAME à la zone DNS
Si le type d'enregistrement CNAME n'existe pas (sinon faite modifier l'enregistrement CNAME et commencer à l'étape 3) :

  1- Cliquez sur "Ajouter un enregistrement" ou "Ajouter une entrée".
  
  2- Choisissez le type d'enregistrement CNAME.
  
  3- Dans le champ "Sous-domaine", laissez vide (pour le domaine principal) ou mettez www (pour le sous-domaine).
  
  4- Cible : Entrez le nom de votre domaine principal (par exemple, votre-domaine.com).
  
  5- Cliquer sur Valider ou Ajouter

  ### Vérifier que le nom de domaine sur Vercel soit correcte

  - Aller sur le projet
  - Aller dans les settings
  - Dans la section domains, ajouter le domaine www.nom-domaine.com, si il n'y est pas

