# Actividades Clase 2

### *1) Crear una nueva base de datos de un sistema de streaming de video (ej. Netflix, Flow, Amazon Prime) que permita almacenar movies*

```js
use netflix
```

### *2) Para cada movie, se debería guardar información como título (String), year (Number), rating (Number, entre 1.0 y 5.0), genre (String), description (String), actors (Array<String>), country (String), income (Number), duration (Number)*

```js
db.createCollection("movies")
```

### *3) Agregar películas usando insert(), insertOne() & insertMany()*

```js
db.movies.insert(
    {
        "titulo": "Back to the future",
        "year": 1985,
        "rating": 5.0,
        "genre": "Sci-Fi",
        "description": "Marty McFly, a 17-year-old high school student, is accidentally sent thirty years into the past in a time-traveling DeLorean invented by his close friend, the eccentric scientist Doc Brown.",
        "actors": ["Michael J. Fox", "Christopher Lloyd", "Lea Thompson"],
        "country": "USA",
        "income": 381100000,
        "duration": 116
    })

WriteResult({ "nInserted" : 1 })

db.movies.insertOne(
    {
        "titulo": "The Lord of the Rings",
        "year": 2001,
        "rating": 4.8,
        "genre": "Accion",
        "description": "A meek Hobbit from the Shire and eight companions set out on a journey to destroy the powerful One Ring and save Middle-earth from the Dark Lord Sauron.",
        "actors": ["Elijah Wood", "Ian McKellen", "Orlando Bloom"],
        "country": "USA",
        "income": 870000000,
        "duration": 228
    })


{
        "acknowledged" : true,
        "insertedId" : ObjectId("5f9330da66c104b67b22dbca")
}


db.movies.insertMany([
    {
        "titulo": "The Sixth Sense",
        "year": 1999,
        "rating": 4.5,
        "genre": "Drama",
        "description": "A boy who communicates with spirits seeks the help of a disheartened child psychologist.",
        "actors": ["Bruce Willis", "Haley Joel Osment", "Toni Collette"],
        "country": "USA",
        "income": 672800000,
        "duration": 110
    },
    {
        "titulo": "School of rock",
        "year": 2003,
        "rating": 4.3,
        "genre": "Comedy",
        "description": "After being kicked out of his rock band, Dewey Finn becomes a substitute teacher of an uptight elementary private school, only to try and turn his class into a rock band.",
        "actors": ["Jack Black", "Mike White", "Joan Cusack"],
        "country": "USA",
        "income": 131944672,
        "duration": 109
    }
])

{
        "acknowledged" : true,
        "insertedIds" : [
                ObjectId("5f9332b366c104b67b22dbcb"),
                ObjectId("5f9332b366c104b67b22dbcc")
        ]
}
```

### *4) Actualizar películas agregando el field highlighted=true a aquellas con rating > 4.5*

```js
db.movies.updateMany({rating: {$gt: 4.5}}, {$set: {highlighted: true}})

{ "acknowledged" : true, "matchedCount" : 2, "modifiedCount" : 2 }
```

### *5) Actualizar películas cambiando el genre “drama” por “bored”*

```js
db.movies.updateMany({genre: "Drama"} , {$set: {genre: "Bored"}})


{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
```

### *6) Borrar todas las películas que tengan más de 30 años*

```js
db.movies.deleteMany({year: {$lt: 2020-30}})


{ "acknowledged" : true, "deletedCount" : 1 }

```

### *7) Buscar todas las películas argentinas*

```js
db.movies.find({country: "Argentina"})

```

### *8) Buscar todas las películas de acción con un buen rating (ej. > 4.0) que hayan salido los últimos 2 años*

```js
db.movies.find(
    {
        genre: "Accion",
	rating: {$gt: 4.0},
	year: {$gt: 2020-2}
    })

```