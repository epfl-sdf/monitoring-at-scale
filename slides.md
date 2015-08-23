%Git, easy branching
%Malik Bougacha
%Marc Schaer

### git ?

\pause
\center
\includegraphics[width=10cm]{img/logo.png}

### Qu'est ce que git ?

Suivi de code 

\pause

* Distribuable
\pause

* branchable
\pause

* versionable
\pause

* rapide

### petite histoire


### pourquoi git

very easy branching
very easy collaboration
very fast even with thousand of branches
merging is clear
forge your commit

### configuration globale

```
git config
```

### Demarrer un repo

```sh
git init
```
### Crafter un commit

add 
vs
reset 

### Ajouter des modifications  a un commit

```sh
git add
```

* nouveau fichier
* ancien fichier
* detection des fichiers deplace

### Enlever des modifications a un future commit

```sh
git reset
```

### Regarder ce qui va etre commite

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

# more branch !

### Creez une branch

Creons une nouvelle branche

```sh 
git checkout -b new_feature_for_cats
```


### Commit dans une branche

```sh 
git commit -m 'message de commit dans la branche new_feature_for_cats'
```

### Merger la nouvelle branche dans master

```sh 
git checkout master
git merge new_feature_for_cats
```

\pause

```sh 
git checkout master
git merge new_feature_for_cats master
```

# more conflict !

### Creer un conflict

```sh 
git checkout new_feature_for_cats
```

creation du conflict

### diagnostique du conflict

```sh 
git status
```

### resolution des conflicts

```sh 
git add
git commit
```

# plus de gens, plus de repo


### ajoutez une remote

```sh 
git remote add origin  \
git@gitlab.com:gcmalloc/git-talk.git
```
origin: nom de la remote 
url: emplacement de la remote
\pause
(http ou ssh)

### prendre l'etat de la remote et le copier localement

```sh 
git fetch 
```

* -p pour enlever les branches de la remote n'existant plus

### merger l'etat d'une branche de la remote et la branche locale

```sh 
git merge origin/master
```

\pause 

equivalent de 

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

### Going to deeper

### Conclusion

