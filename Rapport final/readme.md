# Informations sur notre rapport

Notre rapport sur la SAE 2.03 porte sur l'installation automatisée de Debian ainsi que sur les systèmes Git. Dans ce rapport nous avons choisis de ne pas répondre aux questions des semaines de façon explicites, mais les réponses sont bien dans notre rapport. Ci dessous, vous trouverez de façon explicites, les questions ainsi que nos réponses sur nos différents rapports de chaque semaine.

De plus, pour ce rapport nous l'avons fait intégralement en **Markdown**, puis nous l'avons converti en HTML puis ensuite en pdf.

# **Rapport 1 - Installation Debian**

## <font color="blue">Questions</font>

### *Question(s) 1. Configuration matérielle dans VirtualBox*
* Que signifie “64-bit” dans “Debian 64-bit” ?
> Dans une version d’un système d’exploitation de 64 bits, 64 bits signifie que les informations qu’envoie les informations au processeur, sont codées sur 64 bits, un système d’exploitation 64 bits est donc conçu pour un processeur avec une architecture 64 bits.
* Quelle est la configuration réseau utilisée par défaut ?
>Dans la configuration de base de VirtualBox, le réseau est configuré en NAT.
* Quel est le nom du fichier XML contenant la configuration de votre machine ?
>La configuration de la machine virtuelle, est stocké en XML dans le fichier qui porte le sae203.vbox.
* Sauriez-vous le modifier directement ce fichier pour mettre 2 processeurs à votre machine ?
Faites-le
>Oui sur la ligne 91 du fichier XML, il y a une balise « CPU count= » où l’on peut mettre le nombre que l’on souhaite, cela change le nombre de processeur que la machine virtuelle va utiliser.
___
### *Question(s) 2. Installation OS de base :*
* Qu’est-ce qu’un fichier iso bootable ?
>Un fichier iso bootable, est un fichier d’extension iso, qui contient des composants logiciel, qui peuvent être démarré directement sur l’ordinateur sans passer par un système d’exploitation. Un fichier bootable est souvent une installation de système d’exploitation
* Qu’est-ce que MATE ? GNOME ?
>MATE est un environnement de bureau (Permet de manier l’ordinateur via un environnement graphique), alors que GNOME est un environnement graphique (dispositif de dialogue homme-machine, dans lequel les objets à manipuler sont dessinés sous forme de pictogrammes à l'écran).
* Qu’est-ce qu’un serveur web ?
>Un serveur web est un ordinateur dédié à l'hébergement de sites internet, qui gère les demandes des clients (navigateurs web) en leur transmettant les pages web demandées.
* Qu’est-ce qu’un serveur ssh ?
>Un serveur SSH est un serveur qui permet à des utilisateurs de se connecter de manière sécurisée à un ordinateur distant en utilisant le protocole SSH, pour transférer des fichiers ou exécuter des commandes par exemple.
* Qu’est-ce qu’un serveur mandataire ?
>Un serveur mandataire est un serveur qui agit comme un intermédiaire entre un client et d'autres serveurs. Le client envoie une demande à un serveur mandataire, qui se connecte alors au serveur cible et transmet la demande.
---
### *Question(s) 3. sudo*
* Comment peux-ton savoir à quels groupes appartient l’utilisateur user ?
>La commande “adduser user sudo” permet d’ajouter l’utilisateur user au groupe sudo.Deux manières de voir les groupes d’un utilisateur : 
groups → permet de voir les groupes de l’utilisateur courant
groups user → permet de voir les groupes de l'utilisateur nommé “user”
___
### *Question(s) 4. Suppléments invités*
* Quel est la version du noyau Linux utilisé par votre VM ? N’oubliez pas, comme pour toutes les
questions, de justifier votre réponse.
>Pour connaître la version du noyau linux utilisée, il suffit de taper la commande “uname -mr” dans le terminal. La version de notre VM est la “5.10.0-21-amd x86_94
* À quoi servent les suppléments invités ? Donner 2 principales raisons de les installer.
>Les suppléments invités permettent un meilleur confort dans l’utilisation de la VM. Par exemple :
Le presse-papiers est partagé entre la machine virtuelle et la machine hôte.
Les dossiers peuvent être échangés entre la VM et la machine hôte.
Le pointeur de souris est le même pour la VM et la machine hôte ce qui permet de ne plus appuyer sur la touche hôte pour ré-utiliser la souris sur la machine hôte.
* À quoi sert la commande mount (dans notre cas de figure et dans le cas général) ?
>Dans un cas général, la commande mount permet de monter un système de fichier qui est disponible sur un périphérique quelconque. Dans notre cas, elle monte les fichiers nécessaires permettant d’utiliser les fonctionnalités des suppléments invités.

# **Rapport 2 -  Installation Debian automatisée par pré-configuration**

## <font color="blue">Questions</font>
### *Question 1 : Qu’est-ce que le Projet Debian ? D’où vient le nom Debian ?*
> Le projet Debian est un groupe de développeurs volontaires, qui cherchent à créer un système d'exploitation composé de logiciels libres. A sa création c'est la seule distribution ouverte aux contributions de tout développeur ou utilisateur. C'est toujours le seul distributeur Linux majeur qui ne soit pas une entité commerciale. &nbsp; Le nom Debian vient de 2 prénoms celui de l'épouse du créateur de l'OS "Debra" et de son créateur "Ian", ce qui a donné "Debian"
&nbsp;
[Source](https://www.debian.org/doc/manuals/project-history/intro.fr.html)
#### La maintenance
### *Question 2 : Il existe 3 durées de prise en charge (support) de ces versions : la durée minimale, la durée en support long terme (LTS) et la durée en support long terme étendue (ELTS). Quelle sont les durées de ces prises en charge ?*
> La durée minimale de prise en charge est environ de 3 ans, pour la durée en support long terme, le temps est d'environ de 2 ans supplémentaires de la durée minimale. Et la durée en support long terme étendue ajoute 5 ans supplémentaires au LTS, 10 ans cumulés. &nbsp;[Source:DebianReleases](https://wiki.debian.org/fr/DebianReleases)
[Source:DebianWiki-LTS](https://wiki.debian.org/fr/LTS)
[Source:DebianWiki-ELTS](https://wiki.debian.org/fr/LTS/Extended)
### *Question 3 : Pendant combien de temps les mises à jour de sécurité seront-elles fournies ?*
> Après la durée minimale, l'équipe LTS s'occupe de la sécurité de la version mais, pas l'équipe ELTS
&nbsp; [Source:DebianWiki-LTS](https://wiki.debian.org/fr/LTS)
#### Nom générique, nom de code et version
### *Question 4 : Combien de version au minimum sont activement maintenues par Debian ? Donnez leur nom générique (= les types de distribution).*
> 2 versions : Bullseye, Buster sont encore maintenues.
[Source](https://wiki.debian.org/fr/DebianReleases)

### *Question 5 :Chaque distribution majeur possède un nom de code différent. Par exemple, la version majeur actuelle (Debian 11) se nomme Bullseye. D’où viennent les noms de code données aux distributions ?*
>Les noms de code des versions de Debian viennent des noms des personnages des films Toy Story.
&nbsp; [Source](https://wiki.debian.org/DebianBuzz)

### *Question 6 : L’un des atouts de Debian fut le nombre d’architecture (≈ processeurs) officiellement prises en charge. Combien et lesquelles sont prises en charge par la version Bullseye ?*
9 architectues sont compatibles.

>* amd64
>* i386
>* ppc64el
>* s390x
>* armel
>* armhf
>* arm64
>* mipsel
>* mips64el
&nbsp; [Source](https://wiki.debian.org/DebianBullseye#Architectures)

### *Question 7 : Première version avec un nom de code*
* Quelle a était le premier nom de code utilisé ?
> Le premier nom de code utilisé est Buzz
* Quand a-t-il été annoncé ?
> Il a été publié le 17 Juin 1996
* Quelle était le numéro de version de cette distribution ?
> Son numéro de version était le 1.1
&nbsp; [Source:DebianReleases](https://wiki.debian.org/fr/DebianReleases)
&nbsp; [Source:DebianBuzz](https://wiki.debian.org/DebianBuzz)

### *Question 8 : Dernière nom de code attribué*
* Quel est le dernier nom de code annoncée à ce jour ?
> Le dernier nom de code utilisé est Forky
* Quand a-t-il été annoncé ?
> Il a été annoncé le 13 octobre 2022
* Quelle était le numéro de version de cette distribution ?
> Sa version est la version 14
&nbsp; [Source:DebianReleases](https://wiki.debian.org/fr/DebianReleases)
&nbsp; [Source:DebianForky](https://wiki.debian.org/DebianForky)


# **Rapport 3 - Gitea**

## Introduction

Dans le cadre de notre projet, nous avons étudié le logiciel Gitea qui est une solution open source de gestion de projets Git. Dans ce rapport, nous allons répondre aux questions posées en détaillant chacune des réponses.

## Questions

1. Préliminéaire

* Qu'est-ce que le logiciel *git-gui*? Comment se lance t-il?

Git-gui est une interface graphique pour git, qui permet aux utilisateurs d'accéder à toutes les fonctionnalités de git (commits, branches, etc.) via une interface utilisateur graphique.

* Mêmes questions avec gitk

Gitk est également une interface graphique pour Git, qui permet de visualiser les commits, les branches et les tags d'un projet Git. Gitk est installé avec Git et peut être lancé en utilisant la commande gitk dans le terminal.

* Quelle sera la ligne de commande git pour utiliser par défaut le proxy de l’université sur tous vos
projets git ?

Pour utiliser le proxy de l'université sur tous les projets Git, il faut exécuter la commande suivante dans le terminal :

```bash
git config --global http.proxy http://cache.univ-lille.fr:3128
```

2. A propos de Gitea

* Qu'est-ce que Gitea ?

Gitea est une solution open source de gestion de projets Git, qui permet aux développeurs de collaborer sur un même projet en toute simplicité. Gitea est écrit en langage de programmation Go et est conçu pour être léger, rapide et facile à installer et à utiliser.

* À quels logiciels bien connus dans ce domaine peut-on le comparer (en citer au moins 2) ?

Gitea peut être comparé à plusieurs logiciels bien connus dans le domaine de la gestion de projets Git, tels que GitLab, GitHub, Bitbucket, SourceForge et GitKraken

## Commandes

### Installation de Gitea

Pour installer Gitea, il faut tout d'abord télécharger le fichier d'installation `/usr/bin/gitea` sur le site officiel de Gitea. Une fois le fichier téléchargé, il faut lui donner les droits d'exécution en exécutant la commande `chmod +x /usr/bin/gitea/fichierinstallation`.

### Démarage automatique de Gitea

Pour que Gitea démarre automatiquement lors du démarrage de la machine, il faut créer un fichier de service pour systemd en éditant le fichier `/etc/systemd/system/gitea.service` avec la commande `sudo nano /etc/systemd/system/gitea.service`

Ensuite, il faut copier et coller le contenu du fichier de service disponible sur le site officiel de Gitea dans le fichier `/etc/systemd/system/gitea.service` Une fois le contenu collé, il faut enregistrer le fichier et quitter l'éditeur de texte.
Une fois le fichier texte sauvegardé, il suiffit de mettre ces deux commandes :

```bash
sudo systemctl enable gitea
sudo systemctl start gitea
```