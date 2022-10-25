# SQLAssesment
first assemnt

mysql> create table Movies(
    -> Title varchar(100) NOT NULL DEFAULT '',
    -> Runtime int UNSIGNED NOT NULL DEFAULT 0,
    -> Genre varchar(30) NOT NULL DEFAULT '',
    -> IMDBScore DECIMAL(7,2) NOT NULL DEFAULT 99999.99,
    -> Rating char(6) NOT NULL DEFAULT '',
    -> PRIMARY KEY(Title)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Howard the duck','110','Sci-Fi','4.6','PG');
Query OK, 1 row affected (0.03 sec)
'''
+-----------------+---------+--------+-----------+--------+
| Title           | Runtime | Genre  | IMDBScore | Rating |
+-----------------+---------+--------+-----------+--------+
| Howard the duck |     110 | Sci-Fi |      4.60 | PG     |
+-----------------+---------+--------+-----------+--------+
'''

mysql> insert in movies(Title, Runtime, Genre, IMBDScore, rating)
    -> VALUES('Howard the duck','Sci-Fi','4.6','PG');
mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Howard the duck','110','Sci-Fi','4.6','PG');
Query OK, 1 row affected (0.03 sec)

mysql> select * from movies
    -> ;
    '''
+-----------------+---------+--------+-----------+--------+
| Title           | Runtime | Genre  | IMDBScore | Rating |
+-----------------+---------+--------+-----------+--------+
| Howard the duck |     110 | Sci-Fi |      4.60 | PG     |
+-----------------+---------+--------+-----------+--------+
'''
1 row in set (0.00 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Lavalantula','83','Horror','4.7','TV-14');
Query OK, 1 row affected (0.03 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Starship Troopers', '129','Sci-Fi','7.2','PG-13');
Query OK, 1 row affected (0.01 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Waltz With Bashir', '90','Documentary','8.0','R');
Query OK, 1 row affected (0.01 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Spaceballs', '96','Comedy','7.1','PG');
Query OK, 1 row affected (0.03 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Monster Inc.', '92','Animation','8.1','G');
Query OK, 1 row affected (0.01 sec)

mysql> select * from movies;

'''
+-------------------+---------+-------------+-----------+--------+
| Title             | Runtime | Genre       | IMDBScore | Rating |
+-------------------+---------+-------------+-----------+--------+
| Howard the duck   |     110 | Sci-Fi      |      4.60 | PG     |
| Lavalantula       |      83 | Horror      |      4.70 | TV-14  |
| Monster Inc.      |      92 | Animation   |      8.10 | G      |
| Spaceballs        |      96 | Comedy      |      7.10 | PG     |
| Starship Troopers |     129 | Sci-Fi      |      7.20 | PG-13  |
| Waltz With Bashir |      90 | Documentary |      8.00 | R      |
+-------------------+---------+-------------+-----------+--------+
'''
6 rows in set (0.00 sec)

Add your own movies

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Tenacious D', '120','Comedy','7.1','R');
Query OK, 1 row affected (0.01 sec)

mysql> insert into movies(Title, Runtime, Genre, IMDBScore, rating)
    -> VALUES('Thor Love & Thunder', '119','Action','9.0','PG-13');
Query OK, 1 row affected (0.00 sec)
'''
+---------------------+---------+-------------+-----------+--------+
| Title               | Runtime | Genre       | IMDBScore | Rating |
+---------------------+---------+-------------+-----------+--------+
| Howard the duck     |     110 | Sci-Fi      |      4.60 | PG     |
| Lavalantula         |      83 | Horror      |      4.70 | TV-14  |
| Monster Inc.        |      92 | Animation   |      8.10 | G      |
| Spaceballs          |      96 | Comedy      |      7.10 | PG     |
| Starship Troopers   |     129 | Sci-Fi      |      7.20 | PG-13  |
| Tenacious D         |     120 | Comedy      |      7.10 | R      |
| Thor Love & Thunder |     119 | Action      |      9.00 | PG-13  |
| Waltz With Bashir   |      90 | Documentary |      8.00 | R      |
+---------------------+---------+-------------+-----------+--------+
'''

find all Sci-Fi Genre
mysql> select * from movies WHERE IMDBscore < 6.6;
'''
+-----------------+---------+--------+-----------+--------+
| Title           | Runtime | Genre  | IMDBScore | Rating |
+-----------------+---------+--------+-----------+--------+
| Howard the duck |     110 | Sci-Fi |      4.60 | PG     |
| Lavalantula     |      83 | Horror |      4.70 | TV-14  |
+-----------------+---------+--------+-----------+--------+
'''


PG and less than 100 minutes
mysql> Select * from movies WHERE Rating = 'PG';
'''
+-----------------+---------+--------+-----------+--------+
| Title           | Runtime | Genre  | IMDBScore | Rating |
+-----------------+---------+--------+-----------+--------+
| Howard the duck |     110 | Sci-Fi |      4.60 | PG     |
| Spaceballs      |      96 | Comedy |      7.10 | PG     |
+-----------------+---------+--------+-----------+--------+
'''

Below a 7.5  grouped by genre
mysql> Select * from movies WHERE Rating = 'PG' AND Runtime <100;
'''
+------------+---------+--------+-----------+--------+
| Title      | Runtime | Genre  | IMDBScore | Rating |
+------------+---------+--------+-----------+--------+
| Spaceballs |      96 | Comedy |      7.10 | PG     |
+------------+---------+--------+-----------+--------+
'''

Change Starship troopers to rated R
mysql> UPDATE movies
    -> SET Rating = 'R'
    -> WHERE ID =3;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

 '''
+----+---------------------+---------+-------------+-----------+--------+
| ID | Title               | Runtime | Genre       | IMDBScore | Rating |
+----+---------------------+---------+-------------+-----------+--------+
|  1 | Howard the duck     |     110 | Sci-Fi      |      4.60 | PG     |
|  2 | Lavalantula         |      83 | Horror      |      4.70 | TV-14  |
|  3 | Starship Troopers   |     129 | Sci-Fi      |      7.20 | R      |
|  4 | Waltz With Bashir   |      90 | Documentary |      8.00 | R      |
|  5 | Waltz With Bashir   |      90 | Documentary |      8.00 | R      |
|  6 | Spaceballs          |      96 | Comedy      |      7.10 | PG     |
|  7 | Monster Inc.        |      92 | Animation   |      8.10 | G      |
|  8 | Monster Inc.        |      92 | Animation   |      8.10 | G      |
|  9 | Tenacious D         |     120 | Comedy      |      7.10 | R      |
| 10 | Thor Love & Thunder |     119 | Action      |      9.00 | PG-13  |
+----+---------------------+---------+-------------+-----------+--------+
'''


Average,min, and max IMDBscores
  
mysql> SELECT AVG(IMDBScore) from movies;
''
+----------------+
| AVG(IMDBScore) |
+----------------+
|       7.190000 |
+----------------+
''

mysql> select MIN(IMDBScore)
    -> from movies
    -> ;
    ''
+----------------+
| MIN(IMDBScore) |
+----------------+
|           4.60 |
+----------------+
''
mysql> SELECT MAX(IMDBScore) from movies;
'''
+----------------+
| MAX(IMDBScore) |
+----------------+
|           9.00 |
+----------------+
'''


using  A HAVING COUNT

mysql> SELECT *
    -> FROM movies
    -> HAVING COUNT(*)>1;
    '''
+------+-----------------+---------+--------+-----------+--------+
| ID   | Title           | Runtime | Genre  | IMDBScore | Rating |
+------+-----------------+---------+--------+-----------+--------+
|    1 | Howard the duck |     110 | Sci-Fi |      4.60 | PG     |
+------+-----------------+---------+--------+-----------+--------+
1 row in set (0.00 sec)
'''

Delete all rated R movies
DELETE FROM movies WHERE Rating = 'R';



Remove the table

Drop Movies;
 
 Remove the  database
 Drop SQLAssessment (Database name)









