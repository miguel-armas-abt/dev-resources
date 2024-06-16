## 8. Documentos embebidos

```javascript
var currentUser = {
	nombre: "Fabrizio Sanchez",
	dni: "76517368",
	edad: 24,
	universidad: "USIL"
};

var enrollment = {
	code: 123456,
	year: 2015,
	status: "CREATED"
}
```

> Forma 1
```javascript
currentUser.enrollment = enrollment;
db.users.insert(currentUser);
```

> Forma 2
```javascript
db.users.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$set: {enrollment: enrollment}}
);
```

> Consultar documento embebido
```javascript
db.users.find(
	{"enrollment.code": 123456}
);

db.users.find(
	{"enrollment.code": 123456},
	{_id:0, name:1, enrollment:1}
);
```

> Modificar documento embebido
```javascript
db.users.update(
	{"enrollment.code": 123456},
	{$set: {year: 2016}},
	{_id:0, name:1, enrollment:1}
);
```

> Eliminar documento embebido
```javascript
db.users.remove(
	{"enrollment.code": 123456}
);
```