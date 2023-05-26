# GIT STAGES

- [1. Enviar archivos al siguiente stage](#1-enviar-archivos-al-siguiente-stage)
- [2. Regresar archivos al stage anterior](#2-regresar-archivos-al-stage-anterior)
- [3. Operar sobre un repositorio remoto](#3-operar-sobre-un-repositorio-remoto)

| #   | Stage               | Descripción                                                           |
|-----|---------------------|-----------------------------------------------------------------------|
| 1   | `Working directory` | Carpeta de trabajo donde están los archivos sin rastrear (untracked)  |
| 2   | `Staging area`      | Espacio en memoria ram donde se guaradan los cambios (tracked)        |
| 3   | `Local repository`  | Carpeta /.git en el que están todos los cambios al final del proyecto |                                             |
| 4   | `Remote repository` | Repositorio remoto                                                    |                                             |

# 1. Enviar archivos al siguiente stage

### Enviar archivos al staging area
- Los archivos se envían desde el `working directory` hacia el `staging area`
- Puede indicar un archivo específico o agregar todos los archivos modificados utilizando `.`
```shell script
git add <filename.txt>
git add .
```

### Enviar archivos hacia el repositorio local
- Los archivos se envían desde el `staging area` hacia el `local repository`
- Con el flag `-am` puede realizar en un solo paso `add` y `commit` sobre los archivos anteriormente trackeados
- Si no ingresa un flag, tendrá que agregar el mensaje manualmente en el editor de texto VIM. 
  - Para editar el mensaje de commit presionar `ESC` seguido de `i`
  - Para guardar el commit presionar `ESC` seguido de `shift` + `z` + `z`
```shell script
git commit -m "<my-message>"
git commit -am "<my-message>"
git commit
```

### Enviar archivos al repositorio remoto
- Los archivos se envían desde el `local repository` hacia el `remote repository`
```shell script
git push -u origin <branch-name>
```

# 2. Regresar archivos al stage anterior

### Regresar archivos al working  directory
- Los archivos se regresan desde el `staging area` hacia el `working directory`
```shell script
git rm --cached <filename.txt>
```

# 3. Operar sobre un repositorio remoto

### Clonar un repositorio remoto
- Puede cambiar el nombre del directorio clonado y especificar la rama que desea clonar
```shell script
git clone <url-repository>
git clone <url-repository> <directory-name>
git clone -b <branch-name> <url-repository> <directory-name>
```

### Descargar los cambios del repositorio remoto
- El `git pull` funciona como un `git fetch` en combinación con `git merge`
- Puede especificar la rama de la que quiere obtener los cambios
```shell script
git pull
git pull origin <branch-name>
```









