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