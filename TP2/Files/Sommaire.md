# Sommaire :

------
Contexte 👷
>Suite à la perte des serveurs OVH, Marie Richard souhaite rapatrier son serveur web en interne.  
>Il faut donc donc mettre en place un nouveau site web interne.

On va voir comment configurez un DNS mais aussi comment créer une page web avec Apache2
------

Pour ce faire on va passer par plusieurs étapes.

1. [Mise en place des machines virtuelles](VM.md) 💻
2. [Configurer les services Réseaux](ServiceReseau.md) 🔌
   1. [Adresse ip](https://github.com/Matteo-Grellier/TP-Linux/blob/main/TP2/Files/ServiceReseau.md#adresse-ip)
3. [Configurez les services Web](ServiceWeb.md)
   1. [Créer un site Web](https://github.com/Matteo-Grellier/TP-Linux/blob/main/TP2/Files/ServiceWeb.md#cr%C3%A9ation-dun-site-web) 👨‍💻
   2. [Nom de domaine](DNS.md)
   3. [Certificat SSL](SSL.md) 🔑
4. Mise en place d'une solution de haute disponibilité 🕥
   1. Corosync
   2. Pacemaker
