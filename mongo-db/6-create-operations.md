# Create Operations

## Document Creation
1. **insertOne({})**
```
    db
      .persons
      .insertOne(
          { name: 'Max', age: 30, hobbies: ['Sports', 'Cooking']}
          )
```

2. **insertMany([{}, {}])**
```
    db
      .persons.
      insertMany( [
          {name: 'Ana', age: 20, hobbies: ['Sports']}, 
          {name: 'Bob', age: 10}]
          )
```

3. **insert()** : it can take single document or array of document. 
> **note**: This was used earlier. The above two should be used now.


## Working with ordered Inserts
* **Definition**: Ordered insert means that if at any stage insert fails the remaining elements will not be inserted but previous to that record would have got inserted so they will not roll back  also.
    ```
    db
      .hobbies
      .insertMany
      ([
          {_id: "sports", name: "Sports"}, 
          {_id: "cooking", name: "Cooking"}, 
          {_id: "cards", name: "Cards"}
        ]) 
    ```
    * In above example the we inserted our own id rather than already using the auto generated Id. If you try to insert duplicate key then you will get an duplicate key error collection, **Once this fails then remaining will not be inserted**.
* To change this behavior, we can pass an second param to the insertMany method, this options is called **ordered option**, default is *true* or you can switch off this behavior. 
* **Config**: {options: false}
    ```
    db
      .hobbies
      .insertMany(
          [
              {_id: "sports", name: "Sports"}, 
              {_id: "cooking", name: "Cooking"}, 
              {_id: "cards", name: "Cards"}
          ], 
          {options: false})
    ```
    * In above query it will continue to insert even after failure and now you will get all failing records, this will not roll back

## Write Concern 
* we have client(shell or app) and mongo db server. If we want to do any write(insert, update) operation. Now when you write the data on server , there is a storage engine which will first put it in memory as for fast retrieval but at same time this data in memory will be scheduled to be put on disk
* **Write Concern Config**: {w: 1, j: undefined}
    * w: instances
    * j: journal(It is **TODO** file in storage engine;)
        * Writing into db files is more time consuming then first writing into the journal.
        * journal is there to say that if server goes down, once back the server can look into the journal and write things back to disk, if it was not already written
<br/>

* {w: 1, j: true}: this reports a success after it is both acknowledged and written to the journal.

* {w:1, wtimeout:200, j:true} - what time you give the server before you cancel this operation.

* **Example**
    ```
    db
      .persons
      .insertOne(
          {name: 'Christy', age: 40}, 
          {writeConcern: {w: 1}})
	
    db
      .persons
      .insertOne({
          name: 'Micheal', age: 40}, 
          {writeConcern: {w: 1, j: true}})
	
    db
      .persons
      .insertOne(
          {name: 'Aliyah', age: 22}, 
          {writeConcern: {w: 1, j: true, wtimeout: 200}})
    ```

> **NOTE**: If you dont care if data is actually inserted or not, then you can put w: 0 this can be done for logs. 

## Atomicity
* the operation may sometimes fails, while a document is writing , mongo ensures atomicity at the top document level. Either the whole doc is inserted or if some property failed to insert due to failure then the whole document will roll back. 

## importing existing set of documents 
1.  Using **mongoimport** tool
    1. Exit the shell
	2. Open CMD and goto such folder where you have the file. 
	3.  mongoimport <name_of_file.extension> -d <database_name> -c <collection_name> --jsonArray --drop
		* --jsonArray - will say the file is having array of data and not single data. 
		* --drop - says if the collection exit then drop and insert, if you dont pass this then the data will be appended. 

# LINKS
[insertOne()](https://docs.mongodb.com/manual/reference/method/db.collection.insertOne/)

[insertMany()](https://docs.mongodb.com/manual/reference/method/db.collection.insertMany/)

[Atomicity](https://docs.mongodb.com/manual/core/write-operations-atomicity/#atomicity)

[Write Concern](https://docs.mongodb.com/manual/reference/write-concern/)

[Using mongoimport](https://docs.mongodb.com/manual/reference/program/mongoimport/index.html)