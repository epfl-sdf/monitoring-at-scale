%Git, Easy Branching
%Malik Bougacha \& Marc Schaer
%25 août 2015

# Introduction

### git ? 

\center
\includegraphics[width=10cm]{img/logo.png}

### Qu'est-ce que git ?

Système de gestion de contenu

\pause

* Gestion de version
\pause

* Distribué
\pause

* Gestion facilitée de branches
\pause

* Efficace

### Son histoire

Avril 2005 : créé par Linus Torvalds comme un successeur de Bitkeeper

. . .

* Initialement en Bash

. . .

* Réécriture en C 

. . .

* Prendre CVS comme l'exemple à ne pas faire (WWCVSND: What would CVS never do ?)

. . .

* Imaginé pour un workflow distribué


### Pourquoi git ?

* Prise en main aisée
\pause

* Création de branches simples et rapides
\pause

* Efficace même avec des milliers de branches
\pause

* Fusion de code simplifiée et claire
\pause

* Collaboration facilitée

### Configuration globale

Configuration d'un utilisateur
```
git config --global user.name John Doe
git config --global user.email john.doe@epfl.ch
```
. . .

* Nom d'utilisateur

* E-mail


### Initialiser un dépôt

* Création d'un dépôt local :
```sh
git init
```

* Récupération d'un dépôt distant dans un dépôt local
```sh
git clone $URI
```

### Qu'est-ce qu'un commit ?

Un commit contient:

* Un auteur (nom d'utilisateur, email)

. . .

* Une date

. . .

* Un snapshot de l'état actuel du dépôt

. . .

* Un commentaire indiquant le contenu du commit

### Gestion des fichiers dans git

\center
\includegraphics[width=10cm]{img/work_no_array.png}

### Gestion des fichiers dans git (2)

\center
\includegraphics[width=10cm]{img/work_stag_no_array.png}

### Gestion des fichiers dans git (3)

\center
\includegraphics[width=10cm]{img/work_stag.png}


### Gestion des modifications sur un commit

* Ajouter des modifications à un futur commit
```sh
git add
```
    * Nouveau fichier
    * Ancien fichier
    * Détection des fichiers déplacés

. . .

* Lister les fichiers suivis par git
```sh
git ls-files
```

### Gestion des modifications sur un commit (2)

* Enlever des modifications d'un futur commit
```sh
git reset
```

### Gestion des modifications sur un commit (3)

* Regarder ce qui va etre "commité"
```sh
git status
```

### Gestion des modifications sur un commit (4)

\center
\includegraphics[width=10cm]{img/work_stag_commit_one_arrow.png}

Note: repository est local

### Gestion des modifications sur un commit (5)

\center
\includegraphics[width=10cm]{img/work_stag_commit.png}

Note: repository est local


### Gestion des modifications sur un commit (6)

* Finalement faire le commit
```sh
git commit -m 'ceci est un message de commit'
```

. . .

* Tout ceci en une seule ligne - rapide et efficace
```sh
git commit -a
```
. . .

* Lister les derniers commits
```sh
git log
```

# Plus de branches !

### Pourquoi ?

Objectifs :

* Séparer la production du développement
* Une branche = une feature/bug fix
* Permet d'avoir des environnements de développement facilement


### Gestion d'une branche

* Créer une branche
```sh 
git branch new_feature
```
. . .

* Changer de branche
```sh 
git checkout new_feature
```

. . .


* Le tout en une seule commande
```sh
git checkout -b new_fast_feature
```

### Commit dans une branche

```sh 
git commit -m 'message de commit dans la branche'
```

### Fusionner la nouvelle branche dans la branche master

* Savoir où l'on se trouve
```sh 
git branch
```


* Se déplacer sur la branche master
```sh 
git checkout master
```

* Fusionner la branche new_feature_for_cat dans master
```sh 
git merge new_feature_for_cats
```
    ou
```sh 
    git merge new_feature_for_cats master
```

# Mais plus de conflits !

### Création d'un conflit

* Modification d'un fichier sur la branche active (master) suivi d'un commit

. . .

* Se déplacer sur une branche
```sh 
git checkout new_feature_for_cats
```
. . .

* Modification des mêmes lignes du même fichier suivi d'un commit

. . .

* Retour sur la branche master
```sh 
git checkout master
```

. . .

* Création d'un conflit
```sh 
git merge new_feature_for_cats
```

### Gérer un conflit

* Diagnostique du conflit
```sh 
git status
```
. . .

* Résolution des conflits (à travers un éditeur de texte)

. . .

* Considérer les modifications et les "commiter"
```sh 
git add
git commit
```

# Plus de personnes, plus de collaboration !


### Gestion d'une branche distante
* Prendre l'état du dépôt distant et le copier localement
```sh 
git fetch 
```
    * -p pour enlever les branches locale qui n'existent plus sur le serveur distant

* Fusionner l'état d'une branche de la remote et la branche locale
```sh 
git merge origin/master
```
. . .

* En plus court :
```sh 
git pull origin master
```

### Gestion d'une branche distante (2)

* Envoyer l'état de sa branche locale sur le serveur distant
```sh 
git push origin master
```

# Comparaison des performances - svn vs git


### svn vs git[^2]

Action                | git    | svn    | amelioration |
-------               | ------ | ------ | ------       |
Commit Files          | 0.64   | 2.60   | 4x           |
Commit Images         | 1.53   | 24.70  | 16x          |
Diff Current Diff     | 0.25   | 1.09   | 4x           |
Diff Recent Diff      | 0.25   | 3.99   | 16x          |
Diff TagsjDiff        | 1.17   | 83.57  | 71x          |
Log (50)              | 0.01   | 0.38   | 31x          |
Log (All)             | 0.52   | 169.20 | 325x         |
Log (File)            | 0.60   | 82.84  | 138x         |
Update Pull of Commit | 0.90   | 2.82   | 3x           |
Blame Line            | 1.91   | 3.04   | 1x           |

[^2]: Unités en secondes


# Conclusion


### Conclusion

* Rapide
* Distribué
* Résolution de conflits simple
* Collaboration facilitée
* Travail hors-ligne


### Aller plus en profondeur

Quelques commandes pour aller plus loin :

* Annuler les modifications d'un fichier
```sh 
git checkout mon_fichier
```
. . .

* Changer la connexion de la branche à l'arbre
```sh 
git rebase
```
. . .

* Trouver un commit introduisant une erreur
```sh 
git bissect
```
. . .

* Modifier le commit précédent
```sh 
git commit --amend
```
. . .

* Appliquer un commit depuis une autre branche
```sh 
git cherry pick $mon_commit
```
. . .

* Annuler un commit en gardant son historique
```sh 
git revert $mon_commit
```

### Aller plus en profondeur (2)

* https://git-scm.com

* [Linus Torvalds sur git: https://www.youtube.com/watch?v=4XpnKHJAok8][Linus Torvalds sur git]

* [gitignore.io][gitignore]

* tig / gitg

[Linus Torvalds sur git]: https://www.youtube.com/watch?v=4XpnKHJAok8
[gitignore]: http://gitignore.io

