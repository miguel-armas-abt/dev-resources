Curso de GIT SCM y GitHub
======================

- [1. Línea de comandos](#1-línea-de-comandos)
- [2. Configuraciones de GIT SCM](#2-configuraciones-de-git-scm)
- [3. Working directory - Staging area - Repository](#3-working-directory-staging-area-repository)
- [4. Creación del repositorio](#4-creación-del-repositorio)
- [5. Diferencia entre archivos](#5-diferencia-entre-archivos)
- [6. Versiones](#6-versiones)
- [7. Ramas](#7-ramas)
- [8. Repositorio remoto y FORKS](#8-repositorios-remotos-y-forks)
- [9. Clave SSH](#9-clave-ssh)
- [10. Tags y versiones en GIT SCM y GitHub](#10-tags-y-versiones-en-git-scm-y-github)
- [11. Rebase](#11-rebase)
- [12. Git Stash](#12-git-stash)
- [13. Git Clean](#13-git-clean)
- [14. Git Cherry Pick](#14-git-cherry-pick)
- [15. Git Amend](#15-git-amend)
- [16. Git Reset y Reflog](#16-git-reset-y-reflog)
- [17. Git Grep y Log](#17-git-grep-y-log)
- [18. Comandos y recursos colaborativos](#18-comandos-y-recursos-colaborativos)

## 1. Línea de comandos
- `$ pwd` : Ir a la ruta del usuario.

> La raíz del disco se especifica con "/" y la ruta del usuario con "~".

- `ctrl + L` : Limpiar consola.

> - La estructura de archivos es diferente en Linux, Windows o Mac.
- En Windows no se consideran las mayúsculas al navegar entre carpetas, a diferencia de Linux o Mac.
- Por lo general será más cómodo tener nuestros proyectos en la ruta de usuario "~".

- `TAB` : Autocompleta el comando en consola.
- `$ cd <directory-name>/` : Entrar a la carpeta *directory-name*.
- `$ cd .` : Acceder a la misma carpeta.
- `$ cd ..` : Acceder a la carpeta anterior.
- `$ cd ~/.ssh/` : Acceder a la carpeta .ssh/ dentro de la ruta de usuario.
- `$ mkdir <directory-name>` : Crear la carpeta *directory-name*.
- `$ touch <filename.txt>` : Crear el archivo de texto *filename.txt*.
- `$ ls` : Listar los archivos dentro de la carpeta.
- `$ ls -al` : Listar los archivos ocultos y no ocultos dentro de la carpeta.
- `$ cat <filename.txt>` : Mostrar el contenido del archivo *filename.txt*.
- `$ history` : Mostrar el historial de comandos escrito hasta ahora.
- `$ !11` : Ejecutar el comando número 11 del historial de comandos.
- `$ rm <filename.txt>` : Eliminar el archivo *filename.txt*.

## 2. Configuraciones de GIT SCM
- `$ git config -l` : Mostrar las configuraciones de GIT.
- `$ git config --global user.email "<my-email>"` : Editar email.
- `git config --global http.sslVerify false` : Desactivar verificación SSL

## 3. Working directory - Staging area - Repository
> - **Working directory** : Carpeta de trabajo donde están los archivos sin rastrear (untracked).
- **Staging area** : Espacio en memoria ram donde se guaradan los cambios (tracked).
- **Repository** : carpeta /.git en el que están todos los cambios al final del proyecto.

## 4. Creación del repositorio
- `$ git init`
- `$ git status`
- `$ git add <filename.txt>` : Enviar el archivo *filename.txt* al staging area.
- `$ git add .` : Enviar todos los archivos al staging area.
- `$ git rm --cached <filename.txt>` : Retornar archivo*filename.txt* al working directory.
- `$ git commit -m "<my-message>"` : Enviar archivos del staging area al local repository.
- `$ git commit -am "<message>"` : Hacer commit a los archivos que se le hicieron `$ git add .` previamente.
- `$ git commit` : Realizar un commit con mensaje manual

> - Se abrirá el editor de texto VIM
- Para editar el mensaje de commit presionar `ESC` seguido de `i`
- Para guardar el commit presionar `ESC` seguido de `shift` + `z` + `z`

- `$ git clone <url-repository>` : Clonar repositorio manteniendo el nombre del directorio por defecto.
- `$ git clone <url-repository> <directory-name>` : Clonar repositorio y cambiar el nombre del directorio.
- `$ git clone -b <branch-name> <url-repository> <directory-name>` : Clonar repositorio, cambiar rama y nombre del directorio.
- `$ git log <filename.txt>` : Mostrar el historial de cambios del archivo *filename.txt*.
- `$ git pull` : Funciona como `$ git fetch` + `$ git merge`

## 5. Diferencia entre archivos
- `$ git show` : Mostrar cómo estuvo antes y cómo está ahora.
- `$ git diff <commit-id1> <commit-id2>` : Mostrar las diferencias entre un commit y otro.

## 6. Versiones
- `$ git reset <commit-id> --hard` : Deshacer git add .
- `$ git reset <commit-id> --soft` : Volver a la versión anterior, pero manteniendo el staging area.
- `$ git log --stat` : Ver los cambios específicos hechos en cada commit.
- `$ git checkout <commit-id> <filename.txt>` : Regresar el archivo al estado del commit.

## 7. Ramas
> Una rama o **branch** en inglés, es una bifurcación del estado de nuestro código, en la cual podremos experimentar cambios sin alterar la rama que tiene la versión estable de nuestro proyecto.

> La cabecera o **HEAD** representa la rama y el commit de esa rama donde estamos trabajando. Por defecto, esta cabecera aparecerá en el último commit de nuestra rama principal.

- `$ git show-branch`
- `$ git show-branch --all`
- `$ gitk` : Mostrar la historia de ramas en una plataforma visual.
- `$ git checkout <branch-name>` : Cambiar de rama.
- `$ git checkout -b <branch-name>` : Crear y cambiar a una nueva rama.
- `$ git branch -D <branch-name>` : Eliminar rama local.
- `$ git push origin --delete <branch-name>` : Eliminar rama remota.
- `$ git branch -r` : Mostrar ramas remotas.
- `$ git branch -a` : Mostrar todas las ramas (locales y remotas).

> Una fusión o **merge** es la creación de un nuevo commit juntando una rama con otra. Para ello basta con situarnos (checkout) sobre la rama absorbedora (main), y a continuación absorber (merge) los commits de la otra rama.

> Hay dos tipos de fusión, **fast forward** y **manual merge**. La primera es un reemplazo automático de archivos y se suele apreciar cuando se trabaja con líneas de código diferentes. La segunda es un reemplazo manual y se suele apreciar cuando se trabaja sobre las mismas líneas de código.

- `$ git merge <absorbed-branch>`: Crear nuevo commit con la combinación de dos ramas.

## 8. Repositorio remoto y FORKS
- `$ git remote add origin <remote-repository-url>`
- `$ git remote` : Verificar que la URL se haya guardado correctamente.
- `$ git remote -v` :Mostrar la url del repositorio remoto.

> **Fork** : Es la manera en que se genera **una copia** de un repositorio para hacerle pull request cuando no eres colaborador.

>Cuando trabajas en un proyecto que existe en diferentes repositorios remotos (normalmente a causa de un fork) es muy probable que desees poder trabajar con ambos repositorios, para ésto puedes crear un remoto adicional desde consola.

- `$ git remote add <origin-remote-name> <remote-repository-url>`
> Ejemplo:  $ git remote upstream https://github.com/freddier/hyperblog

> Al crear un remoto adicional podremos hacer pull desde el nuevo origen (en caso de tener permisos podremos hacer fetch y push).

- `$ git pull <origin-remote-name> <branch-name>`
> Ejemplo: $ git pull upstream master

> Este pull nos traerá los cambios del remoto, por lo que se estará al día en el proyecto. De este modo el flujo de trabajo cambia y en adelante se estará trabajando haciendo pull desde el upstream y push al origin para pasar a hacer pull request.
$ git pull upstream master
$ git push origin master

> Para traer la versión del repositorio remoto y hacer merge para crear un commit con los archivos de ambas partes podemos usar git fetch y git merge o solo el git pull con el flag --allow-unrelated-histories.

- `$ git pull origin <branch-name> --allow-unrelated-histories`
- `$ git push origin <branch-name>`

## 9. Clave SSH
> Algunas notas en el proceso de creación de clave SSH:
- Ubicarse en la ruta de usuario.
- Mantener el directorio por defecto.
- Una passhphrase es una contraseña con espacios (para más seguridad).

- `$ ssh-keygen -t rsa -b 5096 -C "<my-email>"`
- `$ eval $(ssh-agent -s)` : Verificar que el servidor de llaves esté corriendo.
- `$ ssh-add ~/.ssh/id_rsa` : Añadir clave privada al usuario del entorno local.

> **Observación**: Si tienes 3 laptops, tienes que tener 3 llaves (privada y pública) conectadas al repositorio remoto por cada computadora.

- `$ git remote set-url origin <url-ssh>` : Cambiar la url (de http hacia ssh) del repositorio asociado a origin.
- `$ git pull origin main` : Traer cambios de la rama main.

## 10. Tags y versiones en GIT SCM y GitHub
- `$ git log --all --graph` : Mostrar cómo se han ido fusionando las ramas.
- `$ git log --all --graph --decorate --oneline` : Mostrar cómo se han ido fusionando las ramas, pero más visual.
- `$ alias tree="git log --all --graph --decorate --oneline"` : Crear alias para los comandos.
- `$ git tag -a <version> -m "<message>" <commit-id>` : Crear tag o release.
> $ git tag -a v0.1 -m "Primera versión" 218d6fa

- `$ git tag` : Mostrar tags.
- `$ git show-ref --tags` : Mostrar detalle del tag por commit.
- `$ git status- ` : Mostrar si hay algo para enviar.
- `$ git push origin --tags` : Subir tags al repositorio remoto.
- `$ git tag -d <tag-name>` : Eliminar tag local.
- `$ git push origin :refs/tags/<tag-name>` : Eliminar tag remoto.

## 11. Rebase
> El comando rebase es una mala práctica, nunca se debe usar. Con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra.

- `$ git checkout <branch-from-rebase>` : Cambiar a la rama sobre la que queremos agregar los cambios confirmados.

- `$ git rebase <branch-to-rebase>` : Aplicar rebase para recoger los cambios de la rama que queremos.

## 12. Git Stash
- `$ git stash` : Guardar cambios en el temporal.
- `$ git stash list` : Mostrar lista de WIP (work in progress).

> **Observación** : Si obtienes los WIP que fueron stasheados en otra rama probablemente generen conflictos. Asegúrate de qué rama los obtienes.

- `$ git stash pop` : Recoger cambios del stash.
- `$ git stash branch <branch-name>` : Salvar los cambios del stash en una rama aparte.
- `$ git stash drop` : Eliminar el stash.

## 13. Git Clean
- `$ git clean --dry-run` : Mostrar los archivos que se borrarán, que no forman parte importante del proyecto.
- `$ git clean -f` : Borrar los archivos listados al ejecutar `$ git clean --dry-run`.

## 14. Git Cherry Pick
> cherry pick permite traer una confirmación (commit) de otra rama y modificar la historia de la rama actual.

- `$ git log --oneline` : Obtener el commit-id o hash.
- `$ git cherry-pick <commit-id>` : Obtener commit de otra rama.

## 15. Git Amend
> amend se utiliza cuando quiere modificarse el último commit más reciente y combinar los cambios en lugar de crear un nuevo commit.

- `$ git commit --amend`
- `$ git commit --amend --no-edit` : Amend para conservar el mensaje del commit original.

## 16. Git Reset y Reflog
- `$ git reflog` : Mostrar los HEAD del historial de cambios hasta ahora (copiamos el commit-id o hash).
- `$ git reset --hard <commit-id>` Retornar a la confirmación (commit) del hisotrial que indiquemos.

## 17. Git Grep y Log
- `$ git grep <ocurrencia>` : Buscar la ocurrencia en el repositorio.
- `$ git grep -n <ocurrencia>` : Indica el archivo y la linea donde se da la ocurrencia.
- `$ git grep -c <ocurrencia>` : Indica la cantidad de veces que se da la ocurrencia en un archivo.
- `$ git grep -c "<p>"` : Entre comillas para evitar error de sintaxis.
- `$ git log -S <ocurrencia-message>` : Buscar los commits por la ocurrencia de la palabra en los mensajes de confirmación.

## 18. Comandos y recursos colaborativos
- `git shortlog` : Ver cuántos commits a hecho los miembros del equipo.
- `git shortlog -sn` : Las personas que han hecho ciertos commits.
- `git shortlog -sn --all` : Todos los commits (también los borrados).
- `git shortlog -sn --all --no-merges` : Mostrar las estadísticas de los commits del repositorio donde estoy.
- `git config --global alias.stats “shortlog -sn --all --no-merges”` : Configura el comando `“shortlog -sn --all --no-merges”` en un alias en las configuraciones globales de git del ordenador.
- `git blame -c blogpost.html` : Mostrar quién ha hecho cambios en dicho archivo identado.
- `git blame --help` : Mostrar en el navegador el uso del comando.
- `git blame archivo -L 35, 60 -c`: Mostrar quién escribió el código con información de la línea 35 a la 60, EJ: git blame css/estilos.css -L 35, 60 -c
