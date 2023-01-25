## 3. Actualizaciones

> 1. Recuperar el documento en una variable, modificarlo y volver a guardarlo
> consultar por expresión regular
```javascript
var currentUser = db.users.findOne({"_id" : ObjectId("5fd8c23a5e34c1f1043c7366")}); 

currentUser.name = "Miguel Rodrigo Armas Abt";
currentUser.age = 22;
currentUser.university = "UNMSM"
currentUser.dni = "76517369"

db.users.update(
	{"_id" : ObjectId("5fd8c23a5e34c1f1043c7366")},
	currentUser
);
```

> 2. Modificar directamente el documento con $set o $unset
> - Modificar una coincidencia
```javascript
db.users.update(
	
	{"_id" : ObjectId("5fd8c23a5e34c1f1043c7364")},
	{$set: 
		{
			name: "Edinson Paolo Boada Cajo",
			age: 19
		}
	}
);
```

> - Modificar múltiples coincidencias
```javascript
db.users.update(
	{university: "UNMSM"},
	{$set: {typeUniversity: "National"}},
	{multi: true}
);

db.users.update(
	{university: "UNMSM"},
	{$set: {careers: ["Ing. Sistemas", "Psicología", "Odontología"]}},
	{multi: true}
);
```

> - Eliminar un campo para múltiples coincidencias
```javascript
db.usuarios.update(
	{university: "UNMSM"},
	{$unset: {typeUniversity: 1}},
	{multi: true}
);
```