# Playbook Ansible pour mise en place de conteneurs mariadb et wordpress sous Docker  

## Description:  
Ce playbook permet une mise en place rapide de la machine de production du projet 7 d'OpenClassrooms.  

## Tables des matières:  


## Fonctionnement:  
  * Le playbook installe les packages minimum au fonctionnement de Docker,  
  * Il configure le dépôt de Docker.com (qui provoque des failed sur les commandes apt update qui apparaissent en rouge lors de l'exécution du book mais ils sont ignorés),  
  * Il installe le package docker-ce,  
  * Il ajoute l'utilisateur "aic" dans le groupe docker,  
  * Il construit et démarre un docker mariadb à partir de l'image officielle,  
  * Il construit et démarre un docker wordpress à partir de l'image officielle.  

## Installation:  
1. ***Fichier zip:***  
Télécharger une archive contenant le playbook en cliquant [ici](https://github.com/Yanick-M/P7-ansible-wordpress_containers-playbook/archive/main.zip) 
Décompresser l'archive dans votre espace de travail.  
2. ***Clonage du projet:***  
La deuxième option d'installation est de cloner le projet grâce à "git".  
Placer vous dans votre espace de travail au préalable ou dans le répertoire temporaire.  
```cd /tmp/
git clone https://github.com/Yanick-M/P7-ansible-wordpress_containers-playbook.git  
```  
## Utilisation:  
  * Accéder à l'espace de travail où se situe le playbook,  
  * Modifier les variables dans le répertoire group_vars/ :  
```
nano group_vars/all  
```  
  * Exécuter le playbook avec la commande :  
```
ansible-playbook -b -i inventory.yml website_deployment.yml  
```  
  * Accéder au wordpress avec l'IP du serveur de production et le port 80 à partir d'un navigateur et configurer le CMS,  
  * La base de donnée est accessible avec la commande (nécessite l'installation du client mysql) :  
```
mysql -h 192.168.0.252 -P 33061 --protocol=tcp -u USER1 -p  
(remplacer l'IP et le nom d'utilisateur par ceux qui ont été configurés dans le fichier "all").  
```  

## Prérequis:  
  * Une machine nommée "serveur-supervision" disposant d'Ansible,  
  * Une machine nommée "serveur-production" disposant d'openssh-server,  
  * Chaque machine d'un compte utilisateur "aic" avec des privilèges,  
  * Chaque machine est configuré dans le fichier "/etc/hosts" de l'autre machine,  
  * La liaison ssh de la machine de supervision vers la machine de production avec l'user aic est paramétrée,  
  * Les machines accèdent à internet.  

## Version:  
1.0  

## Licence:  
#### Copyright (c) 2020 [Yanick-M]
#### GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)