<h1>DATABASE</h1>

`show dbs` //show dbs <br>
`use dbname` //if db !exist automatic create (after create collection) and use <br>
`db.dropDatabase()` //delete db <br>

<h1>COLLECTION</h1>

`show collections` //show collections

<h1>INSERT</h1>

<h2>insert one:</h2>

`db.colname.insertOne({name:'arfian'})`

<h2>insert many:</h2>

```
db.colname.insertMany([
    {name:'arfian'},
    {name:'adi'},
])
```

<h1>BASIC COMMANDS</h1>

<h2>limit:</h2>

`db.colname.find().limit(2)` //result only 2

<h2>sort:</h2>

`db.colname.find().short({name:-1})` //sort name <br />
1 = short <br />
-1 = revers

<h2>skip:</h2>

`db.colname.find().skip(1)` //result data skip 1

<h2>find:</h2>

`db.colname.find({name:'arfian'})` //result where name = 'arfian'

<h2>what you get field</h2>

`db.colname.find({name:'arfian'}, {name:1, _id:0})` //result only field name (1)

<h1>complex query</h1>

<h2>equals:</h2>

```
db.colname.find({name:{
    $eq:'arfian'
}}) //result doc where name == arfian
```

<h2>not equals:</h2>

```
db.colname.find({name:{
    $ne:'arfian'
}}) //result doc name != arfian
```

<h2>greater than:</h2>

```
db.colname.find({age:{
    $gt:13
}}) //result doc age > 13
```

<h2>greater than equals:</h2>

```
db.colname.find({age:{
    $gte:13
}}) //result doc age >= 13
```

<h2>less than:</h2>

```
db.colname.find({age:{
    $lt:13
}}) //result doc age < 13
```

<h2>less than equals:</h2>

```
db.colname.find({age:{
    $lte:13
}}) //result doc age <= 13
```

<h2>in:</h2>

```
db.colname.find({name:{
    $in:['arfian','adi']
}}) //result name arfian, adi in doc
```

<h2>exists field:</h2>

```
db.colname.find({age:{
    $exists:true
}}) //result where doc has age field
```

<h2>beetween (combine):</h2>

```
db.colname.find(
    {age:
        {$gt:12, $lt:30}
    }
) //12< result <30
```

<h2>logic:</h2>

```
db.colname.find({
    $and:[{name:'arfian'},{age:10}]
}) //result where name arfian and age 10

db.colname.find({
    $or:[{name:'arfian'},{age:12}]
}) //result where name arfian or age 12

db.colname.find({
    $not:{name:'arfian'}
}) //result where name doc not arfian
```

<h2>compare:</h2>

```
db.colname.find({$expr:{
    $gt:["field1","field2"]
}}) //result where doc field1 > field 2

db.colname.find({$expr:{
    $gt:["$field1","$field2"]
}}) //result where doc has field1 > field 2
```

<h2>query object:</h2>

```
{
    _id:ajasfyv,
    name:'ruly',
    address:{
        street:''jl raya
    }
}
```

`db.colname.find({'address.street':'jl raya'})`

<h2>count document:</h2>

`db.colname.countDocuments({age:10}) //count doc where age=10`

<h1>UPDATE</h1>

<h2>update one:</h2>

```
db.colname.updateOne({name:'arfian'}, {
    $set:{
        age:11,
        name:'dwi'
        }
) //update one where name = arfian
```

<h2>update many:</h2>

```
db.colname.updateOne({name:'arfian'}, {
    $set:{
        age:11,
        name:'dwi'
        }
) //update many where name = arfian
```

<h2>increment:</h2>

```
db.colname.updateOne(
    {_id:asdf},
    {
        $inc:{age:3}
    }
    ) //increment age 3
```

<h2>rename field:</h2>

```
db.colname.updateOne(
    {_id:asdf},
    {
        $rename:{age:'umur'}
    }
    ) //rename field age to umur
```

<h2>unset:</h2>

```
db.colname.updateOne(
    {_id:asdf},
    {
        $unset:{age:''}
    }
    ) //remove field age
```

<h2>push (array type):</h2>

```
db.colname.updateOne(
    {_id:asdf},
    {
        $push:{hobbies:'swimming'}
    }
    ) //push swimmming to array tipedata (hobbies field)
```

<h2>pull (array type):</h2>

```
db.colname.updateOne(
    {_id:asdf},
    {
        $pull:{hobbies:'swimming'}
    }
    ) //pull (remove) swimmming to array tipedata (hobbies field)
```

<h1>DELETE</h1>

<h2>delete one:</h2>

`db.colname.deleteOne({name:'arfian'})`

<h2>delete many:</h2>

`db.colname.deleteMany({age:10})`
