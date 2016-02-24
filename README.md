#### udmongoininext

using explain()
```
db.coll.find().explain()
```

compound key index and multi key index  
compound:
db.coll.createIndex({"a":1,"b":1})
multiple:(for multi layer data)  
db.coll.createIndex({"person.name":1})

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


