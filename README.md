#### udmongoininext

using explain()
```
db.coll.find().explain()
```

compound key index and multi key index  
compound:
```
db.coll.createIndex({"a":1,"b":1})
multiple:(for multi layer data)  
db.coll.createIndex({"person.name":1})
```

text indexes
```
db.adminCommand({setParameter:"*",textSearchEnabled:true})
db.coll.createIndex({"fieldname":"text"})
db.coll.runCommand({"text",{search:"keyword"})
```

geo  
Ex
```
db.geo.insert({"_id":"a","shape":{"type":"polygon","coord":[2,2]}}}
db.geo.createIndex({shape:"2dsphere"})
db.coll.find({"shape":{$geointersects:{$geometry:BOX}}},{_id:1})
```

2dindex
```
db.coll.insert({"name":"a","location":"hotel","loc":[10,20]})
db.coll.find({"loc":{$near:[10,10]}}).pretty()
```

hash
```
db.coll.createIndex({"fieldname":"hashed"})
```


unique
```
db.coll.createIndex({"person.name":1},{unique:true})
```
sparse
```
db.coll.createIndex({"person.name":1},{sparse:true})
```

TTL
```
db.coll.createIndex({"person.name":1},{"expireAfterSeconds":10})
```

other index meth
```
db.coll.getIndexes();
db.system.indexes.find()
db.coll.totalIndexSize()
```

capped
```
db.createCollection("a",{capped:true,size:1000,max:5})       //max indexed doc=5
db.c.isCapped()
```
convert:
```
db.runCommand({"convertToCapped":"a",size:100,"max":5})
```

aggre pipe
```
db.coll.aggregate({$match:{"f":"A"}})
```

project (rename field)
```
db.coll.aggregate({$project:{"newfield":"$oldfield"}},{$sort:{"newfield":1}})
```

group by number of id:(the output will be determined by $group)
```
db.coll.aggregate({$project:{"field":1}},{$group:{"_id":"field"},{$sort:{"_id":1}})
```

distinct,count,group
```
db.runCommand({"distinct":"collname","key":"finame"})
```

members state:
STARTUP STARTUP2 RECOVERING ARBITER DOWN UNKNOWN REMOVED ROLLBACK FATAL
