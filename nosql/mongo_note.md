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