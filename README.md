# Exercicios da Semana - resolução!

## Inserção de documentos

db.MoviesOn12.insert({"id": 1,
        "title": "10 Things I Hate About You",
        "year": "1999",
        "rated": "PG-13",
        "released": "31 Mar 1999",
        "runtime": "97 min",
        "genre": "Comedy, Drama, Romance",
        "director": "Gil Junger",
        "writer": "Karen McCullah, Kirsten Smith",
        "actors": "Heath Ledger, Julia Stiles, Joseph Gordon-Levitt, Larisa Oleynik",
        "plot": "A pretty, popular teenager can't go out on a date until her ill-tempered older sister does.",
        "language": "English, French",
        "country": "USA",
        "awards": "2 wins & 13 nominations."})

## Atualização de documentos

db.getCollection('MoviesOn12').update(
    { "title" : "Doctor Strange" },
    { $set:
        { 
            "genre": "Action, Sci-Fi"
        }
    }
);

## Exclusão de documentos

db.MoviesOn12.remove({ "year": "2009"})

## Consulta com projeção

db.getCollection('MoviesOn12').find({},{"title" : 1, "_id" : 0})

## Consulta utilizando combinação entre os seletores

db.getCollection('MoviesOn12').find({$or:[{"genre": /.*Action.*/},{"genre": /.*Comedy.*/}]})

## Consulta paginada e ordenada (utilizar skip, limit e sort)
db.getCollection('MoviesOn12').find({}).limit(3)
db.getCollection('MoviesOn12').find().sort({"director": 1})