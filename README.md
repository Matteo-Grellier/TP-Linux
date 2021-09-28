# **TP n°1 Linux - Service réseaux 🐧 : Installation d'une GLPI**  

Matteo Grellier  

----------------  

Dans ce cours on va voir comment installer un outil permettant de gérer un parc informaitique ici GLPI.

## Sommaire :

- ## [Définitions](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/D%C3%A9finitions.md#d%C3%A9finitions)

- ## Outil optionnelle pour la mise en place d'un GLPI

  - SSH 🔑 

    - [Parametrer une clé SSH](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/SSH.md#ssh)

- ## Mise en place des machines virtuelles et configuration réseau 💻 - 🛰️

  - [Installation des vm](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/VM_R%C3%A9seaux.md#installation-des-vm)

  - [Configuration du réseau](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/VM_R%C3%A9seaux.md#configuration-du-r%C3%A9seau)

- ## [Installation des différents packages nécéssaires](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/InstallPackages.md#installation-des-packages) 📦

  - MariaDB 
    - [Création de la BDD](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/InstallPackages.md#cr%C3%A9ation-de-la-base-de-donn%C3%A9e-mariadb)

  - [Apache2](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/InstallPackages.md#installer-apache2)

  - [PHP](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/InstallPackages.md#installer-php)

- ## GLPI 

  - [Installation de GLPI](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/GLPI.md#installation-du-glpi)
  
  - [utilisation de GLPI](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/GLPI.md#utilisation-du-glpi)

- ## Installation du plugin FusionInventory sur GLPI 

  - [Installation du plugin FusionInventory](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/FusionInventory.md#installation-du-plugin-fusioninventory)

  - [Installation de FusionInvetory **Agent**](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/FusionInventory.md#installation-de-fusioninventoryagent)

- ## [Mise en place d'une sauvegarde GLPI avec cron](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/Backup.md#mise-en-place-dune-sauvegarde-automatique)

- ## [Conclusion](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/Conclusion.md#conclusion) :

  - [Axe d'améliorations](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/Conclusion.md#axe-dam%C3%A9lioration)

  - [Difficultées](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/Conclusion.md#difficult%C3%A9es)

----------
# **Sources** ℹ️

J'ai utiliser c'est différentes sources pour m'aider à la réalisation de ce tp :

- [OpenClassroom](https://openclassrooms.com/fr/courses/1730516-gerez-votre-parc-informatique-avec-glpi/5993816-installez-votre-serveur-glpi)
- [Wikipedia](https://fr.wikipedia.org/wiki/Gestionnaire_Libre_de_Parc_Informatique)
