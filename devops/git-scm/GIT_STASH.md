# GIT STASH

> 📌 **Notas**
> - Git stash permite guardar temporalmente los cambios que has realizado en tu `working directory` sin realizar un commit. 
> - Es útil cuando necesitas cambiar de rama o actualizar el repositorio sin llevar contigo los cambios en progreso.
> - Si obtienes un `WIP` (work in progress) que fue stasheado desde otra rama, probablemente genere conflictos.

----

▶️ **Guardar / Mostrar / Eliminar stash**
```shell script
git stash -m "<description>"
git stash list
git stash drop <index>
```

----

▶️ **Recoger cambios del stash**
<br>Puedes especificar el índice del stash que deseas recuperar. Si no lo indicas, por defecto recuperará el último stash.
```shell script
git stash pop
git stash pop <index>
```

----

▶️ **Guardar los cambios del stash en una rama aparte**
```shell script
git stash branch <branch-name>
```

----