# GIT COMMIT

### Regresar el estado de un archivo a un commit específico
```shell script
git checkout <commit-id> <filename.txt>
```

### Mostrar las diferencias entre dos commits
```shell script
git diff <commit-id1> <commit-id2>
```

### Mostrar información detallada de un commit
- Incluye autor, fecha, mensaje de confirmación y las diferencias de los archivos modificados
- Si no se indica el `commit-id` mostrará la información del último commit
```shell script
git show
git show <commit-id>
```

### Combinar cambios con el último commit
El flag `amend` se utiliza cuando se requiere modificar el último commit combinándolo con nuestros cambios más recientes
en lugar de crear un nuevo commit

Puede utilizar el flag `--no-edit` para conservar el mensaje del commit original
```shell script
git commit --amend
git commit --amend --no-edit
```
