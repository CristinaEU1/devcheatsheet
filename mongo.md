# Database CheatSheet

## MongoDB CheatSheet

### Connect & Backup
```bash
mongodb+srv://<username>:<password>@<cluster>/test

mongosh "mongodb+srv://<cluster>/myFirstDatabase" --apiVersion 1 --username mongo

mongosh "mongodb+srv://<username>:<password>@<cluster>/test" --apiVersion 1

mongosh "mongodb+srv://<username>:<password>@<cluster>/sample_airbnb" --apiVersion 1

mongodump --uri "mongodb+srv://<username>:<password>@<cluster>/sample_airbnb"

mongoexport --uri "mongodb+srv://<username>:<password>@<cluster>/sample_airbnb" --collection=listingsAndReviews --out=listingsAndReviews.json
```

### Query

![image](https://user-images.githubusercontent.com/31009750/173095270-26b46c3b-e59e-4d1f-bff2-1efdca6460ac.png)

```bash
show dbs
use <databasename>
show collections
db.<collectionName>.find({"<fieldName>":"<fieldValue>"})
db.<collectionName>.count()
db.<collectionName>.find({"<fieldName>":"<fieldValue>"}).pretty()
```

### Insert

```bash
db.zips.insert({
  city: 'HUEYTOWN',
  zip: '35023',
  loc: { y: 33.414625, x: 86.999607 },
  pop: 39677,
  state: 'AL'    
});
db.zips.insert({
  _id: Object("")
  city: 'HUEYTOWN',
  zip: '35023',
  loc: { y: 33.414625, x: 86.999607 },
  pop: 39677,
  state: 'AL'    
});
// insert multiple documents
db.zips.insert([{
  _id: Object("")
  city: 'HUEYTOWN',
  zip: '35023',
  loc: { y: 33.414625, x: 86.999607 },
  pop: 39677,
  state: 'AL'    
}, {...}]);
// ordered
db.pets.insert([{ "_id": 1, "pet": "cat" },
                { "_id": 1, "pet": "dog" },
                { "_id": 3, "pet": "fish" },
                { "_id": 4, "pet": "snake" }], { "ordered": false })
// => cat, finish, snake documents will be inserted
```

![image](https://user-images.githubusercontent.com/31009750/173192529-19a96900-b374-40a6-aff3-eb537295b57b.png)


### Update

> MQL : MongoDB Query Language

- https://www.mongodb.com/docs/manual/reference/operator/update/

![image](https://user-images.githubusercontent.com/31009750/173192380-ac155ee8-5eb1-4d05-bb22-30c8b257769c.png)


```bash
// we can use this operator 
db.zips.updateMany({"city":"HUDSON"},{"$set": {"area":9876.54}});
```

### Delete

- Delete Document - db.{collectionName}.deleteOne({})/.deleteMany({})
- Delete Collection - db.{collectionName}.drop();
- Delete Database - drop

## MQL Operators

![image](https://user-images.githubusercontent.com/31009750/173490903-e8f3d524-2275-4f79-8526-57209b47d1f3.png)

### Comparison Operators

![image](https://user-images.githubusercontent.com/31009750/173491313-0b3c678b-95b4-4daa-83db-5361152fd00c.png)

### Logic Operators

![image](https://user-images.githubusercontent.com/31009750/173492552-24b8823b-444c-4da9-9165-4e745ba0c487.png)

### Command Line Help
```bash
mongo --help
```

### Database Help
```bash
show dbs
```