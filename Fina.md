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

postgres=# create database perpustakaan77
postgres-# ;
CREATE DATABASE
postgres=#
postgres=#
postgres=#
postgres=# \l
                                                                   List of databases
      Name      |  Owner   | Encoding | Locale Provider |        Collate         |         Ctype          | Locale | ICU Rules |   Access privileges
----------------+----------+----------+-----------------+------------------------+------------------------+--------+-----------+-----------------------
 latihan_db     | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan   | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan5  | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan55 | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan77 | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 perpustakaan8  | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 postgres       | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 sisfo          | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 sisfo24        | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           |
 template0      | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           | =c/postgres          +
                |          |          |                 |                        |                        |        |           | postgres=CTc/postgres
 template1      | postgres | UTF8     | libc            | English_Indonesia.1252 | English_Indonesia.1252 |        |           | =c/postgres          +
                |          |          |                 |                        |                        |        |           | postgres=CTc/postgres
(11 rows)


postgres=# create table perpustakaan77
postgres-# (
postgres(# id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT, tahun_terbit INT
postgres(# );
CREATE TABLE
postgres=# \d
             List of relations
 Schema |      Name      | Type  |  Owner
--------+----------------+-------+----------
 public | perpustakaan77 | table | postgres
 public | perpustakaan99 | table | postgres
 public | showroom_motor | table | postgres
(3 rows)


postgres=# \c perpustakaan77
You are now connected to database "perpustakaan77" as user "postgres".
perpustakaan77=# create table perpustakaan77
perpustakaan77-# (
perpustakaan77(# id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT, tahun_terbit INT
perpustakaan77(# );
CREATE TABLE
perpustakaan77=# \d
             List of relations
 Schema |      Name      | Type  |  Owner
--------+----------------+-------+----------
 public | perpustakaan77 | table | postgres
(1 row)


perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT, tahun_terbit INT, kategori_buku TEXT
perpustakaan77-# );
ERROR:  syntax error at or near "id_buku"
LINE 2: id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT,...
        ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT, tahun_terbit INT, kategori_buku TEXT
perpustakaan77(# );
ERROR:  syntax error at or near "INT"
LINE 3: id_buku INT PRIMARY KEY, judul_buku TEXT, penulis_buku TEXT,...
                ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# ('BK001', 'HARRY POTTER', 'J.K. ROWLING','1997'), ('BK002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'), ('BK003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960'), ('BK004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'), ('BK005', 'THE HUNGER GAMES', 'SUZANNE COLLINS', '2008')
perpustakaan77(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: ...', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'), ('BK005', ...
                                                             ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# ('BK001', 'HARRY POTTER', 'J.K. ROWLING','1997'), ('BK002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'), ('BK003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960'), ('BK004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813')
perpustakaan77(# );
ERROR:  column "id_buku" is of type integer but expression is of type record
LINE 3: ('BK001', 'HARRY POTTER', 'J.K. ROWLING','1997'), ('BK002', ...
        ^
HINT:  You will need to rewrite or cast the expression.
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# ('001', 'HARRY POTTER', 'J.K. ROWLING','1997'), ('002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'), ('003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960'), ('004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813')
perpustakaan77(# );
ERROR:  column "id_buku" is of type integer but expression is of type record
LINE 3: ('001', 'HARRY POTTER', 'J.K. ROWLING','1997'), ('002', 'THE...
        ^
HINT:  You will need to rewrite or cast the expression.
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '001', 'HARRY POTTER', 'J.K. ROWLING','1997','002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954', '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960', '004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'
perpustakaan77(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: '001', 'HARRY POTTER', 'J.K. ROWLING','1997','002', 'THE LOR...
                                                     ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '001', 'HARRY POTTER', 'J.K. ROWLING','1997', '002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954', '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960', '004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'
perpustakaan77(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: '001', 'HARRY POTTER', 'J.K. ROWLING','1997', '002', 'THE LO...
                                                      ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '001', 'HARRY POTTER', 'J.K. ROWLING','1997'
perpustakaan77(# );
INSERT 0 1
perpustakaan77=# select * from anggota
perpustakaan77-# ;
ERROR:  relation "anggota" does not exist
LINE 1: select * from anggota
                      ^
perpustakaan77=# select * from nama_buku
perpustakaan77-# ;
ERROR:  relation "nama_buku" does not exist
LINE 1: select * from nama_buku
                      ^
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |  judul_buku  | penulis_buku | tahun_terbit
---------+--------------+--------------+--------------
       1 | HARRY POTTER | J.K. ROWLING |         1997
(1 row)


perpustakaan77=# update perpustakaan77
perpustakaan77-# set judul_buku='THE LORD OF THE RINGS'
perpustakaan77-# where id_buku='002'
perpustakaan77-# ;
UPDATE 0
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954', '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960', '004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'
perpustakaan77(# );
ERROR:  INSERT has more expressions than target columns
LINE 3: ...THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954', '003', 'TO...
                                                             ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# 002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'
perpustakaan77'# );
perpustakaan77'# ;
perpustakaan77'# );
perpustakaan77'# )
perpustakaan77'# ;
perpustakaan77'# 002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954', '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960', '004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'
perpustakaan77(# );
ERROR:  syntax error at or near "', '"
LINE 3: 002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'
           ^
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'
perpustakaan77(# );
INSERT 0 1
perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# (
perpustakaan77(# '002', 'THE LORD OF THE RINGS', 'J.R.R. TOLKIEN', '1954'
perpustakaan77(# '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960'
perpustakaan77(# '004', 'PRIDE AND PREJUDICE', 'JANE AUSTIN', '1813'
perpustakaan77(# );
ERROR:  INSERT has more expressions than target columns
LINE 4: '003', 'TO KILL A MOCKINGBIRD', 'HARPER LEE', '1960'
               ^
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |      judul_buku       |  penulis_buku  | tahun_terbit
---------+-----------------------+----------------+--------------
       1 | HARRY POTTER          | J.K. ROWLING   |         1997
       2 | THE LORD OF THE RINGS | J.R.R. TOLKIEN |         1954
(2 rows)


perpustakaan77=# update perpustakaan77
perpustakaan77-# set judul_buku='THE LORD OF THE RINGS'
perpustakaan77-# where id_buku='2'
perpustakaan77-# ;
UPDATE 1
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |      judul_buku       |  penulis_buku  | tahun_terbit
---------+-----------------------+----------------+--------------
       1 | HARRY POTTER          | J.K. ROWLING   |         1997
       2 | THE LORD OF THE RINGS | J.R.R. TOLKIEN |         1954
(2 rows)


perpustakaan77=# delete from perpustakaan77 where judul_buku='J.K. ROWLING';
DELETE 0
perpustakaan77=# delete from perpustakaan77 where tahun_terbit='1954';
DELETE 1
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |  judul_buku  | penulis_buku | tahun_terbit
---------+--------------+--------------+--------------
       1 | HARRY POTTER | J.K. ROWLING |         1997
(1 row)


perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-# ('054', 'HIDUP ITU MENEYEBALKAN', 'SERLIA', '2004')
perpustakaan77-# ;
INSERT 0 1
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |       judul_buku       | penulis_buku | tahun_terbit
---------+------------------------+--------------+--------------
       1 | HARRY POTTER           | J.K. ROWLING |         1997
      54 | HIDUP ITU MENEYEBALKAN | SERLIA       |         2004
(2 rows)


perpustakaan77=# insert into perpustakaan77 values
perpustakaan77-#  ('006', 'JALANI HIDUP DENGAN APA ADANYA DENGAN PENUH SUKACITA', 'SERLIA TURU ALLO', '2005')
perpustakaan77-# ;
INSERT 0 1
perpustakaan77=# select * from perpustakaan77
perpustakaan77-# ;
 id_buku |                      judul_buku                      |   penulis_buku   | tahun_terbit
---------+------------------------------------------------------+------------------+--------------
       1 | HARRY POTTER                                         | J.K. ROWLING     |         1997
      54 | HIDUP ITU MENEYEBALKAN                               | SERLIA           |         2004
       6 | JALANI HIDUP DENGAN APA ADANYA DENGAN PENUH SUKACITA | SERLIA TURU ALLO |         2005
(3 rows)


perpustakaan77=# \i 'C:/path/ke/perintah.sql'
C:/path/ke/perintah.sql: No such file or directory
perpustakaan77=#
