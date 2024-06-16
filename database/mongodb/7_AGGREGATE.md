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