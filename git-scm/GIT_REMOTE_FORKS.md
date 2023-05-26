# FORKS

# 1. Repositorio remoto
- `git remote` permite ver, agregar y eliminar conexiones a repositorios remotos
- `origin` es el nombre por defecto asignado al repositorio clonado o con el que estás trabajando

#### Mostrar los repositorios remotos
- El flag `-v` muestra la URL del repositorio remoto
```shell script
git remote
git remote -v
```

# 2. Forks
Un fork implica crear una **réplica de un repositorio** remoto con el objetivo de enviar un pull request cuando no eres 
un colaborador directo. 

Cuando realizas un fork, es recomendable establecer una conexión remota tanto con el repositorio original como con el 
repositorio copiado. Esto permite mantener una relación entre los dos repositorios y facilita la colaboración y la 
sincronización de cambios entre ellos.

#### Agregar un nuevo repositorio remoto
```shell script
git remote add <remote-repository-name> <remote-repository-url>`
```

#### Realizar pull desde un repositorio remoto
Puede agregar el flag `--allow-unrelated-histories` si los repositorios (el local y el remoto) no están relacionados
```shell script
git pull <remote-repository-name> <branch-name> --allow-unrelated-histories
```

#### ¿Cuál es el flujo de trabajo con un fork?
1. Realizar un fork del repositorio original (sobre el cual no somos colaboradores directos) en nuestra cuenta de GitHub
2. Clonar el repositorio forkeado (origin)
3. Agregar al repositorio original como un nuevo repositorio remoto
> Ejemplo: `git remote add original-repository https://github.com/freddier/hyperblog`
4. Realizar un merge del repositorio original con nuestro repositorio forkeado. Este merge actualizará nuestro fork y estará al día respecto al repositorio original
> Ejemplo: `git pull original-repository master --allow-unrelated-histories`
5. Efectuar cambios en nuestro fork y subirlos a nuestro repositorio forkeado (git push) 
6. Realizar un pull request desde nuestro repositorio forkeado hacia el repositorio original, idealmente desde la rama master del fork hacia la rama master del original
