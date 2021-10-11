# High Accessibility

## Prérequis

Nous allons utiliser la deuxième machine virtuelle créer au début du tp.

J'ai modifié le nom de mon DNS, au lieu d'`inform` j'ai mis ``inform-main`` et j'en ai créé une autre avec l'adresse ip de ma seconde machine au nom d'`inform-second`

- Dans cette partie on va voir comment mettre en place un serveur secondaire qui va intervenir lorsque le serveur primaire aura des problèmes.
- On va se servir de notre deuxième VM.

Installation des paquets nécéssaires au fonctionnement de Pacemaker et corosync : 
`apt install pacemaker corosync crmsh`

------------

## Installation

✍️ Un Cluster en informatique est un groupe de serveur ✍️

Il va falloir installer 3 packages dont : Pacemaker, Corosync, crmsh

- Pacemaker est un gestionnaire de resource automatisé, ils nous permettras de détecter lorsqu'un serveur serat défaillants.  
- Corosync est un logiciel open source qui nous permettrat de maintenir notre cluster. En redémarrant des processus par exemple
- crmsh est un terminal spécial pour entrer des commandes pacemaker.

![installation](../Screens/2021-10-09-235650.png)

Nous devons ensuite générer une clé d'authentification sur la machine principale pour lier nos deux noeuds

✍️ Un noeud c'est comme cela que sont appelés nos deux VM ici noeud 1 et noeud 2 ✍️

![](../Screens/2021-10-09-235812.png)

On va copier cette clé vers le deuxième noeud, ici VM-second

![](../Screens/2021-10-09-235912.png)  

Il faut maintenant configurer le réseau privé dans lequel nos deux noeuds vont communiquer  

Et pour cela il faut modifier le fichier `corosync.conf`

![](../Screens/2021-10-10-143544.png)

et y remplacer toutes les lignes par celle-ci 👇
🚨 Il faut bien remplacer les différentes zones par vos addresses ip et BROADCAST 🚨

Votre addresse Broadcast se situe ici :
![](../Screens/2021-10-10-144551.png)

````
logging {
  debug: off
  to_syslog: yes
}
nodelist {
  node {
    name: inform-main
    nodeid: 1
    quorum_votes: 1
    ring0_addr: [IPV4MAIN]
  }
  node {
    name: inform-second
    nodeid: 2
    quorum_votes: 1
    ring0_addr: [IPV4SECOND]
  }
}
quorum {
  provider: corosync_votequorum
}
totem {
  cluster_name: cluster-ha
  config_version: 3
  ip_version: ipv4
  secauth: on
  version: 2
  interface {
    bindnetaddr: [BROADCAST]
    ringnumber: 0
  }
}
````

Il faut ensuite copier ce fichier vers le noeud secondaire 

![](../Screens/2021-10-10-144908.png)

Avant de pouvoir tester les changements, il faut redémarrer corosync avec cette commande :
`service corosync restart`

pour voir le statut de notre cluster, il suffit d'écrire `crm_mon --one-shot -V`

On peut voir que les deux nodes sont ONLINE et donc peuvent communiquer entre eux.

![](../Screens/2021-10-09-232800.png)

## Créer une ip failover 

On va maintenant voir comment configurer une ip virtuelle liée à une ressource et pour cela on va créer une nouvelle configuration

Pour commencer il faut créer une nouvelle configuration 

![](../Screens/2021-10-10-000305.png)

Ensuite on désactive certaines fonctionnalités pas utile pour ce tp : 

![](../Screens/2021-10-10-000325.png)  
![](../Screens/2021-10-10-000350.png)

On définit l'ip ?

On peut voir avec la commande `crm_mon --one-shot -V` qu'une nouvelle ressource à été rajouté.

![](../Screens/2021-10-09-235335.png)

A partir de cette étape on pourrait tester la Haute Disponibilité avec les commandes suivantes :
`sudo crm cluster start`
et pour arreter le test,  
`sudo crm cluster stop`

Et on pourrait voir que le site changerait de contenu lorsque le serveur principal serait down.

<--- [Certificat SSL](SSL.md) |Page 6| [Conclusion](Conclusion.md) --->