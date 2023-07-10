# MongoDB

## Document Oriented Database
- menyimpan data bukan dalam bentuk table tapi dalam bentuk dokument, JSON atau XML, dan menyimpan relasinya dalam embedded object dalam dokument yang sama.
- semi structured data, dokumen pertama atau kedua tidak harus sama bentuk datanya.

## RDB VS MONGODB
table - collection
coloumn - field
row/record - document
join - embedded document / reference
sql - javascript
transaction - no transaction

## Database Methods
db.dropDatabase()
db.getName()
db.hostInfo()
db.version()
db.stats()

## Collection
- tempat menyimpan document
- max 16MB
- max nested document 100 level
db.getCollectionNames()
db.createCollection("name")
db.getCollection("name")
db.name 
db.getCollectionInfos()

## Collection Methods
db.collection.find()
db.collection.count()
db.collection.drops()
db.collection.totalSize()
db.collection.stats()

## Data Modelling
- wajib memakai primary key
- primary key wajib bernama _id
- primary key tidak bisa lebih dari 1 field

## BSON
- binary JSON
- binary-encoded serialization document seperti JSON
- tipe data: 
  - Double
  - String
  - Object
  - Array
  - Binary Data
  - ObjectId: 
      - random data yang unik, cepat di generate, dan terururt
      - konsisten, terdiri dari 12 byte, 4 byte timestampe, 5 byte random , 3 byte incrementing counter
      - digunakan untuk default _id (primary key) jika kita  tidak eksplisit menyebut _id document nya
  - Boolean
  - Date: 
      - 64 bit integer, representasi milisekon sejak unix epoch (1 Januari 1970)
      - representasi waktu 290 juta tahun sebelum dan sesudah unix epoch
      - ISO date, sama dengan Date di javascript
  - Null
  - Regular Expression
  - Javascript
  - Javascript with Scope
  - 32 Bit Integer
  - Timestamp
  - 64 Bit Integer
  - Decimal 128
  - Min Key
  - Max Key


## insert
- buat object json, lalu insert
- kalo tidak pakai _id, otomatis mongo generate objectId
- atau bisa eksplisit generate object id dengan 'new ObjectId()'


## Comparison
- $eq equal
- $gt / gte greater than equal
- $lt / lte lower thane equal
- $in inside array
- $nin not inside array
- $ne not equal
