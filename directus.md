# Directus

## Installer Node.js

- Se mettre dans un dossier en dehors de notre repository

Voir quel version nous avons de Node.js
- ```nvm --version```

Pour installer Node.js
- ```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash```
Si on a un problème de paquet déjà présent, on peut régler le problème avec la commande
- ```rm ~/.npmrc```

Vérifier que le dossier npm-packages existe
- ```mkdir ~/.npm-packages```

Fermer et ouvrir le terminal

Réessayer la commande pour vérifier que NVM soit installer
- ```nvm --version```

## Installer Node.js LTS

Installer dernièere version LTS
- ```nvm install --lts```

Vérifier la version
- ```node --version```

## Installer Directus

Si on souhaite utiliser une base de données MySQL / MariaDB ou PostgreSQL il faut la créer avant l'initialisation de Directus.
Sinon on choisi une base de données SQLite et pas de paramétrage à faire.

En dehors de notre repository, on crée on dossier pour directus
- ```mkdir directus```

On va dans le nouveau dossier
- ```cd directus```

Installer Directus
- ```npm install directus```

Configurer l'environnement Directus
- ```npx directus init```

Le terminal nous guide pour choisir notre base (choix avec les flèches directives puis entrée)

Il nous montre la route de notre dossier, le choix de l'email et le mot de passe. Pour passer à la suite il faut faire la touche entrée

Faire les deux commandes données par le terminal
- ```cd /var/www/html/CV/bddOcook```
- ```npx directus start```

![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/13964b9b-8cfd-4c87-a78e-14ae576b5654)

## Réouverture Directus
Si on a ce genre de problème :

![image](https://github.com/WendyAlverde/tips-WendyAlverde/assets/148342924/1cc48e34-66cf-400a-a44d-bd743137bf9f)

- ```npm rebuild```
