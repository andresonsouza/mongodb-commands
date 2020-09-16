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

**pesquisa um item**

```sql=
> db.students.find()
```

**exemplo de inserção de um registro**

```sql=
> db.students.insert({name:"Andreson", age:22})
```
