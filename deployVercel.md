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

L'enregistrement A sert à rediriger le **domaine principal** (mon-nom-domaine.com) vers Vercel.

L'enregistrement CNAME set à rediriger le **sous-domaine** www vers Vercel.

Cela permet d’avoir mon-nom-domaine.com et www.mon-nom-domaine.com qui fonctionnent tous les deux correctement avec Vercel.

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

  5- Valeur : cname.vercel-dns.com (ou la valeur recommandée par Vercel)
  
  6- Cliquer sur Valider ou Ajouter

  Une fois les changements effectués, il peut falloir jusqu’à 24h pour que les DNS se propagent.
  
  Vérifier la propagation des DNS sur whatsmydns : [whatsmydns.net](https://www.whatsmydns.net/).

  ### Vérifier que le nom de domaine sur Vercel soit correcte

  - Aller sur le projet
  - Aller dans les settings
  - Dans la section domains, ajouter le domaine www.nom-domaine.com, si il n'y est pas

## Le référencement (SEO)

### Après déploiement ou si l'entreprise existait déjà avant

- Indexation avec Google Search Console, quelques heures à quelques jours
- Google My Business (GMB) : Google My Business permet aux entreprises d’apparaître sur Google Maps et dans les résultats locaux de Google, offrant une meilleure visibilité et facilitant l’accès aux clients.
- Ajouter des backlinks : Les backlinks sont des liens provenant d’autres sites web pointant vers le nôtre. Ils jouent un rôle essentiel en SEO en renforçant notre autorité et notre visibilité sur les moteurs de recherche. (exemple : si un blog ou un média parle de l'entreprise et met un lien vers le site) 

### Format et taille d'image pour les cartes des réseaux sociaux

- Format recommandé : jpeg ou png
- Ratio 1.91:1(paysage) ou 1:1(carré pour Instagram
 
| Réseau            | Taille recommandée  |
|------------------|-------------------|
| **Facebook & LinkedIn** | 1200 x 630 px  |
| **Twitter (X) Card large** | 1200 x 675 px  |
| **Instagram**    | 1080 x 1080 px (carré) |
| **WhatsApp**     | 1200 x 630 px  |

- Sinon mettre une seule image universelle : 1200 x 630 px est le meilleur compromis
