📋 **Tipos de dato en MongoDB**:
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

----

▶️ **Inserciones**
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