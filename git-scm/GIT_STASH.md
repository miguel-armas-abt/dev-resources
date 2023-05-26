# GIT STASH
Git stash permite guardar temporalmente los cambios que has realizado en tu working directory sin realizar un commit. 
Esto es útil cuando necesitas cambiar de rama o actualizar el repositorio sin llevar contigo los cambios en progreso.

> Si obtienes los WIP (work in progress) que fueron stasheados en otra rama probablemente generen conflictos, así que 
> asegúrate de tu rama actual y de qué rama provienen los stashes.

### Guardar stash
```shell script
git stash -m "<description>"
```

### Mostrar stashes 
```shell script
git stash list
```

### Recoger cambios del stash
Puedes especificar el índice del stash que deseas recuperar. Si no lo indicas, recuperará por defecto el último stash
```shell script
git stash pop
git stash pop stash@{<index>}
```

### Guardar los cambios del stash en una rama aparte
```shell script
git stash branch <branch-name>
```

### Eliminar el stash
```shell script
git stash drop
```
