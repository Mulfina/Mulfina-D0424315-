Server [localhost]:
Database [postgres]:
Port [5432]:
Username [postgres]:
Password for user postgres:
psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# create database kampus_unsulbar
postgres-# ;
ERROR:  database "kampus_unsulbar" already exists
postgres=# create database kampus_unsulbar1
postgres-# ;
CREATE DATABASE
postgres=#
postgres=#
postgres=#
postgres=# \l
                                                                    List of databases
       Name       |  Owner   | Encoding | Locale Provider |        Collate         |         Ctype          | Locale | ICU Rules |   Access privileges
------------------+----------+----------+-----------------+------------------------+------------------------+--------+-----------+-----------------------
 kampus_store     | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 kampus_unsulbar  | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 kampus_unsulbar1 | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 latihan_db       | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 mahasiswa        | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan     | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan5    | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan55   | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan77   | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan8    | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 postgres         | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 sisfo            | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 sisfo24          | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 template0        | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           | =c/postgres          +
                  |          |          |                 |                        |                        |        |           | postgres=CTc/postgres
 template1        | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           | =c/postgres          +
                  |          |          |                 |                        |                        |        |           | postgres=CTc/postgres
(15 rows)


postgres=# \c kampus_unsulbar1
You are now connected to database "kampus_unsulbar1" as user "postgres".
kampus_unsulbar1=# create table produk_retail
kampus_unsulbar1-# (
kampus_unsulbar1(# id_produk int primary key, nama_produk varchar(50), harga int, stok int
kampus_unsulbar1(# );
CREATE TABLE
kampus_unsulbar1=# \d
             List of relations
 Schema |     Name      | Type  |  Owner
--------+---------------+-------+----------
 public | produk_retail | table | postgres
(1 row)


kampus_unsulbar1=# create table kursus_pendidikan
kampus_unsulbar1-# (
kampus_unsulbar1(# id_kursus int primary key, nama_kursus varchar(50), biaya int, durasi varchar(20)
kampus_unsulbar1(# );
CREATE TABLE
kampus_unsulbar1=# \d
               List of relations
 Schema |       Name        | Type  |  Owner
--------+-------------------+-------+----------
 public | kursus_pendidikan | table | postgres
 public | produk_retail     | table | postgres
(2 rows)


kampus_unsulbar1=# create table mahasiswa
kampus_unsulbar1-# (
kampus_unsulbar1(# id_mahasiswa int primary key, nama varchar(50), email varchar(50), jenis_kelamin varchar(20)
kampus_unsulbar1(# );
CREATE TABLE
kampus_unsulbar1=# \d
               List of relations
 Schema |       Name        | Type  |  Owner
--------+-------------------+-------+----------
 public | kursus_pendidikan | table | postgres
 public | mahasiswa         | table | postgres
 public | produk_retail     | table | postgres
(3 rows)


kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# ('0001','buku_tulis','15000','100'), ('0002','pulpen','5000','50'), ('0003','tas_kuliah','250000','50')
kampus_unsulbar1(# ;
kampus_unsulbar1(# );
ERROR:  syntax error at or near ";"
LINE 4: ;
        ^
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# ('0001','buku_tulis','15000','100'), ('0002','pulpen','5000','50'), ('0003','tas_kuliah','250000','50')
kampus_unsulbar1(# );
ERROR:  column "id_produk" is of type integer but expression is of type record
LINE 3: ('0001','buku_tulis','15000','100'), ('0002','pulpen','5000'...
        ^
HINT:  You will need to rewrite or cast the expression.
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# '0001','buku_tulis','15000','100','0002','pulpen','5000','50','0003','tas_kuliah','250000','50'
kampus_unsulbar1(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: '0001','buku_tulis','15000','100','0002','pulpen','5000','50...
                                          ^
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# (1, 'buku_tulis', 15000, 100), (2, 'pulpen', 5000, 150),(3, 'tas_kuliah', 250000, 175)
kampus_unsulbar1(# );
ERROR:  column "id_produk" is of type integer but expression is of type record
LINE 3: (1, 'buku_tulis', 15000, 100), (2, 'pulpen', 5000, 150),(3, ...
        ^
HINT:  You will need to rewrite or cast the expression.
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'buku_tulis', 15000, 100, 2, 'pulpen', 5000, 150, (3, 'tas_kuliah', 250000, 175
kampus_unsulbar1(# );
kampus_unsulbar1(# ;
kampus_unsulbar1(#
kampus_unsulbar1(#
kampus_unsulbar1(#
kampus_unsulbar1(# );
ERROR:  syntax error at or near ";"
LINE 4: );
         ^
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'buku_tulis', 15000, 100, 2, 'pulpen', 5000, 150, 3, 'tas_kuliah', 250000, 175
kampus_unsulbar1(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: 1, 'buku_tulis', 15000, 100, 2, 'pulpen', 5000, 150, 3, 'tas...
                                     ^
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'buku_tulis', 15000, 100
kampus_unsulbar1(# 2, 'pulpen', 5000, 150
kampus_unsulbar1(# 3, 'tas_kuliah', 250000, 175
kampus_unsulbar1(# );
ERROR:  syntax error at or near "2"
LINE 4: 2, 'pulpen', 5000, 150
        ^
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'buku_tulis', 15000, 100
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 2, 'pulpen', 5000, 150
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# select *from produk_retail
kampus_unsulbar1-# ;
 id_produk | nama_produk | harga | stok
-----------+-------------+-------+------
         1 | buku_tulis  | 15000 |  100
         2 | pulpen      |  5000 |  150
(2 rows)


kampus_unsulbar1=# insert into produk_retail values
kampus_unsulbar1-# (
kampus_unsulbar1(# 3, 'tas_kuliah', 250000, 175
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# select *from produk_retail
kampus_unsulbar1-# ;
 id_produk | nama_produk | harga  | stok
-----------+-------------+--------+------
         1 | buku_tulis  |  15000 |  100
         2 | pulpen      |   5000 |  150
         3 | tas_kuliah  | 250000 |  175
(3 rows)


kampus_unsulbar1=# insert into kursus_pendidikan values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'kursus_menjahit', 500000, '2 bulan'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# insert into kursus_pendidikan values
kampus_unsulbar1-# (
kampus_unsulbar1(# 2, 'bahas_inggris', 750000, '3 bulan'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# insert into kursus_pendidikan values
kampus_unsulbar1-# (
kampus_unsulbar1(# 3, 'publik_speaking', 650000, '1 bulan'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# select *from kursus_pendidikan
kampus_unsulbar1-# ;
 id_kursus |   nama_kursus   | biaya  | durasi
-----------+-----------------+--------+---------
         1 | kursus_menjahit | 500000 | 2 bulan
         2 | bahas_inggris   | 750000 | 3 bulan
         3 | publik_speaking | 650000 | 1 bulan
(3 rows)


kampus_unsulbar1=# insert into mahasiswa values
kampus_unsulbar1-# (
kampus_unsulbar1(# 1, 'andi', 'andi@gmail.com', 'laki-laki'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# insert into mahasiswa values
kampus_unsulbar1-# (
kampus_unsulbar1(# 2, 'siti', 'siti@gmail.com', 'perempuan'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# insert into mahasiswa values
kampus_unsulbar1-# (
kampus_unsulbar1(# 3, 'dewi', 'dewi@gmail.com', 'perempuan'
kampus_unsulbar1(# );
INSERT 0 1
kampus_unsulbar1=# select *from mahasiswa
kampus_unsulbar1-# ;
 id_mahasiswa | nama |     email      | jenis_kelamin
--------------+------+----------------+---------------
            1 | andi | andi@gmail.com | laki-laki
            2 | siti | siti@gmail.com | perempuan
            3 | dewi | dewi@gmail.com | perempuan
(3 rows)


kampus_unsulbar1=# update produk_retail
kampus_unsulbar1-# set harga='5000'
kampus_unsulbar1-# where id_produk='2'
kampus_unsulbar1-# ;
UPDATE 1
kampus_unsulbar1=# select *from produk_retail
kampus_unsulbar1-# ;
 id_produk | nama_produk | harga  | stok
-----------+-------------+--------+------
         1 | buku_tulis  |  15000 |  100
         3 | tas_kuliah  | 250000 |  175
         2 | pulpen      |   5000 |  150
(3 rows)


kampus_unsulbar1=# update kursus_pendidikan
kampus_unsulbar1-# set biaya='750000'
kampus_unsulbar1-# where nama_kursus='bahasa_inggris'
kampus_unsulbar1-# ;
UPDATE 0
kampus_unsulbar1=# update kursus_pendidikan
kampus_unsulbar1-# set biaya='750000'
kampus_unsulbar1-# where id_kursus='2'
kampus_unsulbar1-# ;
UPDATE 1
kampus_unsulbar1=# select *from kursus_pendidikan
kampus_unsulbar1-# ;
 id_kursus |   nama_kursus   | biaya  | durasi
-----------+-----------------+--------+---------
         1 | kursus_menjahit | 500000 | 2 bulan
         3 | publik_speaking | 650000 | 1 bulan
         2 | bahas_inggris   | 750000 | 3 bulan
(3 rows)


kampus_unsulbar1=# update mahasiswa
kampus_unsulbar1-# set email='andi@gmail.com'
kampus_unsulbar1-# where id_mahasiswa='1'
kampus_unsulbar1-# ;
UPDATE 1
kampus_unsulbar1=# select *from mahasiswa
kampus_unsulbar1-# ;
 id_mahasiswa | nama |     email      | jenis_kelamin
--------------+------+----------------+---------------
            2 | siti | siti@gmail.com | perempuan
            3 | dewi | dewi@gmail.com | perempuan
            1 | andi | andi@gmail.com | laki-laki
(3 rows)


kampus_unsulbar1=# delete from produk_retail where id_produk='3';
DELETE 1
kampus_unsulbar1=# select *from produk_retail
kampus_unsulbar1-# ;
 id_produk | nama_produk | harga | stok
-----------+-------------+-------+------
         1 | buku_tulis  | 15000 |  100
         2 | pulpen      |  5000 |  150
(2 rows)


kampus_unsulbar1=# delete from kursus_pendidikan where id_kursus='1';
DELETE 1
kampus_unsulbar1=# select *from kursus_pendidikan
kampus_unsulbar1-# ;
 id_kursus |   nama_kursus   | biaya  | durasi
-----------+-----------------+--------+---------
         3 | publik_speaking | 650000 | 1 bulan
         2 | bahas_inggris   | 750000 | 3 bulan
(2 rows)


kampus_unsulbar1=# delete from mahasiswa where id_mahasiswa='2';
DELETE 1
kampus_unsulbar1=# select from mahasiswa
kampus_unsulbar1-# ;
--
(2 rows)


kampus_unsulbar1=# select *from mahasiswa
kampus_unsulbar1-# ;
 id_mahasiswa | nama |     email      | jenis_kelamin
--------------+------+----------------+---------------
            3 | dewi | dewi@gmail.com | perempuan
            1 | andi | andi@gmail.com | laki-laki
(2 rows)


kampus_unsulbar1=# \i 'C:/path/ke/perintah.sql'
C:/path/ke/perintah.sql: No such file or directory
kampus_unsulbar1=#
