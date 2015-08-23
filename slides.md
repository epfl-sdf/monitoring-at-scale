%Git, easy branching
%Malik Bougacha
%Marc Schaer

### Qu'est ce que git ?

\pause
\center
\includegraphics[width=10cm]{img/logo.png}

* Distribuable
\pause
* branchable
\pause
* versionable

### petite histoire


### pourquoi git

very easy branching
very easy collaboration
very fast even with thousand of branches
merging is clear
forge your commit

### Local use

Global configuration

```
git config
```

Starting a repo

```sh
git init
```

```sh
git add
```


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


### more branch !

#### more branch !

Creons une nouvelle branche

```sh 
git checkout -b new_feature_for_cats
```


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

### more people, more fun, more repo !

```sh 
git fetch
```

```sh 
git pull
```

```sh 
git fetch 
git merge master origin/master
```

### Going to deeper

### Conclusion

