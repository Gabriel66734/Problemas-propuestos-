# Problemas-propuestos-
Problemas propuestos (1.1)

1.Insertar 2 documentos en la colección clientes con '_id' no repetidos


db.clientes.insertOne({
  _id: 1,
  nombre: "Lopez Marcos",
  domicilio: "Colon 111",
  provincia: "Cordoba"
})

db.clientes.insert({
  _id: 2,
  nombre: "Perez Ana",
  domicilio: "San Martin 250",
  provincia: "Buenos Aires"
})
**********************************************************************
RESULTADO:
{
  acknowledged: true,
  insertedId: 1
}
{
  acknowledged: true,
  insertedIds: {
    '0': 2
  }
}
***********************************************************************

2.Intentar insertar otro documento con clave repetida.
db.clientes.insert({
  _id: 1,
  nombre: "Garcia Juan",
  domicilio: "Belgrano 500",
  provincia: "Buenos Aires"
})
**********************************************************************
RESULTADO:
MongoBulkWriteError: E11000 duplicate key error collection: base1.clientes index: _id_ dup key: { _id: 1 }

*************************************************************************

3. Mostrar todos los documentos de la colección libros.

db.libros.find()
**********************************************************************
RESULTADO:{
  _id: ObjectId('6acd63c9868570519e22beeb'),
  codigo: 1,
  nombre: 'El aleph',
  autor: 'Borges',
  editoriales: [
    'Planeta',
    'Siglo XXI'
  ]
}
{
  _id: ObjectId('6acd6444868570519e22beec'),
  codigo: 2,
  nombre: 'Martin Fierro',
  autor: 'Jose Hernandez',
  editoriales: [
    'Planeta'
  ]
}

  _id: ObjectId('6acd64f1868570519e22beed'),
  codigo: 3,
  nombre: 'Aprenda PHP',
  autor: 'Mario Molina',
  editoriales: [
    'Planeta'
  ]
}
{
  _id: ObjectId('6acd64f1868570519e22beee'),
  codigo: 4,
  nombre: 'Java en 10 minutos',
  autor: 'Barros Sergio',
  editoriales: [
    'Planeta',
    'Siglo XXI'
  ]
}
***************************************************************************
---------------------------------------------------------------------------------------------------------------------------------


Problemas propuestos (1.2) 

1y2)1. Crear una base de datos llamada "blog". 
2. Agregar una colección llamada "posts" e insertar 1 documento con 
una estructura a su elección.
3. Mostrar todas las bases de datos actuales. 
4. Eliminar la colección "posts" 
5. Eliminar la base de datos "blog" y mostrar las bases de datos 
existentes. 

1.use blog
2.db.posts.insertOne({_id:1,nombre:"gaby",notas:"mi primer posts"})
**********************************************************************************************

3.show databases
admin    40.00 KiB
base1   144.00 KiB
blog     40.00 KiB
config  108.00 KiB
local    72.00 KiB

4.db.posts.drop()

5.show databases
admin    40.00 KiB
base1   144.00 KiB
blog     40.00 KiB
config  108.00 KiB
local    72.00 KiB
use blog
switched to db blog
db.dropDatabase()
{ ok: 1, dropped: 'blog' }
show databases
admin    40.00 KiB
base1   144.00 KiB
config  108.00 KiB
local    72.00 KiB

*******************************************************************************************************

Problemas propuestos (1.3) 

1. Crear la colección 'articulos' en la base de datos 'base1' (eliminar la 
colección previamente), cargar luego 6 documentos: 
2. Imprimir todos los documentos de la colección 'articulos'. 
3. Imprimir todos los documentos de la colección 'articulos' que no son 
impresoras. 
4. Imprimir todos los artículos que pertenecen al rubro de 'mouse'. 
5. Imprimir todos los artículos con un precio mayor o igual a 5000. 
6. Imprimir todas las impresoras que tienen un precio mayor o igual a 
3500. 
7. Imprimir todos los artículos cuyo stock se encuentra comprendido 
entre 0 y 4

Ejercicios resueltos:

2_db.articulos.find()

3_db.articulos.find({rubro:{$ne:"impresora"}})

4_db.articulos.find({rubro:{$eq:"mouse"}})

5_db.articulos.find({precio:{$gte:5000}})

6_db.articulos.find({rubro:"impresora",precio:{$gte:3500}})

7_db.articulos.find({stock:{$gte:0,$lte:4}})

*************************************************************************************************************

Problemas propuestos (1.4) 

1. Crear la colección 'articulos' en la base de datos 'base1' (eliminar la 
colección previamente), cargar luego 6 documentos: Utilizar la 
colección del problema propuesto anterior (1.3) 
2. Imprimir todos los documentos de la colección 'articulos'. 
3. Borrar los documentos de la colección 'articulos' cuyo rubro son 
impresoras, utilizar las dos sintaxis que permite MongoDB. 
4. Borrar todos los artículos que tienen un _id mayor o igual a 5. 

2_db.articulos.find()

3_db.articulos.deleteMany({rubro:"impresora"})
 _db.articulos.deleteMany({rubro:{$eq:"impresora"}})

4_db.articulos.deleteMany({_id:{$gte:5}})

************************************************************************************************************

Problemas propuestos (1.5) 
1. Crear la colección 'articulos' en la base de datos 'base1' (eliminar la 
colección previamente), cargar luego 6 documentos: Utilizar la colección del 
problema propuesto anterior (1.3)  
2. Imprimir todos los documentos de la colección 'articulos'. 
3. Modificar el precio del mouse 'LOGITECH M90'. 
4. Fijar el stock en 0 del artículo cuyo _id es 6. 
5. Agregar el campo proveedores con el array ['Martinez','Gutierrez'] para el 
artículo cuyo _id es 6. 
6. Eliminar el campo proveedores para el artículo cuyo _id es 6.


2_db.articulos.find()

3_db.articulos.updateMany({nombre:{$eq:"LOGITECH M90"}},{$set:{precio:150}})

4_db.articulos.updateOne({_id:{$eq:6}},{$set:{stock:0}})

5_db.articulos.updateOne({_id:{$eq:6}},{$push:{proveedores:"martinez,gutierrez"}})

6_db.articulos.updateOne({_id:{$eq:6}},{$unset:{proveedores:""}})

****************************************************************************************************************

Problemas propuestos (1.6) 

1. Crear la colección 'articulos' en la base de datos 'base1' (eliminar la 
colección previamente), cargar luego 6 documentos: Utilizar la colección del 
problema propuesto anterior (1.3)  
2. Imprimir todos los documentos de la colección 'articulos'. 
3. Fijar el stock en cero para todos los artículos del rubro monitor. 
4. Agregar un campo llamado 'pedir' con el valor true para todos los artículos 
que tienen el campo stock en 0. 
5. Eliminar el campo 'pedir' de todos los documentos

2_db.articulos.find()

3_db.articulos.updateMany({rubro:{$eq:"monitor"}},{$set:{stock:0}})

4_db.articulos.updateMany({stock:{$eq:0}},{$set:{pedir:true}})

5_db.articulos.updateMany({},{$unset:{pedir:""}})

***************************************************************************************************************
Problemas propuestos (1.7) 

1. Crear la colección 'medicamentos' en la base de datos 'base1' 
(eliminar la colección previamente), cargar luego 6 documentos:
 
2. Imprimir todos los documentos de la colección 'medicamentos'. 
3. Recupere los medicamentos cuyo laboratorio sea 'Roche' y cuyo 
precio sea menor a 5.
4. Recupere los medicamentos cuyo laboratorio sea 'Roche' o cuyo 
precio sea menor a 5. 
5. Muestre todos los medicamentos cuyo laboratorio NO sea "Bayer" 
6. Muestre todos los medicamentos cuyo laboratorio sea "Bayer" y cuya 
cantidad NO sea=100 
7. Elimine todos los documentos de la colección medicamentos cuyo 
laboratorio sea igual a "Bayer" y su precio sea mayor a 10 
8. Cambie la cantidad por 200, a todos los medicamentos de "Roche" 
cuyo precio sea mayor a 5 
9. Borre los medicamentos cuyo laboratorio sea "Bayer" o cuyo precio 
sea menor a 3

2_db.medicamentos.find()

3_db.medicamentos.find({
  $and: [
    { precio: { $lt: 5 } },
    { laboratorio: { $eq: "Roche" } }
  ]
})

4_db.medicamentos.find({$or:[{precio:{$lt:5}},{laboratorio:{$eq:"Roche"}}]})

5_db.medicamentos.find({laboratorio: { $ne: 'Bayer' }})

6_db.medicamentos.find({$and: [{ laboratorio: 'Bayer' },{ cantidad: { $ne: 100 } }]})

7_db.medicamentos.deleteMany({$and: [{ laboratorio: 'Bayer' },{ precio: { $gt: 10 } }]})

8_db.medicamentos.updateMany({$and:[{laboratorio:"roche"},{precio:{$gt:5}}]},{$set:{cantidad:200}})

9_db.medicamentos.deleteMany({$or:[{laboratorio:"Bayer"},{precio:{$lt:3}}]})

************************************************************************************************************************************************************
 Problemas propuestos (1.8)

2. Imprimir todos los documentos de la colección 'articulos', mostrar solo
los campos _id y nombre.
3. Imprimir todos los documentos de la colección 'articulos' que son
impresoras, mostrar solo los campos nombre y precio.
4. Imprimir todas las impresoras que tienen un precio mayor o igual a
3500. Solo mostrar los campos _id, nombre, precio y stock
5. Imprimir todos los documentos de la colección 'articulos' que son
monitor, mostrar solo los campos nombre y precio ordenados de
menor a mayor.

2_db.articulos.find({},{_id:1,nombre:1})

3_db.articulos.find({rubro:"impresora"},{nombre:1,precio:1})

4_db.articulos.find({rubro:"impresora",precio:{$gte:3500}},{_id:1,nombre:1,precio:1,stock:1})

5_db.articulos.find({rubro:"monitor"},{_id:0,nombre:1}).sort({precio:1})
