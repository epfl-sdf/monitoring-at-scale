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

### Ajouter des modifications  a un commit

```sh
git add
```

* nouveau fichier
* ancien fichier
* detection des fichiers deplace

### commit

```sh
git commit
```

the art of crafting a commit

```
git reset
```

```
git add
```


# more branch !

### Creez une branch

Creons une nouvelle branche

```sh 
git checkout -b new_feature_for_cats
```


### Commit dans une branche

```sh 
git commit 
```

pic ==> live

```sh 
git checkout master
git merge new_feature_for_cats
```

### more conflict !

```sh 
git checkout new_feature_for_cats
```

```sh 
git merge
```
O NO

```sh 
git status
```

- conflict resolution

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

