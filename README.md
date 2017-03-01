# mongodb-query

### Database

#### Buat / memakai database

`use academic`

#### Menampilkan seluruh Database yang ada
`show dbs`

### Collection

#### Membuat _collection_ baru

`db.createCollection(nama, option)`

* nama = String : nama _collection_
* option (Optional) = Document

Contoh :
`db.createCollection("department")`

#### Menampilkan seluruh _collections_ yang ada di _database_
`show collections`

#### Menghapus _collection_
`db.NAMA_COLLECTON.drop()`

Contoh : `db.department.drop()`

#### Memasukan data pada _collection_
Kita bisa menggunakan method `insert()` atau `save()`

`db.NAMA_COLLECTON.insert(document)`

contoh : `db.department.insert({code: 'xxx', name:'computer engineer',major: 'computer science' })`

#### Menampilkan data pada _collection_

`db.NAMA_COLLECTON.find()`

supaya data lebih mudah dibaca, kita bisa tambahkan `.pretty()` (Opsional)

Contoh : `db.department.find().pretty()`

#### Menampilkan / mengambil satu data dari suatu _collection_
`db.NAMA_COLLECTON.findOne()`


#### Mengambil data dengan kondisi tertentu
Kita bisa mengambil data berdasarkan banyak hal, misal

`db.NAMA_COLLECTON.find({"name": "Diky Arga"})`

Where Clause

Operasi | Kode | Sintaks
--- | --- | ----
Less Than | $lt | `{<key>: {$lt: <value>}}`
Less Than Equal | $lte | `{<key>: {$lte: <value>}}`
Greater Than | $gt | `{<key>: {$gt: <value>}}`
Greater Than Equals | $gte | `{<key>: {$gte: <value>}}`
Not Equals | $ne | `{<key>: {$ne: <value>}}`

#### Mengurutkan data
`db.NAMA_COLLECTON.find().sort({KEY:1})`

Note : `1` berarti ascending, `-1` berarti descending

Contoh : `db.department.find().sort({"major": -1})`

### Relationship
Ada dua tipe model yang bisa digunakan, **Embeded** dan **Referenced**
Seperti halnya 1:1, 1:N, N:1 atau N:N


#### Embedded Relationship
Akan mencantumkan document yang berelasi lasung didalam collectionnya.

Oke, misal kita sudah punya data di department, seperti ini :
```
{
    "_id" : ObjectId("58b64fce1a46b7fcc20091e4"),
    "code" : "xxx",
    "name" : "computer engineering",
    "major" : "computer science"
}
```

lalu kita mau tambah _student_ dengan department nya Referenced dengan data di _collection_ department.

```
db.student.insert({
  name: 'Diky Arga',
  address: 'Semarang, Indonesia',
  department: ObjectId("58b64fce1a46b7fcc20091e4")
})```

### Hal menarik di MongoDB :

di MongoDB tidak ada yang namanya kolom, seperti bukan database, tapi lebih mirip JSON storage.

Object ID alaha type data di MongoDB yang isinya adalah document's ID
