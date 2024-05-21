# bitwarden-on-premise
Bitwarden on Premise - Raspberry Pi

je me suis lancé dans la mise en place d'un gestionnaire de mot de passe on premise, sur un serveur chez moi à la maison.

état des lieux : actuellement sous bitwarden en mode saas, l'idée est de migrer mes mots de passe sur un serveur en local afin qu'ils ne se trouvent pas sur des serveurs dont je n'ai pas la main.

idée du projet : utiliser IPv6 pour accéder au serveur depuis l'extérieur, sans avoir besoin d'ouvrir des ports sur le routeur ce qui pose souvent des problèmes de sécurité. 

matériel nécessaire : 
* raspberry pi
* alimentation
* cable ethernet
* carte SD
* un opérateur proposant IPv6 (en l'occurence, Free)

j'ai suivi un tuto assez bien fait pour installer bitwarden sur un raspberry, car nativement, l'architecture du processeur du raspberry (arm) n'est pas compatible avec bitwarden. l'idée est donc de faire tourner un conteneur docker qui s'appelle vaultwarden et qui fonctionne tout autant que bitwarden officiel. le voici : https://raspberrytips.fr/installer-bitwarden-sur-raspberry-pi/

en gros, voici les étapes d'installation : 
* installer docker
* installer le conteneur docker et le lancer
* utiliser un DNS pour translater l'IPv6 en une URL
* mettre en place un certificat SSL
