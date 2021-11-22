# Elastic Search

- source: https://www.youtube.com/watch?v=621om_htH0Y&list=PL-CtdCApEFH_tVTwrxVt0K5LmtVT2u8fh&index=6
- database untuk melakukan search data. Banyak feature search data.

- punya fitur search untuk melakukan searching data yang complex.

- sebagai pendamping database utama. ambil data ke database, pencarian di elastic search

- kenapa nggak disimpen di ES aja tanpa db utama? soalnya kalok define table di es, strukturnya ga bisa diubah. Kalo diubah harus delete semua index nya.

## Arsitektur ES
- 1 aplikasi es = 1 node
- biasanya production punya lebih dari 1 node, minimal 3 dalam satu es cluster, untuk backup. harus ganjil
- tiap Node MASTERLESS. Bisa query ke node manapun. meskipun suatu node itu ngga ada datanya, otomatis datanya diakses dari node lain, selama dia ada di satu cluster.

## Index
===== FALSE ======

Database === Index

Table === Type

===== FALSE ======


- saat kita masukin data ke dalam index, data akan dimasukan ke Lucene Document. Document itu isinya attribute(kolom), dan valuenya. Seperti struktur table.

===== TRUE ======

Database === 

Table === Type

===== TRUE ======

- bestpractice penamaan table/index -> APPNAME_TABLENAME

## Sharding
- memotong index menjadi beberapa partisi
- secara default saat kita membuat index, akan dijadikan 5 partisi secara default. tapi yang kita liat itu seakan 1 saja. partisinya bisa di setting lagi
  - dengan dipotong, nanti akan lebih mudah didistribusikan ke node lain dalam node cluster.

## Replication
1. secara default es akan menduplikasi index yang kita buat. storage nya harus 2x lipat
2. di dalam nodes, akan tersebar partisi dan juga duplikasinya. didistribusikan merata, tidak ditempatkan di 1 node antara satu partisi dengan duplikasinya
3. dengan begitu saat satu node mati, partisi / duplikasinya pasti masih ada, jadi data tidak hilang, karena sudah terdistribusi. 
4. saat salah satu node mati, maka akan secara otomatis es akan menduplikasi lagi partisi/duplikasinya yang hilang.

## Document Routing
1. Document disimpan di shard mana? tidak boleh random!
2. routing harus konsisten di suatu partisi biar waktu di get tidak bingung.
3. routing memakai hashing(merubah sesuatu menjadi integer), 
  - shard = hash(id) % number_of_primary_shards
  - jadi data (dengan id yg beda2 itu) tersebar di partisi2 es
  - algoritma hash es -> murmurhash(id)
  - karena itu id dalam es tidak boleh dirubah

## Distributed Document
- insert, update delete,
- https://www.youtube.com/watch?v=w-kv7ur253g&list=PL-CtdCApEFH_tVTwrxVt0K5LmtVT2u8fh&index=9

## Immutable Document
- dokument disimpan secara immutable dalam disc.
- kenapa ga bisa dirubah ?
  - biar tidak perlu ada proses locking data, karena locking itu lambat.
  - jika data tdk pernah berubah, kita ngga khawatir terjadi proses bersamaan ketika akses atau ubah data. 
- terus gimana delete dan update?
  - delete: sebenernya datanya tetep ada. tapi es cuma bikin file .del, dan data yang di delete itu di masukin kesitu buat penanda, namanya soft delete.
  - update: sebenernya bukan update data beneran, tapi delete data yg lama, terus bikin document baru. 
  - terus datanya bengkak terus dong????
  - tenang aja, es ada scheduler untuk cleanup buat ngehapus permanen data yang ada di .del
- benefitnya, data kenceng banget.

## Distributed Search
- biasanya orang memakai es untuk searching
- saat search, semua partisi akan di search. setelah itu hasil searching akan digabungkan.
- 2 tahap: query dan fetch. https://www.youtube.com/watch?v=TZk6iVJwG0s&list=PL-CtdCApEFH_tVTwrxVt0K5LmtVT2u8fh&index=10
1. query:
  - beban kerja searching akan di distribusikan ke node selain node yg di request. tiap partisi di search tapi secara pintar beban kerja node didistribusi merata
  - setelah data ketemu di suatu partisi, yang di return hanyalah id document dan score hasil searchingnya. di return ke node yang di request di awal. 
2. fetch:
  - data2 yang didapat di partisi2 node digabung, lalu dikembalikan ke node awal dan ke aplikasi
- Deep Pagination: Problem di ES
- by default data di limit 10000
- jika mau ambil semua data, pakai feature scroll jangan pakai search. 

# CRUD

## create table
- PUT _{INDEXNAME}

## index API _doc
### insert update 
- PUT index/_doc/id 
- update harus full payload biar data nggak ilang
### delete 
- DELETE index/_doc/id
## update API for partial update _update
- tidak disarankan, karena data jadi mutable
- POST index/_update/id
- object json di wrab dalam property "doc"

# Query
## Match Query
- https://www.elastic.co/guide/en/elasticsearch/reference/7.15/full-text-queries.html
### _search or index/_search

```json
"query": {
  "match": {
    "fieldObject.fieldProperty": "aaa"
  }
}
```

## Bool Query
- https://www.elastic.co/guide/en/elasticsearch/reference/7.15/query-dsl-bool-query.html

- must -> and
- should -> or
- must_not -> not

```json
"query": {
  "bool": {
    "must_not": {
      "match" : {
        "fieldName": "asdf"
      }
    }
  }
}
```

# Aggregation
## Bucketing
- group by
## Metric
- avg, min, max
## Pipeline

## source https://www.elastic.co/guide/en/elasticsearch/reference/7.15/search-aggregations.html










