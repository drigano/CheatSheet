# Cheat Sheet UNIX
*Résumé non exaustif du contenue du cours UNIX*
# 1) Introduction
### Le noyau
**Le noyau** est la couche de base d’un système d’exploitation.
Il gère la mémoire, l’accès aux périphériques (disque dur, carte son, carte
réseau, etc.), la circulation des données sur le bus, les droits d’accès, les
processus, etc.

<p align="center"> <img src="https://user-images.githubusercontent.com/50296202/192870168-325551bc-2460-4a5c-8f1c-dfaf93b3b7d1.png" /> </p>




## Connexion et déconnexion nom@machine$

### Commandes utiles
- `date` -> affiche la date et l'heure
- `who`  -> liste des utilisateurs connectés
- `cal`  -> affiche le calendrier
- `man`  -> mode d'emploi

## Les fichiers et répertoires

### Trois types de fichiers:
* Fichiers ordinaires : .txt, .exe, données etc.
* Fichiers spéciaux   : ce sont souvent des fichiers servant d’interface pour les divers périphériques (périphérique (/dev), processus, liens, tubes nommés, ...).
* répertoires : Dossiers.

<p align="center"> <img src="https://user-images.githubusercontent.com/50296202/192872172-fac42adf-9aff-4338-8e22-2e4c3b192f55.png" /> </p>


### Les chemins d'accès
#### On distingue deux expressions d’un chemin:
- Le chemin d’accès absolu (chemin absolu)
- Le chemin d’accès relatif (chemin relatif)

### Répertoires utiles
<p align="center"> <img src="https://user-images.githubusercontent.com/50296202/192873671-8aacf9f7-c37e-478f-af8a-dd379cbf279e.png" /> </p>

### Commandes utiles
- `cat`   : affiche le contenu d'un fichier.
- `stat`  : stats d'un fichier.
- `ls`    : affiche les caractéristiques d’une liste de fichiers.
  - `-i` affiche les numéros d’i-nœuds des fichiers.
  - `-a` liste aussi les fichiers cachés.
  - `-l` version longue, détaillé.
  - <a href="https://github.com/drigano/CheatSheet/blob/main/UNIX.md#premier-caract%C3%A8re-des-droits-dans-la-commande-ls--l">Premier caractère des droits dans la commande ls -l</a>
- `rm`    : supprime un fichier.
- `touch` : modifie les caractéristiques de date d’un fichier (permet également de créer un fichier vide).
- `mkdir` : créer un répertoire.
- `cd`    : change le répertoire courant.
- `pwd`   : donne le repertoire courant en chemin absolu.
- `rmdir` : supprime un répertoire vide.
- `cp`    : copie de fichier *source -> destination*
- `mv`    : déplace/renomme un fichier *source -> destination*

## Les liens
Un lien est un fichier spécial qui permet de faire plusieurs références (portant donc des noms identiques ou différents) à un même fichier sur le disque dur.
### Deux types de liens
- liens durs/matériels/physiques
- liens symboliques

### Liens physiques
Il s’agit d’une référence à un fichier, autrement dit, les liens durs lient plusieurs fichiers à un même espace disque.
- Les deux (ou +) fichiers sont indépendants mais il n’existe qu’un fichier situé sur le même espace.
- La modification du lien entraîne la modification automatique du fichier lié.
- Un même fichier peut donc avoir plusieurs noms.

**Les liens physiques sont plusieurs entrées de répertoires du même i-nœud (ce sont donc des fichiers réguliers)**

### Liens symboliques
Un lien symbolique est un fichier de type lien qui contient le chemin et le nom d’un autre fichier, autrement dit, le lien symbolique pointe vers le fichier mais n’occupe pas le même espace mémoire.
- Les accès à un lien sont donc des redirections vers un autre fichier.
- Ainsi, la modification du fichier source ne modifie pas le lien symbolique.
- Un lien se comporte comme un raccourci (alias) vers un autre fichier.
- Le contenu d’un lien est :
  - soit un chemin absolu.
  - soit un chemin relatif (qui doit être valide depuis le répertoire dans lequel se trouve le lien !)

**Les liens symboliques ont chacun leur propre i-nœud ; leur contenu désigne un même fichier régulier (ils sont du type liens)**

### Création de liens
`ln [options] destination nom_du_lien`
- sans option : création de liens physiques
- avec l’option -s : création de liens symboliques

## Notions d’utilisateur et de groupe
Chaque login est relié à un uid (User IDentifier), chaque groupe est relié a un gid (Group IDentifier).
Ces informations sont stockées dans des fichiers d’administration
- `/etc/passwd` contient les informations relatives aux utilisateurs (login, mot de passe crypté, uid, gid, nom complet, répertoire de travail au login, commande exécutée au login)
- `/etc/group` contient les informations relatives aux groupes (nom, mot de passe, gid, liste des membres du groupe)
**Un fichier appartient à un utilisateur et à un groupe**

## Les droits
`ls` permet de visualiser les droits.
### Il existe trois catégories :
- Le propriétaire
- Le groupe propriétaire
- Les autres
### Les droits sont définis par quatres caractères :
- `r`  : read
- `w`  : write
- `x`  : execute
- `-` : none
<p align="center"> <img src="https://user-images.githubusercontent.com/50296202/192885470-ba61f8df-325c-487c-a108-0bf2fdc08402.png" /> </p>

### Modifications des droits
- `chown` : Permet de changer le propriétaire (utilisateur et groupe)
- `chgrp` : Permet de changer le groupe propriétaire
- `chmod` : Permet de changer les droits -> `chmod [options] mode fichier`
  mode : 
  - avec (r,w,x) -> rw--wxr-- ou u=rw- ou o-=x
  - avec la manière numérique en octal -> 777
- `umask` : Permet d’indiquer les droits à la création, les droits obtenus sont le complémentaire de ceux indiqués par le masque.
  - utilise des masques sous forme numérique octale
  - sans paramètre : indique le masque courant
  - avec le masque en paramètre : modifie le masque courant

<p align="center" > <img width="200" src="https://user-images.githubusercontent.com/50296202/192887329-ba411e01-3154-4e61-9773-0c0853c8df7d.png" /></p>

Donc:
- 700 -> `rwx------`
- 751 -> `rwxr-x--x`
- 640 -> `rw-r-----`

## Premier caractère des droits dans la commande ls -l
- `d` : répertoire
- `l` : lien
- `c` : pilote caractère
- `-` : régulier
- `b` : pilote bloc
- `p` : pipe/tube

## Wildcards
Permet d'agir avec plusieurs objets à la fois.
- `*` : tout selectionner.
- `?` : désigne un caractère quelconque.
- `[...]` : désigne un caractère quelconque appartenant à la liste.
- `[ˆ...]` : désigne une liste de caractères à exclure.
- `{...,...}` : désigne une liste de chaînes de caractères.
- `∼` : le tilde est interprété comme le chemin absolue qui conduit au répertoire home.
### Exemple d'utilisation avec ls:
```
$ ls
lulu lala toto titi tata
$ ls l*
lulu lala
$ ls ?a ?a
lala tata
$ ls t[oi]t[oi]
toto titi
$ ls t[ˆoi]t[ˆoi]
tata
```
## Protection de caractères
Le shell utilise defférents caractères particuliers pour effectuer ses propres traitements.
Pour utiliser ces caractères comme de simple caractère, il faut les protéger.
- Utiliser `\` ou `" "` ou `' '` en fonction du contexte.

# Les processus
Un **programme** est une suite d’instructions que le système doit faire exécuter au processeur pour résoudre un problème. La suite d’instructions est rangée dans un fichier.
Un **processus** est un programme en train d’être exécuté par le système dans un environnement donné.

Le processeur bascule entre les différents programmes à exécuter (chacun s’exécutant quelques dizaines de millisecondes).
=⇒ **pseudo-parallélisme**
Modèle conceptuel reposant sur les **processus séquentiels**.

## Représentation interne
Un processus correspond à une zone mémoire de taille fixe dans laquelle on stocke :
- les informations sur le processus
- le code : les instructions à exécuter (dans le langage du processeur)
- la zone de données : les variables manipulées par le code
- la pile d’exécution : les paramètres d’appel des fonctions

Un processus est donc représenté comme un programme qui s’exécute et qui possède son **<a href="https://dictionnaire.sensagent.leparisien.fr/Compteur%20ordinal/fr-fr/">propre compteur ordinal</a>**.
Les différentes informations nécessaires au fonctionnement du processus constituent le **contexte d’exécution** du processus.

## La création d’un processus
Sous Unix les processus forment une hiérarchie :
- Chaque processus à un processus père.
- Un processus peut avoir 0, 1, n processus fils.
*Seul le processus init, le processus qui initialise le système n’a pas de processus père*

## Les modes de fonctionnement
On distingue deux modes de fonctionnement :
- En avant-plan (foreground):
  - Le père attend la terminaison du processus fils avant de lancer un autre processus.
  - L’utilisateur peut interagir avec le processus en cours d’exécution (saisie de données).
- En arrière-plan (background):
  - Le père n’attend pas que le fils ait terminé pour continuer à travailler.
  - Ces processus sont le plus souvent des serveurs en attente de requêtes (par exemple serveur d’impression, serveur de messagerie, . . .)


[//]: # ( <p align="center"> <img src="" /> </p> )









