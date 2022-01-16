# Sql-Querys
Patika Sql Eğitim Ödevleri
## Ödev 1 
1. Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

`SELECT title, description FROM film;`
                    
2. Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.  
  
`SELECT * FROM film WHERE (length>60 AND length<75);`

3. Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

`SELECT * FROM film WHERE replacement_cost=12.99 OR replacement_cost=28.99;`

4. Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

`SELECT last_name FROM customer WHERE first_name='Mary';`

5. Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynFı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.                

`SELECT * FROM film WHERE length<50 AND NOT(rental_rate=2.99 OR rental_rate=4.99);`


## Ödev 2


1. Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

`SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;`

2. .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

`SELECT first_name, last_name FROM actor WHERE first_name IN('Penelope', 'Nick', 'Ed');`

3. Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

`SELECT * FROM film WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99);`




## Ödev 3

1. Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

`SELECT country FROM country WHERE country LIKE 'A%a';`

2. Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

`SELECT country FROM country WHERE country LIKE '_____%n';`

3. Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

`SELECT title FROM film WHERE title ILIKE '%t%t%t%t%';`

4. Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

`SELECT * FROM film WHERE title LIKE 'C%' AND length>90 AND rental_rate=2.99;`


## Ödev 4

1. Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

`SELECT  DISTINCT replacement_cost FROM film;`

2. Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

`SELECT COUNT(DISTINCT replacement_cost) FROM film;`

3. Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

`SELECT COUNT(title) FROM film WHERE title LIKE 'T%' AND rating='G';`

4. Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

`SELECT COUNT(country) FROM country WHERE country LIKE '_____';`

5. City tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

`SELECT COUNT(city) FROM city WHERE city ILIKE '%R'; `


## Ödev 5

1. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

`SELECT title FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5; `

2. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

`SELECT title FROM film WHERE title LIKE '%n' ORDER BY length ASC OFFSET 5 LIMIT 5;`

3. Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

`SELECT title FROM customer WHERE store_id=1 ORDER BY last_name DESC LIMIT 4;`


## Ödev 6

1. Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

`SELECT ROUND(AVG(rental_rate), 3) FROM film;`

2. Film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

`SELECT COUNT(title) FROM film WHERE title LIKE 'C%' `

3. Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

`SELECT MAX(length) FROM film WHERE rental_rate=0.99`

4. Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

`SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length>150`

## Ödev 7

1. Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

`SELECT rental_rate FROM film GROUP BY rental_rate`

2. Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

`SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*)>50;`

3. Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

`SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;`

4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

`SELECT country_id, COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;`


## Ödev 8

1. Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```
CREATE TABLE employee(
	id SERIAL PRIMARY KEY, 
	name VARCHAR(50) NOT NULL,
	birthday DATE,
	email VARCHAR(100)
);
```

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

![mocoro](https://user-images.githubusercontent.com/45533057/149657133-8a159851-f7d7-4823-bad3-7febe635f77d.png)

```
insert into employee (name, birthday, email) values ('Reeta Dulieu', '2021/08/08', 'rdulieu0@ibm.com');
insert into employee (name, birthday, email) values ('Ashlie Kippins', '2021/04/18', 'akippins1@geocities.com');
insert into employee (name, birthday, email) values ('Karlie Fines', '2021/02/14', 'kfines2@yellowpages.com');
insert into employee (name, birthday, email) values ('Avrit Renvoys', '2021/09/19', null);
insert into employee (name, birthday, email) values ('Karlis Spriggin', '2021/08/14', 'kspriggin4@etsy.com');
insert into employee (name, birthday, email) values ('Magdalene Phelipeau', '2021/03/02', null);
insert into employee (name, birthday, email) values ('Jeth Dearing', '2021/07/19', 'jdearing6@redcross.org');
insert into employee (name, birthday, email) values ('Giuditta Longland', null, null);
insert into employee (name, birthday, email) values ('Cassius Reggio', '2021/02/12', 'creggio8@skyrock.com');
insert into employee (name, birthday, email) values ('Hanan Kynd', '2021/08/12', 'hkynd9@paypal.com');
insert into employee (name, birthday, email) values ('Elsa Lancaster', '2021/06/21', 'elancastera@salon.com');
insert into employee (name, birthday, email) values ('Evanne Becks', '2021/12/21', 'ebecksb@vimeo.com');
insert into employee (name, birthday, email) values ('Ewell Habron', '2021/10/27', 'ehabronc@epa.gov');
insert into employee (name, birthday, email) values ('Meggy Kiwitz', '2021/03/08', 'mkiwitzd@ft.com');
insert into employee (name, birthday, email) values ('Aloysia Mitcham', '2021/07/14', 'amitchame@utexas.edu');
insert into employee (name, birthday, email) values ('Renie Alishoner', '2021/11/20', 'ralishonerf@arstechnica.com');
insert into employee (name, birthday, email) values ('Ebenezer Martignon', '2021/05/25', 'emartignong@comcast.net');
insert into employee (name, birthday, email) values ('Urbano Kelwaybamber', '2021/05/26', 'ukelwaybamberh@friendfeed.com');
insert into employee (name, birthday, email) values ('Tedmund Deacon', '2021/05/30', null);
insert into employee (name, birthday, email) values ('Orelie Urion', '2021/12/02', 'ourionj@google.co.uk');
insert into employee (name, birthday, email) values ('Katya Ludee', '2021/07/27', 'kludeek@sohu.com');
insert into employee (name, birthday, email) values ('Sylas Howles', '2021/06/07', 'showlesl@nsw.gov.au');
insert into employee (name, birthday, email) values ('Maxie Mutlow', '2021/03/25', 'mmutlowm@stanford.edu');
insert into employee (name, birthday, email) values ('Maryann Truesdale', '2021/05/08', 'mtruesdalen@sbwire.com');
insert into employee (name, birthday, email) values ('Ebenezer Edmeads', '2021/07/27', 'eedmeadso@businesswire.com');
insert into employee (name, birthday, email) values ('Colman Alabone', '2021/09/28', 'calabonep@behance.net');
insert into employee (name, birthday, email) values ('Germain Littlekit', '2021/06/06', 'glittlekitq@domainmarket.com');
insert into employee (name, birthday, email) values ('Dennet Ghiriardelli', '2021/04/24', 'dghiriardellir@washingtonpost.com');
insert into employee (name, birthday, email) values ('Shanan Street', '2021/02/06', 'sstreets@cnbc.com');
insert into employee (name, birthday, email) values ('Frederico Liddy', '2021/01/26', 'fliddyt@reddit.com');
insert into employee (name, birthday, email) values ('Octavia Beningfield', '2021/12/12', 'obeningfieldu@google.com.au');
insert into employee (name, birthday, email) values ('Blake Saffill', '2021/10/30', 'bsaffillv@nsw.gov.au');
insert into employee (name, birthday, email) values ('Gustavus Faye', '2021/10/30', 'gfayew@networksolutions.com');
insert into employee (name, birthday, email) values ('Trudey Rowlands', '2021/01/25', 'trowlandsx@gravatar.com');
insert into employee (name, birthday, email) values ('Anny Petzold', '2022/01/01', 'apetzoldy@soup.io');
insert into employee (name, birthday, email) values ('Charil Rideout', '2021/08/05', null);
insert into employee (name, birthday, email) values ('Cathy Mehew', '2021/07/24', 'cmehew10@globo.com');
insert into employee (name, birthday, email) values ('Zack Helgass', '2021/04/19', 'zhelgass11@last.fm');
insert into employee (name, birthday, email) values ('Alyss D''Alesco', '2021/02/25', 'adalesco12@t-online.de');
insert into employee (name, birthday, email) values ('Jannelle Budcock', '2021/10/21', 'jbudcock13@constantcontact.com');
insert into employee (name, birthday, email) values ('Brendin Vant', '2021/06/24', 'bvant14@dell.com');
insert into employee (name, birthday, email) values ('Dev Maddin', '2021/01/16', 'dmaddin15@cyberchimps.com');
insert into employee (name, birthday, email) values ('Petra Dog', '2021/06/08', 'pdog16@cargocollective.com');
insert into employee (name, birthday, email) values ('Marquita Stillman', '2021/07/25', 'mstillman17@mac.com');
insert into employee (name, birthday, email) values ('Grier Slevin', '2021/11/03', 'gslevin18@blogger.com');
insert into employee (name, birthday, email) values ('Carlye Arlow', '2021/06/17', 'carlow19@ning.com');
insert into employee (name, birthday, email) values ('Callie Muddle', '2021/12/14', 'cmuddle1a@posterous.com');
insert into employee (name, birthday, email) values ('Katerine Foran', '2021/12/26', 'kforan1b@drupal.org');
insert into employee (name, birthday, email) values ('Fanya Bilston', '2021/12/19', 'fbilston1c@joomla.org');
insert into employee (name, birthday, email) values ('Eduino Benner', '2021/09/24', 'ebenner1d@wikispaces.com');
```


3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```
UPDATE employee
SET name = 'Rick Grimes'
WHERE id = 5;	

UPDATE employee
SET birthday = '1958-07-25'
WHERE email LIKE 'eha%'';

UPDATE employee
SET email = 'mkiwitzd@ft.com'
WHERE birthday = '2021-12-21';

UPDATE employee
SET name = 'XXXXX YYYYY'
WHERE id > 45;

UPDATE employee
SET birthday = '2022-01-16'
WHERE name ILIKE 'e%n';
```

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```
DELETE FROM employee
WHERE name = 'Karlie Fines';	

DELETE FROM employee
WHERE id < 6;

DELETE FROM employee
WHERE email LIKE '%b%a%n%';

DELETE FROM employee
WHERE birthday > '2021-12-30';

DELETE FROM employee
WHERE name ILIKE '%y';
```

## Ödev 9

1. City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT city, country FROM city 
INNER JOIN country ON country.country_id = city.country_id;
```

2. Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT customer.first_name, customer.last_name, payment.payment_id FROM customer
INNER JOIN payment ON customer.store_id = payment.staff_id;
```

3. Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT customer.first_name, customer.last_name, rental.rental_id FROM rental
INNER JOIN customer ON customer.customer_id = rental.customer_id;
```











