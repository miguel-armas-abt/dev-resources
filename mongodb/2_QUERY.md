## 2. Consultas
> consultar por _id
```javascript
var user = db.users.findOne(
	{"_id" : ObjectId("5fd8c1df5e34c1f1043c7363")}
);
```

> consultar por nombre
```javascript
db.users.find({name: "Miguel Armas"});
```

> consultar por nombre y edad
```javascript
db.users.find({name: "Miguel Armas", age: 21});
```

> consultar diferente de
```javascript
db.users.find({age: {$ne: 21}});
```

> consultar ocultando campo name y _id
```javascript
db.users.find({}, {name:1, _id:0});
```

> consultar elementos entre
```javascript
db.users.find(
	{age:
		{$gte:18, $lte:21}
	},
	{name:1, _id:0}
).pretty();
```

> consultar por expresión regular
```javascript
db.users.find({name: /ro/});
db.users.find({name: /^ro/});
db.users.find({name: /ro$/});
```
