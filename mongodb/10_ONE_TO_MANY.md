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