# GIT BRANCH && GIT MERGE

- [1. Branch](#1-branch)
- [2. Merge](#2-merge)

# 1. Branch
> Una rama es una bifurcación del estado de nuestro código, en la cual podemos experimentar cambios sin alterar la 
> rama que tiene la versión estable de nuestro proyecto.

> `HEAD` es un puntero que apunta al último commit de la rama actual sobre la que estás trabajando. 

#### Mostrar ramas
- El flag `-a` muestra ramas locales y remotas
- El flag `-r` muestra ramas remotas
```shell script
git branch -a
git branch -r
```

#### Cambiar de rama
- El flag `-b` crea una nueva rama
```shell script
git checkout <branch-name>
git checkout -b <branch-name>
```

#### Eliminar rama local
```shell script
git branch -D <branch-name>
```

#### Eliminar rama remota
```shell script
git push origin --delete <branch-name>
```

#### Mostrar el historial de commits de las ramas
- El flag `--all` muestra tanto ramas locales y remotas
```shell script
git show-branch
git show-branch --all
```

#### Mostrar el historial de commits de las ramas en una UI
- El flag `--all` muestra tanto ramas locales y remotas
```shell script
gitk
gitk --all
```

# 2. Merge

> Un merge es la creación de un nuevo commit juntando una rama con otra. Para ello debemos situarnos `checkout` sobre la
> rama absorbedora, y a continuación absorber `merge` los commits de la otra rama

> Hay dos tipos de merge:
> - `fast forward`: Es un reemplazo automático de archivos y se suele apreciar cuando se trabaja con líneas de código diferentes
> - `manual merge`: Es un reemplazo manual y se suele apreciar cuando se trabaja sobre las mismas líneas de código

#### Crear nuevo commit con la combinación de dos ramas
```shell script
git merge <absorbed-branch>
```

#### Abortar el merge con conflictos
```shell script
git merge --abort
```
