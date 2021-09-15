# Objectifs du TP 


Le but de ce TP est de se mettre à la place d'un personne qui intervient dans une société qui a besoin d'un outil de support pour aider ses clients à remonter leurs problèmes. Pour cela nous devions donc mettre en place un serveur GPLI. 

Nous avions une méthodologie (conseillée) à suivre qui est la suivante : 
    
-  Mettre en place une machine virtuelle (Configuration réseau, accès à Internet, SSH) ;
- Configurer les services réseaux (Adresse IP, résolution DNS) ;
-  Configurer un outil de gestion de ticket (Installer et configurer GLPI, ajouter un Utilisateur, supprimer l’Utilisateur par défaut) ;
- Ajouter au serveur un plugin de remontée de poste client pour pouvoir réaliser l’inventaire du parc (Installer Fusion Inventory) ;
-	Mettre en place un poste client Windows 10 et remonter le poste client dans l’inventaire GLPI (Fusion Inventory) ;
- Mettre en place une sauvegarde de GLPI (Configurer une tâche CRON).

Ensuite, dans un second temps lorsque tout cela était fait nous devions mettre en place un service de messagerie car GPLI propose une solution de depot de ticket par envoi de mail. 

De ce côté, nous étions chargé de : 

-  Déterminer si le serveur de messagerie doit être installé sur le même serveur que GLPI 
- Installer et configurer le service de messagerie 
- Installer et configurer le plugin d’envoi de mail
***

Suivant : [Installation de la VM](TP1/installationVM.md)