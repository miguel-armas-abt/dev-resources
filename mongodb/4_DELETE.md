## 4. Eliminaciones
> - Eliminar un documento
```javascript
db.users.remove(
	{"_id" : ObjectId("5fd8c23a5e34c1f1043c7366")}
);
```

> - Eliminar múltiples coincidencias
```javascript
db.users.remove(
	{university: "UNMSM"},
	{multi: true}
);
```