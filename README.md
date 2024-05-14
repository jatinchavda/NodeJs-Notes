# NodeJs-Notes

## Node Setup with Docker
- [Install Docker](https://docs.docker.com/desktop/install/windows-install/)
- [Release Versions](https://docs.docker.com/desktop/release-notes/)

## Install MongoDb in Windows
- [Docs](https://www.mongodb.com/docs/manual/introduction/)
- [Download MongoDb](https://www.mongodb.com/try/download/community)
- [MongoDb GUI](https://www.mongodb.com/try/download/compass) (Easily explore and manipulate your database with Compass, the GUI for MongoDB.)
- [Mongoose Example](https://blog.appsignal.com/2023/08/09/how-to-use-mongodb-and-mongoose-for-nodejs.html)
- MongoDb Methods
  - insertOne() - insert single record
  - insertMany() - insert multiple record
  - findOne() - get first  record of collection
  - find({_id: '1212'}, { projection: _id: 0, title: 1 }) - Get all records (if condition added then filter data | projection: only specific columns return; )
    - .sort({ name: 1 })  ( { name: 1 } // ascending { name: -1 } // descending )
    - .limit(5)
  - updateOne() - update record by condition
  - updateMany() - update multiple records by condition
  - deleteOne() - delete record by condition.
  - deleteMany() - delete all record by condition
  - db("mydb").collection("customers").drop(function(err, delOK) {}); // delete collecion
  - Join Query :
  ```
  db.db("mydb").collection('orders').aggregate([{
    $lookup: {
      from: 'products',
      localField: 'product_id',
      foreignField: '_id',
      as: 'orderdetails'
    }
  }
  ]).toArray(function(err, res) {
    if (err) throw err;
    console.log(JSON.stringify(res));
    db.close();
  });
  ```
