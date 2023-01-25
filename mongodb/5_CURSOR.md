## 5. Cursores
> Un cursor almacena temporalmente un documento y gracias a ellos podemos realizar consultas sin tener que persistir valores.

```javascript
var cursor = db.users.find();	

// puedo usar el cursor una sola vez
cursor.forEach(function(currentUser){
	currentUser.status = "CREATED"; 
	db.users.save(currentUser);
});

cursor; // ya no puedo acceder al cursor
```

> Podemos realizar consultas con los cursores:
> - Consultar cantidad de documentos
```javascript
db.users.find().count();
```

> - Consultar documentos ordenados ascendentemente por edad
```javascript
db.users.find().sort({age:1});
```

> - Consultar documentos ordenados descendentemente por edad
```javascript
db.users.find().sort({age:-1});
```

> - Consultar tres documentos ordenados descendentemente por edad
```javascript
db.users.find().sort({age:-1}).limit(3);
```

> - Consultar un documento de los ordenados descendentemente por edad a excepción de los dos primeros.
```javascript
db.users.find().sort({edad:-1}).skip(2).limit(1);
```

> - Consultar la cantidad de documentos ordenados descendentemente por edad a excepción de los dos primeros.
```javascript
db.users.find().sort({edad:-1}).skip(2).size();
```
