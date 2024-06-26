# GIT MERGE

> 📌 **Notas**
> - Un merge es la creación de un nuevo commit juntando una rama con otra.
> - Debemos situarnos `checkout` sobre la rama absorbedora, y a continuación absorber `merge` los commits de la otra rama.
>
> Hay dos tipos de merge:
> - **Fast forward**: Reemplazo automático de archivos. Se suele apreciar cuando se trabaja con líneas de código diferentes.
> - **Manual merge**: Reemplazo manual. Se suele apreciar cuando se trabaja sobre las mismas líneas de código.

----

▶️ **Merge**
<br>Crear nuevo commit tras la combinación de dos ramas
```shell script
git merge <absorbed-branch>
```

----

▶️ **Abortar merge con conflictos**
```shell script
git merge --abort
```

----

▶️ **Finalizar merge manual**
```shell script
git merge --continue
```

----
