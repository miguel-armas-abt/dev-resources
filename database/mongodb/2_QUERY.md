## 2. Consultas

▶️ **Consultar por _id**
```javascript
var user = db.users.findOne(
	{"_id" : ObjectId("5fd8c1df5e34c1f1043c7363")}
);
```

----

▶️ **Consultar por campos**
```javascript
db.users.find({name: "Miguel Armas", age: 21});
```

----

▶️ **Consultar diferente de**
```javascript
db.users.find({age: {$ne: 21}});
```

----

▶️ **Consultar ocultando campos**
```javascript
db.users.find({}, {name:1, _id:0});
```

----

▶️ **Consultar elementos entre**
```javascript
db.users.find(
	{age:
		{$gte:18, $lte:21}
	},
	{name:1, _id:0}
).pretty();
```

----

▶️ **Consultar por expresión regular**
```javascript
db.users.find({name: /ro/});
db.users.find({name: /^ro/});
db.users.find({name: /ro$/});
```

----
