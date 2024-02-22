# GIT RESET

> 📌 **Notas**
> - `HEAD~1` se refiere al commit anterior al commit actual.
> - Considere que los flags `--hard` y `--soft` se comportan distinto para cada uno de los siguientes casos.

----

# Reset Hard
> 📌 **Notas**
> <br>`--hard` en conjunto con `git reset` descarta de forma irreversible los commits, así como los cambios en el `working directory`. 

----

▶️ **Deshacer el último commit**
<br>Utilice `--hard` para descartar todos los cambios realizados en el `último commit` y eliminarlos del historial de Git.
```shell script
git reset --hard HEAD~1
```

----

▶️ **Reestablecer el repositorio a un commit específico**
<br>Utilice `--hard` para eliminar todos los `commits posteriores` y eliminarlos del historial de Git.
```shell script
git reset <commit-id> --hard
```

----

# Reset Soft
> 📌 **Notas**
> <br>`--soft` en conjunto con `git reset` descarta de forma irreversible los commits, pero los cambios del commit especificado son enviados al `staging area`.

▶️ **Deshacer el último commit**
<br>Utilice `--soft` para deshacer el `último commit` y conservar en el `staging area` los cambios realizados en este commit.
```shell script
git reset --soft HEAD~1
```

▶️ **Reestablecer el repositorio a un commit específico**
<br>Utilice `--soft` para deshacer todos los `commits posteriores` a este commit y conservarlos en el `staging area`.
```shell script
git reset <commit-id> --soft
```
