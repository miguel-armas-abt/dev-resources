Curso de GIT SCM y GitHub
======================

- [1. Inserciones](#1-inserciones)
- [2. Consultas](#2-consultas)
- [3. Actualizaciones](#3-actualizaciones)
- [4. Eliminaciones](#4-eliminaciones)
- [5. Cursores](#5-cursores)
- [6. Arreglos](#6-arreglos)
- [7. Agregaciones](#7-agregaciones)
- [8. Documentos embebidos](#8-documentos-embebidos)
- [9. Índices](#9-índices)
- [10. Relación uno a muchos](#10-relación-uno-a-muchos)
- [11. Relación entre colecciones](#11-relación-entre-colecciones)

> Algunos de los tipos de datos que tiene MongoDB:
```javascript
var myDocument = {
	stringValue = "Cadena",
	numberValue: 20,
	floatValue: 20.5,
	booleanValue: true,
	dateAndTimeValue: ISODate("2016-04-29T15:49:03.598Z")
	currentDateAndTimeValue: new Date(),
	dateValue: ISODate("2015-10-21"),
};
```

## 1. Inserciones
```javascript
use db_university;
show collections;

var userOne = {
	name: "Paolo Boada",
	dni: "12345678",
	age: 20,
	university: "UNMSM"
};

var userTwo = {
	nombre: "Miguel Armas",
	dni: "76517368",
	age: 21,
	universidad: "UNMSM"
};

db.users.insert([userOne, userTwo]);
db.users.find().pretty();
```

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

## 7. Agregaciones
> Obtener el promedio por estudiantes de universidad UNMSM y UNI
```javascript
db.users.aggregate(
	[
		{$match: {$or: [{university: "UNMSM"}, {age: "UNI"}]}},
		{$group: {_id: "$university", averageAge: {$avg: "$age"}}}
	]
);
```

> Obtener la suma de los salarios de las mujeres mayores de 20
```javascript
var employee = {
	name: 'Laura',
	salary: 4000,
	sexo: 'F',
	workDays: 7,
	area: 'Produccion',
	age: 25,
	paymentDate: ISODate('2020-04-12')
};

db.employees.insert(
	[employee]
);

db.employees.aggregate(
	[
		{$match: {gender: 'F', age:{$gte:20}}},
		{$group: {_id: "$area", total: {$sum: '$salary'}}}
	]
);

db.employees.aggregate(
	[{
		$group: 
		{
			_id:{month: {$month: 'paymentDate'}, year: {$year: '$paymentDate'}},
			monthlySalary: {$sum: {$multiply: ['$salary', '$workDays']}},
			averageDays: {$avg: '$workDays'},
			employeesNumber: {$sum:1}
		}
	}]
);
```

> Agrupar por universidad, sumar las coincidencias de +1 y obtener el promedio de edades
```javascript
db.users.aggregate(
	[
		{
			$group: {
				_id: "$university",
				"coincidences": {$sum: 1},
				"averageAges": {$avg: "$age"}
			}
		}
	]
);
```

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

## 10. Relación uno a muchos
var direccion01 = {
	distrito: "La Molina",
	urbanizacion: "Viña Alta",
	manzana: "Mz. L",
	lote: 9
};

var direccion02 = {
	distrito: "Santa Anita",
	urbanizacion: "Los Nogales",
	manzana: "Mz. J",
	lote: 14
};

db.usuarios.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$set: {direccion: [direccion01, direccion02]}}
);


// la estructura de la relacion 1...* dependerá del rendimiento la aplicación

## 11. Relación entre colecciones
// ****************************************** CREAR LA RELACION
// preparo el documento para tratarlo
db.usuarios.update(
	{"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")},
	{$unset: {matricula: 1}}
);

// recupero el documento que quiero
var user = db.usuarios.findOne({"_id" : ObjectId("5fdc2eb94cd03d82c1193cc8")});
var userId = user._id

// asigno manualmente en la matricula el id del usuario
var matricula = {
	user_id: userId,
	nro_matricula: 123456,
	anio: 2017,
	estado: "CREADO"
};

// inserto
db.matriculas.insert(matricula);



// ****************************************** CONSULTAR MEDIANTE LA RELACION

// obtengo el user_id a traves de la matricula
var matriculaFind = db.matriculas.findOne({"_id" : ObjectId("5fdcd0b516dfe5fcd0c9e947")});
var usuarioIdFind = matriculaFind.user_id;

// obtengo el usuario
var usuarioFound = db.usuarios.findOne({"_id": usuarioIdFind});