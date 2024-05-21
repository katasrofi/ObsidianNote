- CREATE TABLE -> Make new table
- ADD COLUMN
- DROP TABLE -> for delete
- RENAME TABLE NAME TO NEW_NAME

### SELECT 
- SELECT * FROM table_name;
	- Akan menampilkan semua data
- SELECT * FROM table_name WHERE COLUMNS = 'Filter';
	- Akan menampilkan data hanya berdasarkan filter saja
- SELECT DISTINCT Columns FROM table_name;
	- Akan menampilkan data berdasarkan nilai unique saja
- SELECT * FROm table_name LIMIT n;
	- Akan menampilkan jumlah data berdasarkan seberapa banyak n
- SELECT * FROm table_name OFFSET m LIMIT n;
	- Akan menampilkan jumlah data berdasarkan dari m sebanyak n
		- misal OFFSET 6 LIMIT 5 maka akan menunjukkan data dari urutan 7 sampai 12
- SELECT * FROM table name WHERE COLUMNS IN ('Condition1', 'Condition2', 'Condition3', 'Condition4';
	- Hanya akan menampilkan data berdasarkan kondisinya saja
### Between
SELECT * FROM person                                                                                                                  WHERE date_of_birth                                                                                                                           BETWEEN DATE '2000-01-01' AND '2023-01-01';
	- Menampilkan data diantara tahun 2000 - 2023

### LIKE and ILIKE
SELECT * FROM person                                                                                                                 WHERE email LIKE '%opera.com';
	- Menampilkan data yang hanya menunjukkan kata kunci setelah LIKE
		- % berarti any character

### GROUP BY
SELECT country, COUNT(`*`) FROM person GROUP BY country;
	- Menampilkan data yang dikelompokkan berdasarkan GROUP BY

### GROUP BY HAVING
SELECT country, COUNT(*) FROM person 
GROUP BY country HAVING COUNT(*) > 9 ORDER BY count DESC;
	- Menampilkan data hanya diatas nilai yang ditentukan (n=9 pada contoh diatas)

### MIN MAX AVG
SELECT make, model, 
MIN(price) AS min_price, 
MAX(price) as max_price, 
ROUND(AVG(price), 2) as average_price 
FROM car GROUP BY make, model;
- Menampilkan data min max dan avg dari price

### COALESCE
SELECT COALESCE(email, 'Null') FROM person;
	- Memberikan nilai default pada null value

### Primary Key
ALTER TABLE table_names ADD PRIMARY KEY(columns);
- Columns yang digunakan akan otomatis jadi primary key

### ADD UNIQUE KEY
ALTER TABLE table_name ADD CONSTRAINT gender_diff 
CHECK(gender = 'Male' OR gender = 'Female');
	- Add unique kolom untuk memastikan semua input gender adalah male and female