# mongo-drills-thinkful


// Get all

db.getCollection('restaurants').find({})

// Limit and sort

db.getCollection('restaurants').find().sort({"name": 1}).limit(10)

// Get by _id

db.getCollection('restaurants').findOne({}, {"_id" : true})._id

// Get by value

db.getCollection('restaurants').find({"borough" : "Queens"})

// Count

db.getCollection('restaurants').count({})

// Count by nested value

db.getCollection('restaurants').find({"address.zipcode" : "11206"}).count()

// delete by id

var myId = db.getCollection('restaurants').findOne({}, {"id" : true})._id;
db.getCollection('restaurants').remove({'_id' : myId});

// update a single document

db.getCollection('restaurants').findOne({}, {"_id" : true})._id;
db.getCollection('restaurants').updateOne(
    {"_id" : "ObjectId('59074c7c057aaffaafb0da64')"
    },
    { $set : {"name" : "Bizz Bar Bang"}
    },
    { "multi" : false,
        "upsert" : false  query
    });

// update many documents

db.getCollection('restaurants').updateMany(
    {
        "address.zipcode" : "10035"
    },
    {
        $set : {"address.zipcode" : "10036"}
    },
    {
        "multi" : false,
        "upsert" : false
    });

