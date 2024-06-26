## 9. Índices
> Notamos que el tiempo que tarda la búsqueda por _id en comparación con name es mucho menor debido a que el campo _id está indexado.

```javascript
db.users.find({_id: ObjectId("...")}).explain("executionStats").executionStats.executionTimeMillis;

db.users.find({name: "..."}).explain("executionStats").executionStats.executionTimeMillis;
```

> Los índices agilizan el proceso de búsqueda
```javascript
db.inventory.createIndex( {scores: 1} );	// indexar y ordenar ascendentemente
db.inventory.find( {scores: [5, 9]} );
```

> Por defecto los índices en MongoDB se almacenan en árboles B y admiten valores duplicados en las claves. Si deseamos que sea único hay que especificarlo
```javascript
db.persons.createIndex({name:1, 1}, unique:true)
```

> MongoDB automáticamente les asigna un nombre al índice, pero podemos customizarlo
```javascript
db.accounts.createIndex({name: 1}, "indexNamesDesc")
```

> TTL (time to live ): índices que “caducan” al cabo de un tiempo
```javascript
db.persons.createIndex({name: 1}, expireAfterSeconds : 7200})
```

> Partial: se crean exclusivamente sobre documentos con valores concretos en el campo (índice condicionado)
```javascript
db.persons.createIndex(
	{name: 1}, 
	partialFilterExpression: {age: {$gt : 300}}
);
```

> Sparse: sólo se crea el índice en documentos que contienen el campo
```javascript
db.persons.createIndex({name:1}, {sparse: true});
```

> El método explain () nos permite ver el plan llevado a cabo para una consulta
```javascript
db.persons.find().explain();
```

> Borrar los indices
```javascript
db.persons.dropIndexes();
```

> Obtener los indices
```javascript
db.persons.getIndexes();
```

// TIPOS DE INDICES
// 1. indices simples: ascendente/descendente en un único campo de un documento
db.records.createIndex({score:1 });
	// se utilza en:
	db.records.find({score:2});
	db.records.find({score: {$gt:10}});

// 2. indices sobre un campo embebido: ascendente/descendente en un único campo de un documento
db.records.createIndex({"location.state":1});
	// se utilza en:
	db.records.find({"location.state": "La Molina"});
	db.records.find({"location.state": "La Molina"}, {"location.state": "Vitarte"});

// 3. indices compuestos: definidos en múltiples campos	(limite 32)
db.products.createIndex({"item":1, "stock":1});
	// se utilza en:
	db.products.find({item: "banana"});
	db.products.find({item: "banana", stock: {$gt:5}});	// ordena primero por item y luego ordena por stock
	
// 4. indices multiclave: definidos en múltiples campos	(limite 32)	
// mongodb crea automaticamente indice multiclave si el campo indexado es un arreglo


	
// ÍNDICES DE TEXTO
//Los índices de texto pueden incluir cualquier campo cuyo valor sea una cadena o un arreglo de cadenas.

db.articulos.createIndex({comentarios: "text"});

db.articulos.createIndex(
	{
		asunto: ["text",""],
		comentarios: "text"
	}
);

// consultas
//$search busca texto (por default no sensitivo a mayúscula)
// $search: "-text" excluye los resultados con esa cadena
// para textos separados por espacios realiza una busqueda con OR para cada subcadena
db.articulos.find(
	$text:{$search: "texto"}
);

//busqueda de frases
db.articulos.find(
	$text: {$search: "\"texto de frase\""}
);




db.usuarios.createIndex(
	{certificados: ["Spring Boot", "Java 8"]}
);