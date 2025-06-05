# Les commandes git à faire sur le terminal

## Création de repository

Créer un new repository sur GitHub, toutes les commandes sont données par GitHub
- ```git init``` = initialiser le repository
- ```git status``` = voir l'état de notre repos (commande expliquée plus en détails au-dessus)
- ```git add nom-du-fichier``` = Sauvegarder le(s) fichier(s) dans le nouveau repos
- ```git commit -m "nom du commit"``` :
- ```git branch -M main``` = Renommer la branche courante sur laquelle on se trouve (Par convention de GitHub maintenant c'est main)
- ```git remote add origin lienssh``` = quel est le repository distant qui va être lié à ce repo local. Exemple lien ssh : git@github.com:NomGitHub/NomDuRepos.git
- ```git push -u origin main``` = On pousse se qu'on a en local sur GitHub

## Autres commandes souvent utilisées

```git clone``` = cloner le projet de GitHub sur notre VSC

```git status``` = Voir le statut des fichiers :
- Rouge = Changements qui ne seront pas pris en compte pour le commit si on ne les ajoute pas (git add)
- Vert = Prêt à être livrer avec le commit

```git add .``` = Sauvegarder les fichiers. . pour lui dire de prendre tout se qu'il y a dans le dossier courant. On peut aussi ajouter un seul fichier en faisant ```git add nomFichier```

```git commit -m "Nom du commit"``` = Validation des enregistrements des modifications

```git push``` = pousser le projet sur GitHub (*Branche master ou main*)

```git checkout -b nom-branche``` = Créer une nouvelle branche et switch sur celle-ci (checkout = switcher entre les branches / -b = créer) 

```git checkout nom-branche``` = Permet d'aller sur la branche que l'on souhaite

```git branch nom-branche``` = Permet de créer une nouvelle branche (sans être switch dessus)

```git branch -d nom-branche``` = Permet de supprimer une branche, ou -D pour l'obliger à la supprimer

```git branch -a``` = Voir toutes les branches
  - Vert : branche locale sur laquelle on se trouve
  - Blanche : branche locale
  - Rouge : branche distante

```git push -u origin nom-branche``` = Lorsqu'on pousse pour la première fois la branche

```git push origin nom-branche``` = Utilisation en tout temps, pour toute les branches

```git diff``` = Voir les modifications dans le terminal de tous les fichiers ou d'un seul en nommant après la commande le nom du fichier (```git diff nomFichier```)

```git log``` = voir tout les commit

```git pull``` = on récupère le projet modifié ailleurs qu'en local

## Les fusions

Imaginons qu'on a notre branche principale main, une branche dev lier à celle-ci puis une branche front lié à la branche dev.
Si lorsque l'on veut merge il n'y a pas de modification dans la branche dev, par défaut git va faire un fast-forward donc prendre tout les commit de la branche front et les placer devant le dernier commit de la branche dev.
Si on préfère garder un historique,  il faut retirer le fast-forward avec --no-ff.

- ```git checkout nom-branche``` = On se place dans la branche qui va accueillir la fusion (dev)
- ```git merge --no-ff la-branche-quon-veut-merge``` (front)
  -  Une page d'écriture s'ouvre : ctrl + X, N *(Je n'ai pas réussi à changer le nom du commit)*
  -  La branche front existe toujours, la branche dev obtient tous les changements et les commit de la branche front

## Moins utilisé mais très pratique

```git checkout -- .``` : Si tu veux annuler toutes tes modifications locales

```git restore .``` : Version plus moderne pour annuler toutes tes modifications locales

*Cela remet les fichiers dans leur dernier état connu du dernier commit.*

```git reset .``` : Si tu as ajouté des fichiers avec git add, retire-les de l'index

Si il y a oublie de pull avant de travailler sur la branche :
```git pull origin nom de la branche --rebase``` : Récupérer les modifications du dépôt distant avant de pouvoir pousser les notres

## Si modification de nom de projet

Changement sur le terminal:
- ```mv ancienNomProjet nouveauNomProjet```

Vérifier ou changer l’URL du dépôt distant :
- cd nouveauNomProjet
- ```git remote -v```

Si l'URL n'est plus bonne (avec ancienNomProjet)
- ```git remote set-url origin git@github.com:ton-pseudo/nouveauNomProjet.git```

## Vérifier si le dossier est lié au GitHub d'un autre dev

Ce placer dans le dossier du projet
- ```git remote -v```
- Si on y voit quelque chose comme ceci :
  - origin  https://github.com/autreDev/project.git (fetch)
  - origin  https://github.com/autreDev/project.git (push)
- ```git remote remove origin``` : Supprimer l'ancien remote

## Supprimer une branche

- ```git branch -d nom-de-la-branche``` : Utilise -d (safe delete) pour supprimer si la branche est déjà fusionnée
- ```git branch -D nom-de-la-branche``` : Utilise -D (force delete) si elle n'est pas fusionnée ou si tu veux forcer la suppression
- ```git push origin --delete nom-de-la-branche``` : Supprimer une branche distante (sur GitHub)

Pour supprimer toute les branches locales
- ```git checkout main``` : Se placer sur main
- ```git branch | grep -v "main" | xargs git branch -D``` : supprime toutes les branches locales sauf main

## Modifier le nom d'une branche

- ```git branch -m main```

    
*J'ai pris les infos sur les cours O'clock, sur GitHUb et sur la chaîne "Bande de Codeurs" sur Youtube, il a fait deux, très bonnes vidéos explicatives*
