 # INSTALACIÓN POSTGRESQL
 - [Descargar](https://www.enterprisedb.com/download-postgresql-binaries) para `Win x86-64` y reservar los binarios.
 - **Ruta sugerida**: `C:\dev-environment\postgresql\postgresql-16.1`

 > Ingresar a los binarios e instalar (solicitará el ingreso de un nuevo password = `qwerty`):
 > ```shell
 > cd bin
 > initdb.exe -U postgres -A password -E utf8 -W -D C:\dev-environment\postgresql-16.1\data
 > ```

 > Inciar el servidor:
 > ```shell
 > pg_ctl -D ^"C^:^\dev^-environment^\postgresql^-16^.1^\logs^" -l output.log start
 > ```

**Parámetros de conexión**:

| Key      | Value       |
|----------|-------------|
| host     | `localhost` |
| port     | `5432`      |
| database | `postgres`  |
| username | `postgres`  |
| password | `qwerty`    |

> Detener el servidor:
> ```shell
> pg_ctl -D ^"C^:^\dev^-environment^\postgresql^-16^.1^\logs^" -l output.log stop
> ```
