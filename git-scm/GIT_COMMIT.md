# GIT COMMIT

----

▶️ **Regresar el estado de un archivo a un commit específico**
```shell script
git checkout <commit-id> <filename.txt>
```

----

▶️ **Mostrar las diferencias entre dos commits**
```shell script
git diff <commit-id1> <commit-id2>
```

----

▶️ **Mostrar información de un commit**
- Incluye autor, fecha, mensaje de confirmación y las diferencias de los archivos modificados.
- Si no se indica el `commit-id`, se mostrará la información del último commit.
```shell script
git show
git show <commit-id>
```

----

▶️ **Enmendar commit**
- Utilice `amend` para modificar el último commit con nuestros cambios más recientes en lugar de crear un nuevo commit.
- Utilice `--no-edit` para conservar el mensaje del commit original.
```shell script
git commit --amend
git commit --amend --no-edit
```

----

▶️ **Mostrar el historial de commits**
- Utilice `--stat` para mostrar los archivos que fueron modificados en cada commit.
- Puede indicar un archivo específico.
```shell script
git log
git log --stat
git log <filename.txt>
```

----