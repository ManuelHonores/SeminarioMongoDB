# Actividades Clase 1

### *2) Conectarse a MongoDB vía CLI*

```js
mongo
```

### *3) Crear una nueva base de datos llamada futbolfifa*

```js
use futbolfifa
```

### *4) Crear una nueva collection llamada players*

```js
db.createCollection("players")
```

### *5) Insertar 5 documentos en la collection players con datos básicos (nombre, apellido, posición, fecha de nacimiento, etc)*

```js
db.players.insert({"name": "Silvio", "lastname": "Romero", "position": "DC", "age": 32})

db.players.insert({"name": "Andres", "lastname": "Roa", "position": "DC", "age": 27})

db.players.insert({"name": "Fabricio", "lastname": "Bustos", "position": "CMD", "age": 23})

db.players.insert({"name": "Alan", "lastname": "Franco", "position": "CB", "age": 24})

db.players.insert({"name": "Sebastian", "lastname": "Sosa", "position": "GK", "age": 33})
```

### *6) Listar todos los documentos de la collection players*

```js
db.players.find()
```

### *7) Crear otras collections con documentos (ej. teams, games, etc)*

```js
db.createCollection("teams")

db.createCollection("leagues")
```