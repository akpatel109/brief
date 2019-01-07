# MongoDB_brief


-> Collections and Documents
-> Collections can be considered as Tables in RDBMS
-> Documents can be considered as rows in RDBMS
-> Joins are removed by embedded documents
-> Fast read operations even on lerger scale due oo BJSON(Binary JSON)

# md directoryname to change data storage location


syntaxes:
-> use databasename (switch to database, if it is not there it will create one)
-> db.createCollection(collectionname) (to create a collection in current database)
-> db.collectionname.drop()  (to drop a collection)
-> db.dropDatabase() (to drop current database)

-> db.collectionname.insert({document})  (document->{prod_name:"Bat",price:200,use:['play','hit someone']})
-> db.collectionname.insert([{document1},{document2}])
-> db.collectionname.insertOne() || db.collectionname.insertMany()
-> if collection is not there, it will create one.
-> '_id' column is created for every document which works as primary key here


-> db.collectionname.find({where statements},{columns to be selected}) to retrieve data from collection
  ex. db.product_catalog.find( { publisher: "Dreamtech" }, { prodname: 1, price: 1 } )     (in columns 1 means show that nd 0 means dont show)
-> db.collectionname.find({where clause}).pretty()    to show in pretty format

{
        prodid: 7000001,
        prodname: "iphone 7",
        manufacturer: "apple",
        categories: {main:"electronics",sub:"smartphones"},
        year_of_launch: 2017,
        price: 60000,
        colors: ["silver","black","gold","rosegold"]
}
-> db.product_catalog.find({ "categories.main":"electronics" })  for embedded documents
-> db.product_catalog.find({ colors: "black" },{ prodname: 1 })   for array elements
  -> { field_name: { $all: [ "value1",  "value2" ] }     to show those documents which consists atleast value1 and value2
  -> db.product_catalog.find({ colors : { $all : ["black", "silver"] } },{ _id: 0, prodname: 1 })
  -> db.product_catalog.find(
	{$and:[
			{ "categories.sub": "smartphones" },
			{ manufacturer: "apple" }
	      ]
	} 
)


  -> db.product_catalog.find(
	{ "categories.main":{$ne:"electronics"} }
	{ _id: 0, prodname: 1 }
)


