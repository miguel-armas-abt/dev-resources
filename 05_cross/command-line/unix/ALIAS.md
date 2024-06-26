▶️ **Crear / Listar / Eliminar alias**
```shell script
alias <alias-name>=<command>
alias
unalias <alias-name>
```
Ejemplos:
- `alias docker-ps-format=docker ps -a --format "table {{.ID}}\t{{.Names}}\t{{.Status}}"`
- `unalias docker-ps-format`