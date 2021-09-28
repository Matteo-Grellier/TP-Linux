# Installation des packages

## Être SuperAdministrateur

Vous devez être SuperAdministrateur avant d'utiliser toutes les commandes.
Pour cela, écrivez `su -` dans votre terminale et taper votre mot de passe SuperAdministrateur créer lors de l'initialisation de votre vm Debian

## Installation des modules complémentaires

Il est nécéssaire d'installer ces modules complémentaires pour pouvoir utiliser GLPI sans problème.
`apt-get install apcupsd php-apcu`

- ## Création de la base de donnée Mariadb

Pour ce faire, je vais sur ma vm Debian et je tape la commande `mysql -u root -p`
Entrer votre mot de passe.
Ensuite, vous êtes dans le prompt de MariaDB.
Écrivez ces commandes :

:warning: n'oubliez pas de mettre un `;` à la fin des commandes :warning:

`create database glpidb;`
`grant all privileges on glpidb.* to glpiuser@localhost identified by "[votremotdepasse]";`
`quit`

- ### Installer Apache2

Pour installer Apache2 utiliser la commande :
`apt-get install apache2 php libapache2-mod-php`

- ### Installer PHP

Utiliser cette commande pour installer PHP et des modules PHP nécéssaire au bon fonctionnement du GLPI :
`apt-get install php-imap php-ldap php-curl php-xmlrpc php-gd php-mysql php-cas`

- ## Finalisation

Pour terminer l'installation des différents packages, on va redémarrer le serveur apache2 et la BDD.

``/etc/init.d/apache2 restart``
``/etc/init.d/mysql restart``  

[<--- Sommaire](https://github.com/Matteo-Grellier/LinuxGLPI) --- Page 4 --- [GLPI --->](https://github.com/Matteo-Grellier/LinuxGLPI/blob/main/Files/GLPI.md#installation-du-glpi)