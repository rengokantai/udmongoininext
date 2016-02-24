#### udmongoininext

using explain()
```
db.coll.find().explain()
```

compound key index and multi key index  
compound:
db.createIndex({"a":1,"b":1})
multiple:(for multi layer data)  
db.createIndex({"person.name":1})

text indexes
```
db.adminCommand({setParameter:"*",textSearchEnabled:true})
```
