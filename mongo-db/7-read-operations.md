# Read Operations

## Method, Filters and Operators
* **syntax**: db.collection.find({parameters_what_look_for:value})
* Ones with $ are built-in reserve words.

```
    db
      .collection
      .find( {age: {$gt:30} })
```

### Projection Operators 
* `db.collectionName.findOne()` : we can pass any filter and alway result the first matching one. 
* `db.collectionItem.find({paramName:"value_You_want_to_match"})` : find all matching value, by equality(which is def filter criteria). 
* `db.movies.find({runtime:{ $ne :60}}).pretty()` : $ne - Not equal
* `db.movies.find({runtime:{ $lt:60}}).pretty()` : 
    * `$lt` - less than, 
    * `$lte` - less than+equal, 
    * `$gt` - greater than, 
    * `$gte` - greater than equals to 

### Querying Embedded Fields