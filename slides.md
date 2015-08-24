%Git, Easy Branching
%Malik Bougacha \& Marc Schaer
%25 août 2015

# Introduction

### git ? 
\pause

\center
\includegraphics[width=10cm]{img/logo.png}

### Qu'est ce que git ?

Système de gestion de contenu

\pause

* Gestion de version
\pause

* Distribué
\pause

* Création de branches
\pause

* Efficace

### Son histoire

Avril 2005 : créé par Linus Thorvald après une accusation de "Reverse Engineering" de Bitkeeper

* Réécriture en C
* Prendre CVS comme l'exemple à ne pas faire (WWCVSND: What would CVS never do ?)
* Imaginé pour un workflow distribué


### Pourquoi git ?

* Facile d'utilisation
\pause

* Création de branches simples et rapides
\pause

* Collaboration facilitée
\pause

* Efficaces même avec des miliers de branches
\pause

* Fusion de code facile et claire
\pause

* Elaboration d'un commit

### Configuration globale

* Travail en local...
\pause

* ... mais collaboration...
\pause

* ... signifie identification !
\pause

```
git config
```

* Nom d'utilisateur

* E-mail

### Démarrer un dépôt

Création d'un dépôt local :

```sh
git init
```
### Modeler un commit

add vs. reset

Ici faut remplir avec qqch (image ?)

### Gestion des modifications sur un commit

* Ajouter des modifications à un commit
```sh
git add
```
    * Nouveau fichier
    * Ancien fichier
    * Détection des fichiers déplacés

. . .

* Enlever des modifications d'un futur commit
```sh
git reset
```

### Gestion des modifications sur un commit (2)

* Regarder ce qui va etre "commité"
```sh
git diff --staged
```

. . .

* Finalement faire le commit
```sh
git commit -m 'ceci est un message de commit'
```

. . .

* Tout ceci en une seule ligne - rapide et efficace
```sh
git commit -am 'ceci est un message de commit'
```

# Plus de branches !

### Pourquoi ?

Objectifs :

* Séparer les branches de développement de la production
* Une branche = une feature
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

* Aller sur une branche
```sh 
git checkout new_feature_for_cats
```
. . .

* Création du conflit (Modification d'un fichier)

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

* Ajouter une branche distante
```sh 
git remote add origin  \
git@gitlab.com:gcmalloc/git-talk.git
```
    * origin: nom de la remote 
    * url: emplacement de la remote
\pause
(http ou ssh)

. . .


### Gestion d'une branche distante (2)
* Prendre l'état de la remote et le copier localement
```sh 
git fetch 
```
    * -p pour enlever les branches de la remote n'existant plus

* Fusionner l'état d'une branche de la remote et la branche locale
```sh 
git merge origin/master
```
    * Equivalent à
    ```sh 
    git pull origin master
    ```

# Comparaison des performances - svn vs git


### svn vs git[^1]

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

[^1]: Unités en secondes


# Conclusion


### Conclusion

* Rapide
* Distribué
* Résolution de conflits simple
* Collaboration facilitée
* Travail hors-ligne


### Aller plus en profondeur

* https://git-scm.com

* [Linus Thorvald sur git: https://www.youtube.com/watch?v=4XpnKHJAok8][Linus Thorvald sur git]

* [gitignore.io][gitignore]

[Linus Thorvald sur git]: https://www.youtube.com/watch?v=4XpnKHJAok8
[gitignore]: http://gitignore.io

