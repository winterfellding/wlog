### MongoDB是什么

    mongo db是一个document db，存储的是BSON(Binary JSON)数据，与传统的关系型数据库不同，
    它没有join，没有transaction。

### 启动mongo
    
    下完包后定义好存储数据位置，使用mongod打开数据库，默认会开在27017端口。

    mongo可以打开mongo shell对数据库进行shell操作。

### mongo shell
    
    * findOne   db.collections.findOne()
    * find      db.collections.find()
    * insert    db.collections.insert({json object})

    find & findOne的扩充用法
    * find({whereClauses}, {retrieve columns})
        e.g.    db.people.find({name: 'Jhon'}, {'age': true, '_id':false})
                可以这样处理让mongo shell不去取默认的ObjectId

    * whereClause
            $gt     greater than
            $lt     less than
            $gte    greater than or equals
            $lte    less than or equals
            $or     $or key to an array, makes the or clause
                    e.g. db.people.find({ $or: [{name: "jack"}, {age: {$exist: true}}]}), this will return the ones which name is jack or the ones has age property.
            $and    and is similar to the or notation.
            $all    所有元素都要在其中
            $in     只要有元素在其中

            dot notation
                    点写法可以读取属性的子属性。
    * cursor object
   			hasNext
   			next
   			limit
   			sort
   			skip	cursor的各种whereClause
   			
   	* counter
   		db.people.count({type: "exam"}) => like select count(id) from people.
   		
   	* update
   		db.people.update( { name : "Smith" }, { name : "Thompson", salary : 50000})
   			1st parameter is for retrieve, and 2nd parameter is for data updating.
   			this operation will discard all information before the updating.
   		db.people.update( { name : "Smith" }, { $set: { age : 31 }})   set
   												 $inc     increase
   												 $unset   remove property
   												 $push
   												 $pop
   												 $pushAll these three are all array value
   												 $pull
   												 $pullAll remove the value-same
   												 $addToSet
   	* upsert
   		if not exist, create a new document
   		db.people.update({ name : "Smith" }, { age : 23 }, { upsert : 1 })
   	* multi-update
   		db.people.update( { }, { title : "Dr" }, { multi : true })
   	* remove
   		db.people.remove( { whereClause } )
   	* drop
  
  	* getLastError (MongoDB V2.4 or later)
  	db.runCommand({ getLastError : 1 })
  		will show the last error.
  
### Mongo Java Classes

	// get a mongo db client
	MongoClient client = new MongoClient(new ServerAddress("localhost", 27017));
	// get the database
	DB db = client.getDb("course");
   	DBCollection people = db.getCollection("people");
   	DBObject doc = people.findOne();
   	DBCursor cursor = people.find();
   	while (cursor.hasNext()) {
   		 DBObject doc = cursor.next();
   		 System.out.println(doc);
   	}
   	
   	DBCursor cursor1 = people.find(new BasicDBObject("name", "Jhon"));
   	... // this will retrieve the name is Jhon's document data.
   	
   	// There's a builder interface for where clause building
   	QueryBuilder query = QueryBuilder.start().xxx;
   	query.get() will return an DBObject