# MongoDB

Db Drop
Insert/save
InsertMany
Find(search, show) 
	Search {key: "value"}
	Show {key: 0 or 1} 0 gone and 1 visit able
	
Update, Save update data and also insert if not found and use $ Set and unset
Remove
Limit 
skip is started form zero 0
Sort (key: 0 or -1) 0 ASC and a -1 DECS
ensureIndex({key:1}) for index keys
	Key: 1 ASC
	Key: -1 DECS
	Index save in ram if you search fields which joust only is index
	
Aggregate  is gtoupby with count
	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}])
	$min
	$max
	$push
	$first
	$last
	$avg
	$addToSet without repeat
	
Fun in Aggregate:
	1. $project
	2. Match
	3. Group
	4. Skip
	5. Limit
	6. Unwind

Sharing 
 
Backup 
	>mongodump  گرفتن
	<Mongorestore  برگرداندن 
	mongodump –host HOST_NAME –port PORT_NUMBER  for all db
	mongodump –dbpath DB_PATH –out BACKUP_DIRECTORY  for once db
	 mongodump –collection COLLECTION –db DB_NAME  for once data
	برای بازگرداندن اطلاعات پشتیبان از فرمان mongorestore MongoDB استفاده می شود.
	
Mongostat it is stat from db
Mongotop it is read and write db

 Embedded  {user : { address {cite ……}}}
Referenced  {user} {address,user_id}
	1:1 1:N N:N
 
DBRef
	"address": {
	   "$ref": "address_home",
	   "$id": ObjectId("534009e4d852427820000002"),
	   "$db": "tutorialspoint"
	}
Explian
Hint
findAndModify
	>db.products.findAndModify({ 
	   query:{_id:2,product_available:{$gt:0}}, 
	   update:{ 
	      $inc:{product_available:-1}, 
	      $push:{product_bought_by:{customer:"rob",date:"9-Jan-2014"}} 
	   }    
	})
	
ObjectId
	>ObjectId("5349b4ddd2781d08c09890f4").getTimestamp()
	
	
MapReduce
		>db.collection.mapReduce(
		   function() {emit(key,value);},  //map function
		   function(key,values) {return reduceFunction}, {   //reduce function
		      out: collection,
		      query: document,
		      sort: document,
		      limit: number
		   }
		)

Search in text body
	 >db.posts.find({$text:{$search:"tutorialspoint"}})
	
index
	>db.posts.find({$text:{$search:"tutorialspoint"}})
	>db.posts.dropIndex("post_text_text")
	
Regex
	>db.posts.find({post_text:{$regex:"tutorialspoint"}})
	>db.posts.find({post_text:/tutorialspoint/})
	>db.posts.find({post_text:/tutorialspoint/})
	
	برای ایجاد حساسیت جستجو، از پارامتر options$ با مقدار i$ استفاده می کنیم.
	دستور زیر به دنبال رشته هایی با کلمه “tutorialspoint”، صرف نظر از حروف کوچکت یا بزرگ است.
	>db.posts.find({post_text:{$regex:"tutorialspoint",$options:"$i"}})
	
	Capped محدود کننده
	Ø               
	
	isCapped()
