# Sauvegarde GLPI 

## Qu'est ce que une sauvegarde ? Les différents types

En informatique, la sauvegarde est l'opération qui consiste à dupliquer et à mettre en sécurité les données contenues dans un système informatique.

Il existe 4 types de sauvegardes : 

- La sauvegarde complète : Comme son nom l'indique, elle est une sauvegarde **complète** des données à chaque fois qu'on la lance. 

    Avantages : Restauration rapide des fichiers et plus simple 
    Inconvénients : + lent et + d'espace de stockage. 

- La sauvegarde incrémentale : Elle stocke seulement les dernières modifications apportés depuis la dernière sauvegarde

    Avantages : + rapide à sauvegarder, - de quantité de stockage. 
    Inconvénients : + longue à restaurer 

- La sauvegarde différentielle : A la diférence de la sauvegarde incrémentale, la sauvegarde différentielle sauvegarde tous les changements depuis la dernière sauvegarde complète.

    Avantages : temps de restauration rapide
    Inconvénients : + d'espace de stockage que l'incrémentale 

- La sauvegarde Miroir : Cette sauvegarde est une copie exacte des données, il n'y a qu'une seule sauvegarde mais qui contient tout les fichiers du système lors de la dernière sauvegarde. 

    Avantages : Ne contient pas de fichiers obsolètes ou anciens, capacité de restauration rapide. 
    Inconvénients : Problème si un fichier est supprimé et que le système est sauvegardé.

## A quelle fréquence réaliser une sauvegarde sur une base de données en entreprise et quel type de sauvegarde choisir ?

Dans une entreprise, je pense qu'il faudrait réaliser des sauvegarde à une fréquence de 1 par semaine, de préférence a mileu de semaine car si il y'a des problèmes de sauvegarde toutes les personnes capable de les régler sont potentiellement présent. 
En entreprise, je pense que la sauvegarde la plus adapté est tout d'abord de commencer par une sauvegarde complète de tout les fichier, puis toute les semaines de réaliser une sauvegarde différentielle car elle ne sauvegarde que les changements effectué depuis la dernière complète. Je pense que c'est la plus adapté car c'est elle qui a le temps de restauration le plus faible. Il faudra quand même completer celle-ci avec une sauvegarde complète de temps en temps. 


***
## Ma sauvegarde GLPI 

Pour ce qui est de la sauvegarde j'ai tout simplement créer un fichier qui se nomme **./backup.sh** et je suis rentré dedans avec **nano backup.sh** puis j'y ai mis le script suivant : 

```
#!/bin/bash

# Backup Fichier
mkdir /tmp/backup
bkp_dir=/tmp/backup/bkp.tar.gz
glpi_dir=/opt/glpi
bkp_sql=/tmp/backup/bkp.sql
bkp_gen=/tmp/backup.tar.gz
bkp=/tmp/backup

#archive des fichiers de glpi
tar -cvzf $bkp_dir $glpi_dir

#archive de la base de donnée
glpi_user=louis
glpi_pass=azety
mysqldump -u$glpi_user -p$glpi_pass -h localhost glpi > $bkp_sql

#archive des fichiers et de la bdd
tar -cvzf $bkp_gen $bkp
```

Malheuresement, ce script ne marchait pas et m'as mis des erreurs que beaucoup de personne avait dans la classe. Je n'ai donc pas pu sauvegarder ma base de donnée. Je n'ai pas pu donc, dans la logique, l'automatiser avec **crontab**. 

