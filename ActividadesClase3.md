# Actividades Clase 3

### *1) Utilizar la misma base de datos de películas e insertar varias películas con distinto contenido*

```js
db.movies.insertMany([
    {
        "titulo": "Avengers: Infinity War",
        "year": 2018,
        "rating": 4.6,
        "genre": "Accion",
        "description": "The Avengers and their allies must be willing to sacrifice all in an attempt to defeat the powerful Thanos before his blitz of devastation and ruin puts an end to the universe.",
        "actors": ["Robert Downey Jr.", "Chris Hemsworth", "Mark Ruffalo"],
        "country": "USA",
        "income": 2048359754,
        "duration": 149
    },
    {
        "titulo": "Deadpool 2",
        "year": 2018,
        "rating": 4.0,
        "genre": "Comedy",
        "description": "Foul-mouthed mutant mercenary Wade Wilson (a.k.a. Deadpool), brings together a team of fellow mutant rogues to protect a young boy with supernatural abilities from the brutal, time-traveling cyborg Cable.",
        "actors": ["Ryan Reynolds", "Josh Brolin", "Morena Baccarin"],
        "country": "USA",
        "income": 784000000,
        "duration": 119
    },
    {
        "titulo": "El secreto de sus ojos",
        "year": 2009,
        "rating": 4.3,
        "genre": "Drama",
        "description": "A retired legal counselor writes a novel hoping to find closure for one of his past unresolved homicide cases and for his unreciprocated love with his superior - both of which still haunt him decades later.",
        "actors": ["Ricardo Darín", "Soledad Villamil", "Pablo Rago"],
        "country": "Argentina",
        "income": 56965279,
        "duration": 129
    }
])
```

### *2) Listar todas las películas del año 2018*

```js
db.movies.find({year: 2018})
```

### *3) Listar las 10 primeras películas de Hollywood*

```js
db.movies.find({country: "USA"}).limit(10).sort({rating: -1}) 

```

### *4) Listar las 5 películas más taquilleras*

```js
db.movies.find().limit(5).sort({income: -1})

```

### *5) Listar el 2do conjunto de 5 películas más taquilleras*

```js
db.movies.find().skip(5).limit(5).sort({income: -1})

```

### *6) Repetir query 3 y 4 pero retornando sólo el título y genre*

```js
db.movies.find({country: "USA"}, {titulo: 1, genre: 1, _id: 0}).limit(10).sort({rating: -1})

db.movies.find({}, {titulo: 1, genre: 1, _id: 0}).limit(5).sort({income: -1})

```

### *7) Mostrar los distintos países que existen en la base de datos*

```js
db.movies.distinct("country")

```