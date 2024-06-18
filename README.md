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
* mettre en place un certificat SSL (obligatoire pour créer un compte sur votre interface web, mais au delà de ça, indispensable pour stocker des mots de passe...)

je vais pas redétailler toutes les étapes, le tuto en ligne est assez bien fait pour le coup. pour le DNS, j'ai utilisé https://dynv6.com/, qui après quelques recherches est à ma connaissance le seul qui supporte IPv6.
ça marche plutôt bien, et c'est gratuit.

j'ai quand même eu quelques soucis lors de l'installation, mais rien de méchant. lors de l'installation du certificat SSL Letsencrypt, il arrive parfois que tous les certificats soient pris et qu'il faille attendre pour le générer. la date et l'heure où vous pouvez réessayer sont inscrits dans les logs quand ça vous met l'erreur.

de plus, certains réseaux d'entreprises ayant des exigences de sécurité un peu élevées peuvent bloquer l'accès au serveur à cause du certificat Letsencrypt. du coup je vous invite à utiliser un autre certificat si vous le pouvez, mais letsencrypt fonctionne très bien sur des réseaux domestiques. si vous avez que cet usage là, pour le coup letsencrypt fera tout votre usage.

pour la sauvegarde de la BDD, il faut encore que je me penche sur le sujet. le mieux serait soit d'avoir un sauvegarde de la BDD sur un support externe, un serveur à part, ou encore avoir un 2e serveur bitwarden délocalisé afin d'avoir une redondance. 
_En cours de réflexion_

# renouvellement du certificat

voir : https://chatgpt.com/share/1a3f13d0-f890-4f5f-be06-d54b5febbcbd
