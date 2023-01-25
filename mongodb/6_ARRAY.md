## 6. Arreglos
> - Agregar elementos:
>
> Agregar un campo 'certificates' de tipo arreglo en un documento de la coleccion 'users'
```javascript
var certificates = ["Java 17", "Az900"];
var currentUser = db.users.findOne({"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")});
currentUser.certificates = certificates;
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	currentUser
);
```

> Agregar elementos a un campo de tipo arreglo con addToSet. No permite añadir valores repetidos
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$addToSet:{certificates: "Angular"}}
);
```

> Agregar elementos a un campo de tipo arreglo con push
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$push:{certificates: "Angular"}}
);
```

> Agregar varios elementos a un campo de tipo arreglo
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$addToSet:
		{certificates:
			{$each: ["Angular", "Spring Boot"]}
		}
	}
);
```

> Definir el índice sobre el campo de tipo arreglo
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$push:
		{certificates:
			{$each: 
				["SOA", "RxJava"],
				$position: 2
			}
		}
	}
);
```

> Ordenar el arreglo después de agregar elementos. Si se manda un arreglo vacío, solo ordena
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$push:
		{certificates:
			{$each: 
				["Microservicios", "Redux"],
				$sort: 1
			}
		}
	}
);
```

> - Remover elementos:
>
> Remover un elemento del array
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$pull: {certificates: "KanBan"}}
);
```

> Remover múltiples elementos del array
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$pullAll: 
		{certificates: ["KanBan", "SOA", "Redux"]}
	}
);

```

> - Consultar elementos:
>
> Consultar documentos que posean dentro de su array coincidencias con los elementos especificados ($in). Para la negación se utiliza $nin

```javascript
db.users.find(
	{certificates: 
		{$in: ["Spring Boot", "Angular"]}
	}
).pretty();

```