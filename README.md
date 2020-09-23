# Comandos mongodb

**Uma particularidade do mongo**

caso um database ou um collection inexistente seja chamado o mesmo passa a existir;

exemplos:

**cria um database com nome school**

```sql=
> use school
```

**cria uma coleção com nome collections**

```sql=
> show collections
```

**exemplo de inserção de um registro**

```sql=
> db.students.insert({name:"Andreson", age:22})
WriteResult({ "nInserted" : 1 })
```

**exemplo de inserção de múltiplos registros**

Segue comando e exemplo de retorno:

```sql=
> db.students.insert([{name:"Jennifer",age:26},{name:"Lisa",age:3}]);
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 2,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
```

**listagem de registros sem formatação**

Segue comando e exemplo de retorno:

```sql=
> db.students.find();
{ "_id" : ObjectId("5f6abedcb6f5e07db292a898"), "name" : "Bob", "age" : 22 }
{ "_id" : ObjectId("5f6abf76b6f5e07db292a899"), "name" : "Jennifer", "age" : 26 }
{ "_id" : ObjectId("5f6abf76b6f5e07db292a89a"), "name" : "Lisa", "age" : 3 }
```

**listagem de registros com formatação**

Segue comando e exemplo de retorno:

```sql=
> db.students.find().pretty();
{
	"_id" : ObjectId("5f6abedcb6f5e07db292a898"),
	"name" : "Bob",
	"age" : 22
}
{
	"_id" : ObjectId("5f6abf76b6f5e07db292a899"),
	"name" : "Jennifer",
	"age" : 26
}
{
	"_id" : ObjectId("5f6ac2c62d0be4a56216d088"),
	"name" : "Lisa",
	"age" : 3
}
```

**filtrando uma busca**

Segue comando e exemplo de retorno:

```sql=
> db.students.find({name:"Bob"}).pretty()
{
	"_id" : ObjectId("5f6abedcb6f5e07db292a898"),
	"name" : "Bob",
	"age" : 22
}
```

**atualizando valores de forma geral**

O primeiro objeto é o filtro e o segundo são os valores atuais.
Essa forma de atualização não é muito recomendada pois é feita a atualização de todo o registro.

```sql=
> db.students.update({name:"Andreson"},{name:"Andreson Souza", age:34})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

**atualizando valores de um único registro**

Segue o mesmo padrão de filtro seguido de valores atuais.

```sql=
> db.students.updateOne({name:"Klay"},{$set:{age: 35}})
{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
```

**removendo um registro**

Para remover foi passado o id.

```sql=
> db.students.remove({_id: ObjectId("5f6abf76b6f5e07db292a89a")})
WriteResult({ "nRemoved" : 1 })
```