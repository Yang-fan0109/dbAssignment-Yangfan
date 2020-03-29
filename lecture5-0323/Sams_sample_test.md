1. 数据库调用

   ```
   mysql> show databases;
   +--------------------+
   | Database           |
   +--------------------+
   | bllk               |
   | book               |
   | information_schema |
   | mydb               |
   | mysql              |
   | performance_schema |
   | sams_sample_yf     |
   | sys                |
   +--------------------+
   8 rows in set (0.01 sec)
   
   mysql> use sams_sample_yf;
   Database changed
   mysql> show tables;
   +--------------------------+
   | Tables_in_sams_sample_yf |
   +--------------------------+
   | customers                |
   | orderitems               |
   | orders                   |
   | products                 |
   | vendors                  |
   +--------------------------+
   5 rows in set (0.01 sec)
   ```

2. 第2课

```
mysql> select * from products;
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
| prod_id | vend_id | prod_name           | prod_price | prod_desc                                                             |
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
| BNBG01  | DLL01   | Fish bean bag toy   |       3.49 | Fish bean bag toy, complete with bean bag worms with which to feed it |
| BNBG02  | DLL01   | Bird bean bag toy   |       3.49 | Bird bean bag toy, eggs are not included                              |
| BNBG03  | DLL01   | Rabbit bean bag toy |       3.49 | Rabbit bean bag toy, comes with bean bag carrots                      |
| BR01    | BRS01   | 8 inch teddy bear   |       5.99 | 8 inch teddy bear, comes with cap and jacket                          |
| BR02    | BRS01   | 12 inch teddy bear  |       8.99 | 12 inch teddy bear, comes with cap and jacket                         |
| BR03    | BRS01   | 18 inch teddy bear  |      11.99 | 18 inch teddy bear, comes with cap and jacket                         |
| RGAN01  | DLL01   | Raggedy Ann         |       4.99 | 18 inch Raggedy Ann doll                                              |
| RYL01   | FNG01   | King doll           |       9.49 | 12 inch king doll with royal garments and crown                       |
| RYL02   | FNG01   | Queen doll          |       9.49 | 12 inch queen doll with royal garments and crown                      |
+---------+---------+---------------------+------------+-----------------------------------------------------------------------+
9 rows in set (0.00 sec)

mysql> select prod_name from products;
+---------------------+
| prod_name           |
+---------------------+
| Fish bean bag toy   |
| Bird bean bag toy   |
| Rabbit bean bag toy |
| 8 inch teddy bear   |
| 12 inch teddy bear  |
| 18 inch teddy bear  |
| Raggedy Ann         |
| King doll           |
| Queen doll          |
+---------------------+
9 rows in set (0.00 sec)

mysql> select prod_id,prod_name,prod_price from products;
+---------+---------------------+------------+
| prod_id | prod_name           | prod_price |
+---------+---------------------+------------+
| BNBG01  | Fish bean bag toy   |       3.49 |
| BNBG02  | Bird bean bag toy   |       3.49 |
| BNBG03  | Rabbit bean bag toy |       3.49 |
| BR01    | 8 inch teddy bear   |       5.99 |
| BR02    | 12 inch teddy bear  |       8.99 |
| BR03    | 18 inch teddy bear  |      11.99 |
| RGAN01  | Raggedy Ann         |       4.99 |
| RYL01   | King doll           |       9.49 |
| RYL02   | Queen doll          |       9.49 |
+---------+---------------------+------------+
9 rows in set (0.00 sec)

mysql> select vend_id from products;
+---------+
| vend_id |
+---------+
| BRS01   |
| BRS01   |
| BRS01   |
| DLL01   |
| DLL01   |
| DLL01   |
| DLL01   |
| FNG01   |
| FNG01   |
+---------+
9 rows in set (0.01 sec)

mysql> select distinct vend_id from products;
+---------+
| vend_id |
+---------+
| BRS01   |
| DLL01   |
| FNG01   |
+---------+
3 rows in set (0.00 sec)

mysql> select prod_name from products limit 5;
+---------------------+
| prod_name           |
+---------------------+
| Fish bean bag toy   |
| Bird bean bag toy   |
| Rabbit bean bag toy |
| 8 inch teddy bear   |
| 12 inch teddy bear  |
+---------------------+
5 rows in set (0.00 sec)

mysql> select prod_name from products limit 5 offset 5;
+--------------------+
| prod_name          |
+--------------------+
| 18 inch teddy bear |
| Raggedy Ann        |
| King doll          |
| Queen doll         |
+--------------------+
4 rows in set (0.00 sec)
```

3. 第3课

   ```
   mysql> select prod_name from products;
   +---------------------+
   | prod_name           |
   +---------------------+
   | Fish bean bag toy   |
   | Bird bean bag toy   |
   | Rabbit bean bag toy |
   | 8 inch teddy bear   |
   | 12 inch teddy bear  |
   | 18 inch teddy bear  |
   | Raggedy Ann         |
   | King doll           |
   | Queen doll          |
   +---------------------+
   9 rows in set (0.00 sec)
   
   mysql> select prod_name from products order by prod_name;
   +---------------------+
   | prod_name           |
   +---------------------+
   | 12 inch teddy bear  |
   | 18 inch teddy bear  |
   | 8 inch teddy bear   |
   | Bird bean bag toy   |
   | Fish bean bag toy   |
   | King doll           |
   | Queen doll          |
   | Rabbit bean bag toy |
   | Raggedy Ann         |
   +---------------------+
   9 rows in set (0.00 sec)
   
   mysql> select prod_id,prod_price,prod_name from products order by prod_price,prod_name;
   +---------+------------+---------------------+
   | prod_id | prod_price | prod_name           |
   +---------+------------+---------------------+
   | BNBG02  |       3.49 | Bird bean bag toy   |
   | BNBG01  |       3.49 | Fish bean bag toy   |
   | BNBG03  |       3.49 | Rabbit bean bag toy |
   | RGAN01  |       4.99 | Raggedy Ann         |
   | BR01    |       5.99 | 8 inch teddy bear   |
   | BR02    |       8.99 | 12 inch teddy bear  |
   | RYL01   |       9.49 | King doll           |
   | RYL02   |       9.49 | Queen doll          |
   | BR03    |      11.99 | 18 inch teddy bear  |
   +---------+------------+---------------------+
   9 rows in set (0.00 sec)
   
   mysql> select prod_id,prod_price,prod_name from products order by 2,3;
   +---------+------------+---------------------+
   | prod_id | prod_price | prod_name           |
   +---------+------------+---------------------+
   | BNBG02  |       3.49 | Bird bean bag toy   |
   | BNBG01  |       3.49 | Fish bean bag toy   |
   | BNBG03  |       3.49 | Rabbit bean bag toy |
   | RGAN01  |       4.99 | Raggedy Ann         |
   | BR01    |       5.99 | 8 inch teddy bear   |
   | BR02    |       8.99 | 12 inch teddy bear  |
   | RYL01   |       9.49 | King doll           |
   | RYL02   |       9.49 | Queen doll          |
   | BR03    |      11.99 | 18 inch teddy bear  |
   +---------+------------+---------------------+
   9 rows in set (0.00 sec)
   
   mysql> select prod_id,prod_price,prod_name from products order by prod_price desc;
   +---------+------------+---------------------+
   | prod_id | prod_price | prod_name           |
   +---------+------------+---------------------+
   | BR03    |      11.99 | 18 inch teddy bear  |
   | RYL01   |       9.49 | King doll           |
   | RYL02   |       9.49 | Queen doll          |
   | BR02    |       8.99 | 12 inch teddy bear  |
   | BR01    |       5.99 | 8 inch teddy bear   |
   | RGAN01  |       4.99 | Raggedy Ann         |
   | BNBG01  |       3.49 | Fish bean bag toy   |
   | BNBG02  |       3.49 | Bird bean bag toy   |
   | BNBG03  |       3.49 | Rabbit bean bag toy |
   +---------+------------+---------------------+
   9 rows in set (0.00 sec)
   
   mysql> select prod_id,prod_price,prod_name from products order by prod_price desc, prod_name;
   +---------+------------+---------------------+
   | prod_id | prod_price | prod_name           |
   +---------+------------+---------------------+
   | BR03    |      11.99 | 18 inch teddy bear  |
   | RYL01   |       9.49 | King doll           |
   | RYL02   |       9.49 | Queen doll          |
   | BR02    |       8.99 | 12 inch teddy bear  |
   | BR01    |       5.99 | 8 inch teddy bear   |
   | RGAN01  |       4.99 | Raggedy Ann         |
   | BNBG02  |       3.49 | Bird bean bag toy   |
   | BNBG01  |       3.49 | Fish bean bag toy   |
   | BNBG03  |       3.49 | Rabbit bean bag toy |
   +---------+------------+---------------------+
   9 rows in set (0.00 sec)
   ```

4. 第4课 过滤数据

   ```
   mysql> select prod_name,prod_price from products where prod_price = 3.49;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | Fish bean bag toy   |       3.49 |
   | Bird bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   +---------------------+------------+
   3 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where prod_price < 10;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | Fish bean bag toy   |       3.49 |
   | Bird bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | 8 inch teddy bear   |       5.99 |
   | 12 inch teddy bear  |       8.99 |
   | Raggedy Ann         |       4.99 |
   | King doll           |       9.49 |
   | Queen doll          |       9.49 |
   +---------------------+------------+
   8 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where prod_price <= 10;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | Fish bean bag toy   |       3.49 |
   | Bird bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | 8 inch teddy bear   |       5.99 |
   | 12 inch teddy bear  |       8.99 |
   | Raggedy Ann         |       4.99 |
   | King doll           |       9.49 |
   | Queen doll          |       9.49 |
   +---------------------+------------+
   8 rows in set (0.00 sec)
   
   mysql> select vend_id,prod_name from prodects where vend_id<>'DLL01';
   ERROR 1146 (42S02): Table 'sams_sample_yf.prodects' doesn't exist
   mysql> select vend_id,prod_name from products where vend_id<>'DLL01';
   +---------+--------------------+
   | vend_id | prod_name          |
   +---------+--------------------+
   | BRS01   | 8 inch teddy bear  |
   | BRS01   | 12 inch teddy bear |
   | BRS01   | 18 inch teddy bear |
   | FNG01   | King doll          |
   | FNG01   | Queen doll         |
   +---------+--------------------+
   5 rows in set (0.00 sec)
   
   mysql> select vend_id,prod_name from products where vend_id!='DLL01';
   +---------+--------------------+
   | vend_id | prod_name          |
   +---------+--------------------+
   | BRS01   | 8 inch teddy bear  |
   | BRS01   | 12 inch teddy bear |
   | BRS01   | 18 inch teddy bear |
   | FNG01   | King doll          |
   | FNG01   | Queen doll         |
   +---------+--------------------+
   5 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where prod_price between 5 and 10;
   +--------------------+------------+
   | prod_name          | prod_price |
   +--------------------+------------+
   | 8 inch teddy bear  |       5.99 |
   | 12 inch teddy bear |       8.99 |
   | King doll          |       9.49 |
   | Queen doll         |       9.49 |
   +--------------------+------------+
   4 rows in set (0.00 sec)
   
   mysql> select prod_name from products where prod_price is NULL;
   Empty set (0.00 sec)
   
   mysql> select cust_name from customers where cust_email is null;
   +---------------+
   | cust_name     |
   +---------------+
   | Kids Place    |
   | The Toy Store |
   +---------------+
   2 rows in set (0.00 sec)
   ```

5. 第5课 高级数据过滤

   ```
   mysql> #第五课
   mysql> select prod_id,prod_price,prod_name from products where vend_id='DLL01' and prod_price<=4;
   +---------+------------+---------------------+
   | prod_id | prod_price | prod_name           |
   +---------+------------+---------------------+
   | BNBG01  |       3.49 | Fish bean bag toy   |
   | BNBG02  |       3.49 | Bird bean bag toy   |
   | BNBG03  |       3.49 | Rabbit bean bag toy |
   +---------+------------+---------------------+
   3 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where vend_id='DLL01' or vend_id='BRS01';
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | 8 inch teddy bear   |       5.99 |
   | 12 inch teddy bear  |       8.99 |
   | 18 inch teddy bear  |      11.99 |
   | Fish bean bag toy   |       3.49 |
   | Bird bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | Raggedy Ann         |       4.99 |
   +---------------------+------------+
   7 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where vend_id='DLL01' or vend_id='BRS01' and prod
       -> select prod_name,prod_price from products where vend_id='DLL01' or vend_id='BRS01' and prod_price>=10;
   ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'select prod_name,prod_price from products where vend_id='DLL01' or vend_id='BRS0' at line 2
   mysql> select prod_name,prod_price from products where vend_id='DLL01' or vend_id='BRS01' and prod_price>=10;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | 18 inch teddy bear  |      11.99 |
   | Fish bean bag toy   |       3.49 |
   | Bird bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | Raggedy Ann         |       4.99 |
   +---------------------+------------+
   5 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products where (vend_id='DLL01' or vend_id='BRS01') and prod_price>=10;
   +--------------------+------------+
   | prod_name          | prod_price |
   +--------------------+------------+
   | 18 inch teddy bear |      11.99 |
   +--------------------+------------+
   1 row in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products
       -> where vend_id in ('DLL01','BRS01')
       -> order by prod_name;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | 12 inch teddy bear  |       8.99 |
   | 18 inch teddy bear  |      11.99 |
   | 8 inch teddy bear   |       5.99 |
   | Bird bean bag toy   |       3.49 |
   | Fish bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | Raggedy Ann         |       4.99 |
   +---------------------+------------+
   7 rows in set (0.00 sec)
   
   mysql> select prod_name,prod_price from products
       -> where vend_id ='DLL01' or vend_id = 'BRS01'
       -> order by prod_name;
   +---------------------+------------+
   | prod_name           | prod_price |
   +---------------------+------------+
   | 12 inch teddy bear  |       8.99 |
   | 18 inch teddy bear  |      11.99 |
   | 8 inch teddy bear   |       5.99 |
   | Bird bean bag toy   |       3.49 |
   | Fish bean bag toy   |       3.49 |
   | Rabbit bean bag toy |       3.49 |
   | Raggedy Ann         |       4.99 |
   +---------------------+------------+
   7 rows in set (0.00 sec)
   
   mysql> select prod_name from products
       -> where not vend_id = 'DLL01'
       -> order by prod_name;
   +--------------------+
   | prod_name          |
   +--------------------+
   | 12 inch teddy bear |
   | 18 inch teddy bear |
   | 8 inch teddy bear  |
   | King doll          |
   | Queen doll         |
   +--------------------+
   5 rows in set (0.00 sec)
   
   mysql> select prod_name from products
       -> where vend_id <> 'DLL01'
       -> order by prod_name;
   +--------------------+
   | prod_name          |
   +--------------------+
   | 12 inch teddy bear |
   | 18 inch teddy bear |
   | 8 inch teddy bear  |
   | King doll          |
   | Queen doll         |
   +--------------------+
   5 rows in set (0.00 sec)
   ```

6. 第6课 用通配符进行过滤

   ```
   mysql> #第6课
   mysql> select prod_id, prod name
       -> from products
       -> where prod_name like 'Fish%';
   ERROR 1054 (42S22): Unknown column 'prod' in 'field list'
   mysql> select prod_id, prod_name
       -> from products
       -> where prod_name like 'Fish%';
   +---------+-------------------+
   | prod_id | prod_name         |
   +---------+-------------------+
   | BNBG01  | Fish bean bag toy |
   +---------+-------------------+
   1 row in set (0.00 sec)
   
   mysql> select prod_id, prod_name
       -> from products
       -> where prod_name like '%bean bag%';
   +---------+---------------------+
   | prod_id | prod_name           |
   +---------+---------------------+
   | BNBG01  | Fish bean bag toy   |
   | BNBG02  | Bird bean bag toy   |
   | BNBG03  | Rabbit bean bag toy |
   +---------+---------------------+
   3 rows in set (0.00 sec)
   
   mysql> select prod_name
       -> from products
       -> where prod_name like 'F%y';
   +-------------------+
   | prod_name         |
   +-------------------+
   | Fish bean bag toy |
   +-------------------+
   1 row in set (0.00 sec)
   
   mysql> select prod_id, prod_name
       -> from products
       -> where prod_name like '__ inch teddy bear';
   +---------+--------------------+
   | prod_id | prod_name          |
   +---------+--------------------+
   | BR02    | 12 inch teddy bear |
   | BR03    | 18 inch teddy bear |
   +---------+--------------------+
   2 rows in set (0.00 sec)
   
   mysql> select prod_id, prod_name
       -> from products
       -> where prod_name like '% inch teddy bear';
   +---------+--------------------+
   | prod_id | prod_name          |
   +---------+--------------------+
   | BR01    | 8 inch teddy bear  |
   | BR02    | 12 inch teddy bear |
   | BR03    | 18 inch teddy bear |
   +---------+--------------------+
   3 rows in set (0.00 sec)
   
   mysql> select cust_contact
       -> from customers
       -> where cust_contact like '[JM]%'
       -> order by cust_contact;
   Empty set (0.00 sec)
   
   mysql> select * from customers;
   +------------+---------------+----------------------+-----------+------------+----------+--------------+--------------------+-----------------------+
   | cust_id    | cust_name     | cust_address         | cust_city | cust_state | cust_zip | cust_country | cust_contact       | cust_email            |
   +------------+---------------+----------------------+-----------+------------+----------+--------------+--------------------+-----------------------+
   | 1000000001 | Village Toys  | 200 Maple Lane       | Detroit   | MI         | 44444    | USA          | John Smith         | sales@villagetoys.com |
   | 1000000002 | Kids Place    | 333 South Lake Drive | Columbus  | OH         | 43333    | USA          | Michelle Green     | NULL                  |
   | 1000000003 | Fun4All       | 1 Sunny Place        | Muncie    | IN         | 42222    | USA          | Jim Jones          | jjones@fun4all.com    |
   | 1000000004 | Fun4All       | 829 Riverside Drive  | Phoenix   | AZ         | 88888    | USA          | Denise L. Stephens | dstephens@fun4all.com |
   | 1000000005 | The Toy Store | 4545 53rd Street     | Chicago   | IL         | 54545    | USA          | Kim Howard         | NULL                  |
   +------------+---------------+----------------------+-----------+------------+----------+--------------+--------------------+-----------------------+
   5 rows in set (0.00 sec)
   ```

7. 第7课 创建计算字段

   ```
   mysql> select concat(vend_name,'(',vend_country,')')
       -> from vendors
       -> order by vend_name;
   +----------------------------------------+
   | concat(vend_name,'(',vend_country,')') |
   +----------------------------------------+
   | Bear Emporium(USA)                     |
   | Bears R Us(USA)                        |
   | Doll House Inc.(USA)                   |
   | Fun and Games(England)                 |
   | Furball Inc.(USA)                      |
   | Jouets et ours(France)                 |
   +----------------------------------------+
   6 rows in set (0.01 sec)
   
   mysql> select concat(vend_name,'(',vend_country,')') as vend_title
       -> from vendors
       -> order by vend_name;
   +------------------------+
   | vend_title             |
   +------------------------+
   | Bear Emporium(USA)     |
   | Bears R Us(USA)        |
   | Doll House Inc.(USA)   |
   | Fun and Games(England) |
   | Furball Inc.(USA)      |
   | Jouets et ours(France) |
   +------------------------+
   6 rows in set (0.00 sec)
   
   mysql> select prod_id,quantity, item_price
       -> from orderitems
       -> where order_num = 20008;
   +---------+----------+------------+
   | prod_id | quantity | item_price |
   +---------+----------+------------+
   | RGAN01  |        5 |       4.99 |
   | BR03    |        5 |      11.99 |
   | BNBG01  |       10 |       3.49 |
   | BNBG02  |       10 |       3.49 |
   | BNBG03  |       10 |       3.49 |
   +---------+----------+------------+
   5 rows in set (0.00 sec)
   
   mysql> select prod_id,quantity, item_price, quantity*item_price as expanded_price
       -> from orderitems
       -> where order_num = 20008;
   +---------+----------+------------+----------------+
   | prod_id | quantity | item_price | expanded_price |
   +---------+----------+------------+----------------+
   | RGAN01  |        5 |       4.99 |          24.95 |
   | BR03    |        5 |      11.99 |          59.95 |
   | BNBG01  |       10 |       3.49 |          34.90 |
   | BNBG02  |       10 |       3.49 |          34.90 |
   | BNBG03  |       10 |       3.49 |          34.90 |
   +---------+----------+------------+----------------+
   5 rows in set (0.00 sec)
   ```

8. 第8课 使用函数处理数据

   ```
   mysql> select vend_name, upper(vend_name) as vend_name_upcase
       -> from vendors
       -> order by vend_name;
   +-----------------+------------------+
   | vend_name       | vend_name_upcase |
   +-----------------+------------------+
   | Bear Emporium   | BEAR EMPORIUM    |
   | Bears R Us      | BEARS R US       |
   | Doll House Inc. | DOLL HOUSE INC.  |
   | Fun and Games   | FUN AND GAMES    |
   | Furball Inc.    | FURBALL INC.     |
   | Jouets et ours  | JOUETS ET OURS   |
   +-----------------+------------------+
   6 rows in set (0.00 sec)
   
   mysql> select cust_name, cust_contact
       -> from customers
       -> where cust_contact =
       -> 'Micheal Green';
   Empty set (0.00 sec)
   
   mysql> select cust_name, cust_contact
       -> from customers
       -> where soundex(cust_contact) = soundex('Michael Green');
   +------------+----------------+
   | cust_name  | cust_contact   |
   +------------+----------------+
   | Kids Place | Michelle Green |
   +------------+----------------+
   1 row in set (0.00 sec)
   
   mysql> select order_num
       -> from orders
       -> where year(order_date) = 2012;
   +-----------+
   | order_num |
   +-----------+
   |     20005 |
   |     20006 |
   |     20007 |
   |     20008 |
   |     20009 |
   +-----------+
   5 rows in set (0.00 sec)
   ```

9. 第9课 汇总数据

   ```
   mysql> select avg(prod_price) as avg_price
       -> from products;
   +-----------+
   | avg_price |
   +-----------+
   |  6.823333 |
   +-----------+
   1 row in set (0.01 sec)
   
   mysql> select avg(prod_price) as avg_price
       -> from products
       -> where vend_id = 'DLL01';
   +-----------+
   | avg_price |
   +-----------+
   |  3.865000 |
   +-----------+
   1 row in set (0.00 sec)
   
   mysql> select count(*) as num_cust
       -> from customers;
   +----------+
   | num_cust |
   +----------+
   |        5 |
   +----------+
   1 row in set (0.02 sec)
   
   mysql> select count(cust_email) as num_cust
       -> from customers;
   +----------+
   | num_cust |
   +----------+
   |        3 |
   +----------+
   1 row in set (0.00 sec)
   
   mysql> select max(prod_price) as max_price
       -> from products;
   +-----------+
   | max_price |
   +-----------+
   |     11.99 |
   +-----------+
   1 row in set (0.01 sec)
   
   mysql> select min(prod_price) as min_price
       -> from products;
   +-----------+
   | min_price |
   +-----------+
   |      3.49 |
   +-----------+
   1 row in set (0.00 sec)
   
   mysql> select sum(quantity) as items_ordered
       -> from orderitems
       -> where order_num = 20005;
   +---------------+
   | items_ordered |
   +---------------+
   |           200 |
   +---------------+
   1 row in set (0.00 sec)
   
   mysql> select sum(item_price*quantity) as total_price
       -> from orderitems
       -> where order_num = 20005;
   +-------------+
   | total_price |
   +-------------+
   |     1648.00 |
   +-------------+
   1 row in set (0.01 sec)
   
   mysql> select avg(distinct prod_price) as avg_price
       -> from products
       -> where vend_id = 'DLL01';
   +-----------+
   | avg_price |
   +-----------+
   |  4.240000 |
   +-----------+
   1 row in set (0.01 sec)
   
   mysql> select count(*) as num_items, min(prod_price) as price_min, max(prod_price) as price_max, avg(prod_price) as price_avg
       -> from products;
   +-----------+-----------+-----------+-----------+
   | num_items | price_min | price_max | price_avg |
   +-----------+-----------+-----------+-----------+
   |         9 |      3.49 |     11.99 |  6.823333 |
   +-----------+-----------+-----------+-----------+
   1 row in set (0.00 sec)
   ```

   

10. 第10课 分组数据

    ```
    mysql> select count(*) as num_prods
        -> from products
        -> where vend_id = 'DLL01';
    +-----------+
    | num_prods |
    +-----------+
    |         4 |
    +-----------+
    1 row in set (0.01 sec)
    
    mysql> select count(*) as num_prods
        -> from products;
    +-----------+
    | num_prods |
    +-----------+
    |         9 |
    +-----------+
    1 row in set (0.00 sec)
    
    mysql> select count(*) as num_prods
        -> from products
        -> group by vend_id;
    +-----------+
    | num_prods |
    +-----------+
    |         3 |
    |         4 |
    |         2 |
    +-----------+
    3 rows in set (0.00 sec)
    
    mysql> select cust_id, count(*) as orders
        -> from orders
        -> group by cust_id
        -> having count(*)>=2;
    +------------+--------+
    | cust_id    | orders |
    +------------+--------+
    | 1000000001 |      2 |
    +------------+--------+
    1 row in set (0.00 sec)
    
    mysql> select vend_id, count(*) as num_prods
        -> from products
        -> where prod_price >= 4
        -> group by vend_id
        -> having count(*)>=2;
    +---------+-----------+
    | vend_id | num_prods |
    +---------+-----------+
    | BRS01   |         3 |
    | FNG01   |         2 |
    +---------+-----------+
    2 rows in set (0.00 sec)
    
    mysql> select vend_id, count(*) as num_prods
        -> from products
        -> group by vend_id
        -> having count(*)>=2;
    +---------+-----------+
    | vend_id | num_prods |
    +---------+-----------+
    | BRS01   |         3 |
    | DLL01   |         4 |
    | FNG01   |         2 |
    +---------+-----------+
    3 rows in set (0.00 sec)
    
    mysql> select order_num, count(*) as items
        -> from orderitems
        -> group by order_num
        -> having count(*)>=3;
    +-----------+-------+
    | order_num | items |
    +-----------+-------+
    |     20006 |     3 |
    |     20007 |     5 |
    |     20008 |     5 |
    |     20009 |     3 |
    +-----------+-------+
    4 rows in set (0.00 sec)
    
    mysql> select order_num, count(*) as items
        -> from orderitems
        -> group by order_num
        -> having count(*)>=3
        -> order by items, order_num;
    +-----------+-------+
    | order_num | items |
    +-----------+-------+
    |     20006 |     3 |
    |     20009 |     3 |
    |     20007 |     5 |
    |     20008 |     5 |
    +-----------+-------+
    4 rows in set (0.00 sec)
    ```

11. 第11课 利用子查询

    ```
    mysql> #第11课
    mysql> select order_num
        -> from orderitems
        -> where prod_id='RGAN01';
    +-----------+
    | order_num |
    +-----------+
    |     20007 |
    |     20008 |
    +-----------+
    2 rows in set (0.00 sec)
    
    mysql> select cust_id
        -> from orders
        -> where order_num in (select order_num)
        -> ;
    +------------+
    | cust_id    |
    +------------+
    | 1000000001 |
    | 1000000001 |
    | 1000000003 |
    | 1000000004 |
    | 1000000005 |
    +------------+
    5 rows in set (0.01 sec)
    
    mysql> select cust_id
        -> from orders
        -> where order_num in (select order_num
        ->                  from orderitems
        ->                  where prod_id='RGAN01');
    +------------+
    | cust_id    |
    +------------+
    | 1000000004 |
    | 1000000005 |
    +------------+
    2 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact
        -> from customers
        -> where cust_id in ('1000000004','1000000005');
    +---------------+--------------------+
    | cust_name     | cust_contact       |
    +---------------+--------------------+
    | Fun4All       | Denise L. Stephens |
    | The Toy Store | Kim Howard         |
    +---------------+--------------------+
    2 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact
        -> from customers
        -> where cust_id in (select cust_id
        ->                  from orders
        ->                  where order_num in (select order_num
        ->                                  from orderitems
        ->                                  where prod_id = 'RGAN01'));
    +---------------+--------------------+
    | cust_name     | cust_contact       |
    +---------------+--------------------+
    | Fun4All       | Denise L. Stephens |
    | The Toy Store | Kim Howard         |
    +---------------+--------------------+
    2 rows in set (0.01 sec)
    
    mysql> select count(*) as orders
        -> from orders
        -> where cust_id = '1000000001';
    +--------+
    | orders |
    +--------+
    |      2 |
    +--------+
    1 row in set (0.00 sec)
    
    mysql> select cust_name, cust_state, (select count(*)
        ->                                  from orders
        ->                                  where orders.cust_id = customers.cust_id) as orders
        -> from customers
        -> order by cust_name;
    +---------------+------------+--------+
    | cust_name     | cust_state | orders |
    +---------------+------------+--------+
    | Fun4All       | IN         |      1 |
    | Fun4All       | AZ         |      1 |
    | Kids Place    | OH         |      0 |
    | The Toy Store | IL         |      1 |
    | Village Toys  | MI         |      2 |
    +---------------+------------+--------+
    5 rows in set (0.01 sec)
    
    mysql> select cust_name, cust_state, (select count(*)
        ->                                  from orders
        ->                                  where cust_id = cust_id) as orders
        -> from customers
        -> order by cust_name;
    +---------------+------------+--------+
    | cust_name     | cust_state | orders |
    +---------------+------------+--------+
    | Fun4All       | IN         |      5 |
    | Fun4All       | AZ         |      5 |
    | Kids Place    | OH         |      5 |
    | The Toy Store | IL         |      5 |
    | Village Toys  | MI         |      5 |
    +---------------+------------+--------+
    5 rows in set (0.00 sec)
    ```

    

12. 第12课 联结表

    ```
    mysql> select vend_name,prod_name,prod_price
        -> from vendors,products
        -> where vendors.vend_id = products.vend_id;
    +-----------------+---------------------+------------+
    | vend_name       | prod_name           | prod_price |
    +-----------------+---------------------+------------+
    | Doll House Inc. | Fish bean bag toy   |       3.49 |
    | Doll House Inc. | Bird bean bag toy   |       3.49 |
    | Doll House Inc. | Rabbit bean bag toy |       3.49 |
    | Bears R Us      | 8 inch teddy bear   |       5.99 |
    | Bears R Us      | 12 inch teddy bear  |       8.99 |
    | Bears R Us      | 18 inch teddy bear  |      11.99 |
    | Doll House Inc. | Raggedy Ann         |       4.99 |
    | Fun and Games   | King doll           |       9.49 |
    | Fun and Games   | Queen doll          |       9.49 |
    +-----------------+---------------------+------------+
    9 rows in set (0.00 sec)
    
    mysql> select vend_name, prod_name, prod_price
        -> from vendors, products;
    +-----------------+---------------------+------------+
    | vend_name       | prod_name           | prod_price |
    +-----------------+---------------------+------------+
    | Bear Emporium   | Fish bean bag toy   |       3.49 |
    | Bears R Us      | Fish bean bag toy   |       3.49 |
    | Doll House Inc. | Fish bean bag toy   |       3.49 |
    | Fun and Games   | Fish bean bag toy   |       3.49 |
    | Furball Inc.    | Fish bean bag toy   |       3.49 |
    | Jouets et ours  | Fish bean bag toy   |       3.49 |
    | Bear Emporium   | Bird bean bag toy   |       3.49 |
    | Bears R Us      | Bird bean bag toy   |       3.49 |
    | Doll House Inc. | Bird bean bag toy   |       3.49 |
    | Fun and Games   | Bird bean bag toy   |       3.49 |
    | Furball Inc.    | Bird bean bag toy   |       3.49 |
    | Jouets et ours  | Bird bean bag toy   |       3.49 |
    | Bear Emporium   | Rabbit bean bag toy |       3.49 |
    | Bears R Us      | Rabbit bean bag toy |       3.49 |
    | Doll House Inc. | Rabbit bean bag toy |       3.49 |
    | Fun and Games   | Rabbit bean bag toy |       3.49 |
    | Furball Inc.    | Rabbit bean bag toy |       3.49 |
    | Jouets et ours  | Rabbit bean bag toy |       3.49 |
    | Bear Emporium   | 8 inch teddy bear   |       5.99 |
    | Bears R Us      | 8 inch teddy bear   |       5.99 |
    | Doll House Inc. | 8 inch teddy bear   |       5.99 |
    | Fun and Games   | 8 inch teddy bear   |       5.99 |
    | Furball Inc.    | 8 inch teddy bear   |       5.99 |
    | Jouets et ours  | 8 inch teddy bear   |       5.99 |
    | Bear Emporium   | 12 inch teddy bear  |       8.99 |
    | Bears R Us      | 12 inch teddy bear  |       8.99 |
    | Doll House Inc. | 12 inch teddy bear  |       8.99 |
    | Fun and Games   | 12 inch teddy bear  |       8.99 |
    | Furball Inc.    | 12 inch teddy bear  |       8.99 |
    | Jouets et ours  | 12 inch teddy bear  |       8.99 |
    | Bear Emporium   | 18 inch teddy bear  |      11.99 |
    | Bears R Us      | 18 inch teddy bear  |      11.99 |
    | Doll House Inc. | 18 inch teddy bear  |      11.99 |
    | Fun and Games   | 18 inch teddy bear  |      11.99 |
    | Furball Inc.    | 18 inch teddy bear  |      11.99 |
    | Jouets et ours  | 18 inch teddy bear  |      11.99 |
    | Bear Emporium   | Raggedy Ann         |       4.99 |
    | Bears R Us      | Raggedy Ann         |       4.99 |
    | Doll House Inc. | Raggedy Ann         |       4.99 |
    | Fun and Games   | Raggedy Ann         |       4.99 |
    | Furball Inc.    | Raggedy Ann         |       4.99 |
    | Jouets et ours  | Raggedy Ann         |       4.99 |
    | Bear Emporium   | King doll           |       9.49 |
    | Bears R Us      | King doll           |       9.49 |
    | Doll House Inc. | King doll           |       9.49 |
    | Fun and Games   | King doll           |       9.49 |
    | Furball Inc.    | King doll           |       9.49 |
    | Jouets et ours  | King doll           |       9.49 |
    | Bear Emporium   | Queen doll          |       9.49 |
    | Bears R Us      | Queen doll          |       9.49 |
    | Doll House Inc. | Queen doll          |       9.49 |
    | Fun and Games   | Queen doll          |       9.49 |
    | Furball Inc.    | Queen doll          |       9.49 |
    | Jouets et ours  | Queen doll          |       9.49 |
    +-----------------+---------------------+------------+
    54 rows in set (0.00 sec)
    
    mysql> select vend_name,prod_name,prod_price
        -> from vendors inner join products
        -> on vendors.vend_id = products.vend_id;
    +-----------------+---------------------+------------+
    | vend_name       | prod_name           | prod_price |
    +-----------------+---------------------+------------+
    | Doll House Inc. | Fish bean bag toy   |       3.49 |
    | Doll House Inc. | Bird bean bag toy   |       3.49 |
    | Doll House Inc. | Rabbit bean bag toy |       3.49 |
    | Bears R Us      | 8 inch teddy bear   |       5.99 |
    | Bears R Us      | 12 inch teddy bear  |       8.99 |
    | Bears R Us      | 18 inch teddy bear  |      11.99 |
    | Doll House Inc. | Raggedy Ann         |       4.99 |
    | Fun and Games   | King doll           |       9.49 |
    | Fun and Games   | Queen doll          |       9.49 |
    +-----------------+---------------------+------------+
    9 rows in set (0.01 sec)
    
    mysql> select prod_name, vend_name, prod_price, quantity
        -> from orderitems, products, vendors
        -> where products.vend_id = vendors.vend_id
        -> and orderitems.prod_id = products.prod_id
        -> and order_num = 20007;
    +---------------------+-----------------+------------+----------+
    | prod_name           | vend_name       | prod_price | quantity |
    +---------------------+-----------------+------------+----------+
    | 18 inch teddy bear  | Bears R Us      |      11.99 |       50 |
    | Fish bean bag toy   | Doll House Inc. |       3.49 |      100 |
    | Bird bean bag toy   | Doll House Inc. |       3.49 |      100 |
    | Rabbit bean bag toy | Doll House Inc. |       3.49 |      100 |
    | Raggedy Ann         | Doll House Inc. |       4.99 |       50 |
    +---------------------+-----------------+------------+----------+
    5 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact
        -> from customers, orders, orderitems
        -> where customers.cust_id = orders.cust_id
        -> and orderitems.order_num = orders.order_num
        -> and prod_id = 'RGAN01';
    +---------------+--------------------+
    | cust_name     | cust_contact       |
    +---------------+--------------------+
    | Fun4All       | Denise L. Stephens |
    | The Toy Store | Kim Howard         |
    +---------------+--------------------+
    2 rows in set (0.00 sec)
    ```

13. 第13课 创建高级联结

    ```
    mysql> #13
    mysql> select cust_name,cust_contact
        -> from customers as c, orders as o, orderitems as oi
        -> where c.cust_id = o.cust_id
        -> and oi.order_num = o.order_num
        -> and prod_id = 'RGAN01';
    +---------------+--------------------+
    | cust_name     | cust_contact       |
    +---------------+--------------------+
    | Fun4All       | Denise L. Stephens |
    | The Toy Store | Kim Howard         |
    +---------------+--------------------+
    2 rows in set (0.00 sec)
    
    mysql> select cust_id, cust_name, cust_contact
        -> from customers
        -> where cust_name = (select cust_name
        ->                  from customers
        ->                  where cust_contact = 'Jim Jones');
    +------------+-----------+--------------------+
    | cust_id    | cust_name | cust_contact       |
    +------------+-----------+--------------------+
    | 1000000003 | Fun4All   | Jim Jones          |
    | 1000000004 | Fun4All   | Denise L. Stephens |
    +------------+-----------+--------------------+
    2 rows in set (0.00 sec)
    
    mysql> select c1.cust_id, ci.cust_name, c1.cust_contact
        -> from customers as c1, customers as c2
        -> where c1.cust_name = c2.cust_name
        -> and c2.cust_contact = 'Jim Jones';
    ERROR 1054 (42S22): Unknown column 'ci.cust_name' in 'field list'
    mysql> select c1.cust_id, c1.cust_name, c1.cust_contact
        -> from customers as c1, customers as c2
        -> where c1.cust_name = c2.cust_name
        -> and c2.cust_contact = 'Jim Jones';
    +------------+-----------+--------------------+
    | cust_id    | cust_name | cust_contact       |
    +------------+-----------+--------------------+
    | 1000000003 | Fun4All   | Jim Jones          |
    | 1000000004 | Fun4All   | Denise L. Stephens |
    +------------+-----------+--------------------+
    2 rows in set (0.00 sec)
    
    mysql> select c.*, o.order_num, o.order_date, oi.prod_id, oi.quantity, oi.item_price
        -> from customers as c, orders as o, orderitems as oi
        -> where c.cust_id = o.cust_id
        -> and oi.order_num = o.order_num
        -> and prod_id = 'RGAN01';
    +------------+---------------+---------------------+-----------+------------+----------+--------------+--------------------+-----------------------+-----------+---------------------+---------+----------+------------+
    | cust_id    | cust_name     | cust_address        | cust_city | cust_state | cust_zip | cust_country | cust_contact       | cust_email            | order_num | order_date          | prod_id | quantity | item_price |
    +------------+---------------+---------------------+-----------+------------+----------+--------------+--------------------+-----------------------+-----------+---------------------+---------+----------+------------+
    | 1000000004 | Fun4All       | 829 Riverside Drive | Phoenix   | AZ         | 88888    | USA          | Denise L. Stephens | dstephens@fun4all.com |     20007 | 2012-01-30 00:00:00 | RGAN01  |       50 |       4.49 |
    | 1000000005 | The Toy Store | 4545 53rd Street    | Chicago   | IL         | 54545    | USA          | Kim Howard         | NULL                  |     20008 | 2012-02-03 00:00:00 | RGAN01  |        5 |       4.99 |
    +------------+---------------+---------------------+-----------+------------+----------+--------------+--------------------+-----------------------+-----------+---------------------+---------+----------+------------+
    2 rows in set (0.01 sec)
    
    mysql> select customers.cust_id, orders.order_num
        -> from customers inner join orders
        -> on customers.cust_id = orders.cust_id;
    +------------+-----------+
    | cust_id    | order_num |
    +------------+-----------+
    | 1000000001 |     20005 |
    | 1000000001 |     20009 |
    | 1000000003 |     20006 |
    | 1000000004 |     20007 |
    | 1000000005 |     20008 |
    +------------+-----------+
    5 rows in set (0.00 sec)
    
    mysql> select customers.cust_id, orders.order_num
        -> from customers left outer join orders
        -> on customers.cust_id = orders.cust_id;
    +------------+-----------+
    | cust_id    | order_num |
    +------------+-----------+
    | 1000000001 |     20005 |
    | 1000000001 |     20009 |
    | 1000000002 |      NULL |
    | 1000000003 |     20006 |
    | 1000000004 |     20007 |
    | 1000000005 |     20008 |
    +------------+-----------+
    6 rows in set (0.00 sec)
    
    mysql> select customers.cust_id, orders.order_num
        -> from customers right outer join orders
        -> on customers.cust_id = orders.cust_id;
    +------------+-----------+
    | cust_id    | order_num |
    +------------+-----------+
    | 1000000001 |     20005 |
    | 1000000001 |     20009 |
    | 1000000003 |     20006 |
    | 1000000004 |     20007 |
    | 1000000005 |     20008 |
    +------------+-----------+
    5 rows in set (0.00 sec)
    
    mysql> select customers.cust_id, count(orders.order_num) as num_ord
        -> from customers inner join orders
        -> on customers.cust_id = orders.cust_id
        -> group by customers.cust_id;
    +------------+---------+
    | cust_id    | num_ord |
    +------------+---------+
    | 1000000001 |       2 |
    | 1000000003 |       1 |
    | 1000000004 |       1 |
    | 1000000005 |       1 |
    +------------+---------+
    4 rows in set (0.00 sec)
    
    mysql> select customers.cust_id, count(orders.order_num) as num_ord
        -> from customers left outer join orders
        -> on customers.cust_id = orders.cust_id
        -> group by customers.cust_id;
    +------------+---------+
    | cust_id    | num_ord |
    +------------+---------+
    | 1000000001 |       2 |
    | 1000000002 |       0 |
    | 1000000003 |       1 |
    | 1000000004 |       1 |
    | 1000000005 |       1 |
    +------------+---------+
    5 rows in set (0.00 sec)
    ```

14. 第14课 组合查询

    ```
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_state in ('IL','IN','MI');
    +---------------+--------------+-----------------------+
    | cust_name     | cust_contact | cust_email            |
    +---------------+--------------+-----------------------+
    | Village Toys  | John Smith   | sales@villagetoys.com |
    | Fun4All       | Jim Jones    | jjones@fun4all.com    |
    | The Toy Store | Kim Howard   | NULL                  |
    +---------------+--------------+-----------------------+
    3 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_name = 'FUN4ALL';
    +-----------+--------------------+-----------------------+
    | cust_name | cust_contact       | cust_email            |
    +-----------+--------------------+-----------------------+
    | Fun4All   | Jim Jones          | jjones@fun4all.com    |
    | Fun4All   | Denise L. Stephens | dstephens@fun4all.com |
    +-----------+--------------------+-----------------------+
    2 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_state in ('IL','IN','MI')
        -> union
        -> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_name = 'FUN4ALL';
    +---------------+--------------------+-----------------------+
    | cust_name     | cust_contact       | cust_email            |
    +---------------+--------------------+-----------------------+
    | Village Toys  | John Smith         | sales@villagetoys.com |
    | Fun4All       | Jim Jones          | jjones@fun4all.com    |
    | The Toy Store | Kim Howard         | NULL                  |
    | Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
    +---------------+--------------------+-----------------------+
    4 rows in set (0.01 sec)
    
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_state in ('IL','IN','MI')
        -> or cust_name = 'FUN4ALL';
    +---------------+--------------------+-----------------------+
    | cust_name     | cust_contact       | cust_email            |
    +---------------+--------------------+-----------------------+
    | Village Toys  | John Smith         | sales@villagetoys.com |
    | Fun4All       | Jim Jones          | jjones@fun4all.com    |
    | Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
    | The Toy Store | Kim Howard         | NULL                  |
    +---------------+--------------------+-----------------------+
    4 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_state in ('IL','IN','MI')
        -> union all
        -> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_name = 'FUN4ALL';
    +---------------+--------------------+-----------------------+
    | cust_name     | cust_contact       | cust_email            |
    +---------------+--------------------+-----------------------+
    | Village Toys  | John Smith         | sales@villagetoys.com |
    | Fun4All       | Jim Jones          | jjones@fun4all.com    |
    | The Toy Store | Kim Howard         | NULL                  |
    | Fun4All       | Jim Jones          | jjones@fun4all.com    |
    | Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
    +---------------+--------------------+-----------------------+
    5 rows in set (0.00 sec)
    
    mysql> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_state in ('IL','IN','MI')
        -> union
        -> select cust_name, cust_contact, cust_email
        -> from customers
        -> where cust_name = 'FUN4ALL'
        -> order by cust_name, cust_contact;
    +---------------+--------------------+-----------------------+
    | cust_name     | cust_contact       | cust_email            |
    +---------------+--------------------+-----------------------+
    | Fun4All       | Denise L. Stephens | dstephens@fun4all.com |
    | Fun4All       | Jim Jones          | jjones@fun4all.com    |
    | The Toy Store | Kim Howard         | NULL                  |
    | Village Toys  | John Smith         | sales@villagetoys.com |
    +---------------+--------------------+-----------------------+
    4 rows in set (0.00 sec)
    ```

15. 第15课 插入数据

    ```
    mysql> insert into customers
        -> values('1000000006',
        ->          'Toy Land',
        ->          '123 Any Street',
        ->          'New York',
        ->          'NY',
        ->          '11111',
        ->          'USA',
        ->          NULL,
        ->          NULL);
    Query OK, 1 row affected (0.02 sec)
    
    mysql> insert into customers(cust_id,
        ->                  cust_contact,
        ->                  cust_email,
        ->                  cust_name,
        ->                  cust_address,
        ->                  cust_city,
        ->                  cust_state,
        ->                  cust_zip)
        -> values('1000000006',
        ->          NULL,
        ->          NULL,
        ->          'Toy Land',
        ->          '123 Any Street',
        ->          'New York',
        ->          'NY',
        ->          '11111');
    ERROR 1062 (23000): Duplicate entry '1000000006' for key 'customers.PRIMARY'
    mysql> select *
        -> into custcopy
        -> from customers;
    ERROR 1327 (42000): Undeclared variable: custcopy
    mysql> create table custcopy as
        -> select * from customers;
    Query OK, 6 rows affected (0.77 sec)
    Records: 6  Duplicates: 0  Warnings: 0
    ```

16. 第16课 更新和删除数据

    ```
    mysql> update customers
        -> set cust_email = 'kim@thetoystore.com'
        -> where cust_id = '1000000005';
    Query OK, 1 row affected (0.01 sec)
    Rows matched: 1  Changed: 1  Warnings: 0
    
    mysql> update customers
        -> set cust_contact = 'Sam Roberts',
        ->          cust_email = 'sam@toyland.com'
        -> where cust_id = '1000000006';
    Query OK, 1 row affected (0.01 sec)
    Rows matched: 1  Changed: 1  Warnings: 0
    
    mysql> update customers
        -> set cust_email = NULL
        -> where cust_id = '1000000005';
    Query OK, 1 row affected (0.01 sec)
    Rows matched: 1  Changed: 1  Warnings: 0
    
    mysql> delete from customers
        -> where cust_id = '1000000006';
    Query OK, 1 row affected (0.01 sec)
    ```

17. 第17课 创建和操纵表

    ```
    mysql> create table products1
        -> (
        ->  product_id1     char(10)        NOT NULL,
        ->  vend_id1        char(10)        NOT NULL,
        -> prod_name        char(254)       NOT NULL,
        -> prod_price       DECIMAL(8,2)    NOT NULL,
        -> prod_desc        VARCHAR(1000)   NULL
        -> );
    Query OK, 0 rows affected (0.06 sec)
    
    mysql> create table orders1
        -> (
        -> order_num1 integer NOT NULL,
        -> order_date1 DATETIME NOT NULL,
        -> cust_id1 CHAR(10) NOT NULL
        -> );
    Query OK, 0 rows affected (0.08 sec)
    
    mysql> CREATE TABLE Vendors
        -> (
        ->   vend_id      char(10) NOT NULL ,
        ->   vend_name    char(50) NOT NULL ,
        ->   vend_address char(50) NULL ,
        ->   vend_city    char(50) NULL ,
        ->   vend_state   char(5)  NULL ,
        ->   vend_zip     char(10) NULL ,
        ->   vend_country char(50) NULL
        -> );
    ERROR 1050 (42S01): Table 'vendors' already exists
    mysql> CREATE TABLE OrderItems
        -> (
        ->   order_num  int          NOT NULL ,
        ->   order_item int          NOT NULL ,
        ->   prod_id    char(10)     NOT NULL ,
        ->   quantity   int          NOT NULL   DEFAULT 1 ,
        ->   item_price decimal(8,2) NOT NULL
        -> );
    ERROR 1050 (42S01): Table 'orderitems' already exists
    mysql> alter table vendors
        -> add vend_phone CHAR(20);
    Query OK, 0 rows affected (0.06 sec)
    Records: 0  Duplicates: 0  Warnings: 0
    
    mysql> alter table vendors
        -> DROP COLUMN vend_phone;
    Query OK, 0 rows affected (0.23 sec)
    Records: 0  Duplicates: 0  Warnings: 0
    ```

    