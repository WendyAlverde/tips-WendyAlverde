# SQL

## Syntaxe

- Les noms des tables sont entourés de backticks " ` "  pour s'assurer que les noms de tables sont interprétés correctement
- DROP = supprimé
- CREATE TABLE IF NOT EXISTS = Créer la table, si elle n'est pas déjà existante
- COMMENT = commentaire
- VARCHAR = chaîne de caractères
- TIMESTAMP = qui enregistre la date et l'heure de création de l'enregistrement
- TINYINT = spécifier l'ordre d'affichage
- PRIMARY KEY = clé primaire : qui sera un identifiant unique pour chaque enregistrement de la table
- ENGINE = InnoDB; = On spécifie que la table utilise le moteur de stockage InnoDB. Il permet  une meilleure performance et une plus grande fiabilité des données.
- DECIMAL(10,2) = ty décimal avec une précision de 10 chiffres dont 2 après la virgule
- FOREIGN KEY (brand_id) = qui garantit que chaque valeur de « brand_id » correspond à une valeur existante dans la colone « id » de la table « brands »
- INDEX = Pour optimiser les requêtes de recherche
- SET = Restaurer
- START TRANSACTION; = nous permet de regrouper plusieurs opération SQL en une seule unité de travail. Les modifications ne seront pas pris en compte tant que la transaction ne sera pas validée avec COMMIT.
