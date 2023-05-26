# GIT RESET

- [1. Reset Hard](#1-reset-hard)
- [2. Reset Soft](#2-reset-soft)

> - `HEAD~1` se refiere al commit anterior al commit actual
> - Considere que los flags `--hard` y `--soft` se comportan distinto para cada uno de los siguientes casos

# 1. Reset Hard
> - Cuando se utiliza el flag `--hard` en conjunto con `git reset`, se descartan de forma irreversible los commits, así 
> como los cambios en el `working directory` 


### Deshacer el último commit
El flag `--hard` descarta todos los cambios realizados en el **_último commit_** y los elimina del historial de Git
```shell script
git reset --hard HEAD~1
```

### Reestablecer el repositorio a un commit específico
El flag `--hard` elimina todos los cambios realizados **_después de ese commit_** y los elimina del historial de Git
```shell script
git reset <commit-id> --hard
```

# 2. Reset Soft
> - Cuando se utiliza el flag `--soft` en conjunto con `git reset`, se descartan de forma irreversible los commits, pero
> los cambios del commit especificado son enviados al `staging area`

### Deshacer el último commit
El flag `--soft` deshace el **_último commit_**, pero los cambios realizados en ese commit se mantienen en el 
`staging area` y en el índice de Git
```shell script
git reset --soft HEAD~1
```

### Reestablecer el repositorio a un commit específico
El flag `--soft` deshace todos los **_commits posteriores_** a ese commit, pero los cambios realizados en esos commits 
se mantienen en el `staging area` y en el índice de Git
```shell script
git reset <commit-id> --soft
```
