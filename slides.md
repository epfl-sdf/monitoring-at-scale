%Git, easy branching
%Malik Bougacha
%Marc Schaer

# Introduction

### git ?  \pause
\center
\includegraphics[width=10cm]{img/logo.png}

### Qu'est ce que git ?

Système de gestion de code

\pause

* Gestion de version
\pause

* Distribué
\pause

* Création de branches
\pause

* Efficace

### Son histoire

* TODO : petite recherche rapide sur l'historique des systèmes de gestion de code

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

* Gestion facile des commits (=forge your commit ?)

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

### Ajouter des modifications à un commit

```sh
git add
```

* Nouveau fichier
* Ancien fichier
* Détection des fichiers déplacés

### Enlever des modifications d'un futur commit

```sh
git reset
```

### Regarder ce qui va etre "commité"

```sh
git diff --staged
```

### Finalement faire le commit

```sh
git commit -m 'ceci est un message de commit'
```

### Rapide et efficace

```sh
git commit -am 'ceci est un message de commit'
```

# Plus de branches !

### Créez une branche

Créons une nouvelle branche

```sh 
git branch new_feature_for_cats
```

### Changer de branche

```sh 
git checkout new_feature_for_cats
```

### Commit dans une branche

```sh 
git commit -m 'message de commit dans la branche new_feature_for_cats'
```

### Fusionner la nouvelle branche dans la branche master

```sh 
git checkout master
git merge new_feature_for_cats
```

\pause

```sh 
git checkout master
git merge new_feature_for_cats master
```

# Mais plus de conflits !

### Créer un conflit

```sh 
git checkout new_feature_for_cats
```

* Création du conflit

### Diagnostique du conflit

```sh 
git status
```

### Résolution des conflits

```sh 
git add
git commit
```

# Plus de personnes, plus de collaboration !


### Ajouter une branche remote

```sh 
git remote add origin  \
git@gitlab.com:gcmalloc/git-talk.git
```
* origin: nom de la remote 
* url: emplacement de la remote
\pause
(http ou ssh)

### Prendre l'état de la remote et le copier localement

```sh 
git fetch 
```

* -p pour enlever les branches de la remote n'existant plus

### Fusionner l'état d'une branche de la remote et la branche locale

```sh 
git merge origin/master
```

\pause 

Equivalent à

```sh 
git pull origin master
```

### Vitesse 

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

### Plus en profondeur

### Conclusion

* Des questions ?
\pause

* Un endroit de référence :

https://git-scm.com

