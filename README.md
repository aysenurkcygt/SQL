# SQL (Patika.dev Eğitimi)

## ÖDEV 1

- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

SELECT title and description FROM film;

- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

SELECT * FROM film WHERE length > 60 AND length < 75;

- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

SELECT * FROM film WHERE rental_rate = 0,99 AND replacement_cost = 12,99 OR replacement_cost = 28,99; 

- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

SELECT * FROM customer WHERE first_name = 'Mary';

- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

SELECT * FROM film WHERE NOT length > 50 AND (rental_rate != 2,99 OR rental_rate != 4,99);

## ÖDEV 2

- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;

- actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick','Ed');

- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT * FROM film WHERE rental_rate IN (0.99,2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);

## ÖDEV 3

- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

SELECT country FROM country WHERE country LIKE 'A%a';

- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

SELECT country FROM country WHERE country LIKE '_____%n';

- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

SELECT title FROM film WHERE title ILIKE '%t%t%t%t';

- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

SELECT * FROM film WHERE title LIKE 'C%' AND length>90 AND rental_rate = 2.99;
  
## ÖDEV 4

- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

SELECT DISTINCT replacement_cost FROM film;

- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

SELECT COUNT (DISTINCT replacement_cost) FROM film;

- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

SELECT COUNT (*) FROM film WHERE title LIKE 'T%' AND rating='G';

- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

SELECT COUNT (*) FROM country  WHERE country LIKE '_____';

- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

SELECT COUNT (*) FROM city WHERE city ILIKE '%r'


## ÖDEV 5

- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

SELECT title FROM film WHERE title LIKE '%n'ORDER BY length DESC LIMIT 5;

- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

SELECT title FROM film WHERE title LIKE '%n' ORDER BY length ASC OFFSET 5 LIMIT 10;

- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;

## ÖDEV 6

- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

SELECT AVG(rental_rate) FROM film;

- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

SELECT COUNT (title) FROM film WHERE title LIKE 'C%';

- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

SELECT MAX(length) FROM film WHERE rental_rate=0.99;

- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

SELECT COUNT (DISTINCT replacement_cost) FROM film WHERE length>150

## ÖDEV 7

- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

SELECT rating FROM film GROUP BY rating;

- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

SELECT replacement_cost, COUNT(title) FROM film GROUP BY replacement_cost HAVING COUNT (*) >50;

- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;

- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

SELECT country_id, COUNT (city) FROM city GROUP BY country_id ORDER BY COUNT(city) DESC LIMIT 1;

## ÖDEV 8

- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

CREATE TABLE employee(
	id SERIAL PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	birthday DATE,
	email VARCHAR(100)
);
select * from employee;

- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim. 

insert into MOCK_DATA (id, first_name, birthday, email) values (1, 'Sonnnie Ranson', '16.05.2022', 'sranson0@sakura.ne.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (2, 'Brok Gierke', '22.05.2022', 'bgierke1@miitbeian.gov.cn');
insert into MOCK_DATA (id, first_name, birthday, email) values (3, 'Merill Kummerlowe', '19.09.2022', 'mkummerlowe2@cbc.ca');
insert into MOCK_DATA (id, first_name, birthday, email) values (4, 'Douglass Kennion', '22.04.2022', 'dkennion3@domainmarket.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (5, 'Nadean Borborough', '11.01.2023', 'nborborough4@smugmug.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (6, 'Babita Duddan', '24.10.2022', 'bduddan5@scribd.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (7, 'Melitta Springford', '20.05.2022', 'mspringford6@army.mil');
insert into MOCK_DATA (id, first_name, birthday, email) values (8, 'Dolf Dodgshun', '20.11.2022', 'ddodgshun7@rakuten.co.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (9, 'Caleb Mouan', '22.01.2023', 'cmouan8@shop-pro.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (10, 'Archibold Leger', '21.05.2022', 'aleger9@java.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (11, 'Talbot Kunat', '23.04.2022', 'tkunata@netscape.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (12, 'See Hugh', '26.04.2022', 'shughb@networkadvertising.org');
insert into MOCK_DATA (id, first_name, birthday, email) values (13, 'Rene Tithecott', '03.08.2022', 'rtithecottc@canalblog.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (14, 'Bobby Le Noir', '07.01.2023', 'bled@rakuten.co.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (15, 'Tobi D''Cruze', '15.02.2022', 'tdcruzee@dot.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (16, 'Berke Cammacke', '01.11.2022', 'bcammackef@deviantart.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (17, 'Mill Van der Son', '23.05.2022', 'mvang@reuters.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (18, 'Prince Succamore', '23.04.2022', 'psuccamoreh@oracle.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (19, 'Tessi Ellin', '28.01.2023', 'tellini@plala.or.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (20, 'Oralla Pimlett', '12.08.2022', 'opimlettj@wikia.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (21, 'Cyrillus Clute', '12.12.2022', 'cclutek@istockphoto.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (22, 'Lock Allibone', '21.04.2022', 'lallibonel@biblegateway.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (23, 'Hansiain Addington', '22.11.2022', 'haddingtonm@phoca.cz');
insert into MOCK_DATA (id, first_name, birthday, email) values (24, 'Charmane Ganiclef', '14.03.2022', 'cganiclefn@zdnet.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (25, 'Marsha Jeandet', '18.09.2022', 'mjeandeto@bloomberg.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (26, 'Lydon Jessard', '13.11.2022', 'ljessardp@addtoany.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (27, 'Terrye Filippucci', '06.07.2022', 'tfilippucciq@yahoo.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (28, 'Hyacinthe Rupel', '08.04.2022', 'hrupelr@ft.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (29, 'Chandra Mitchely', '25.02.2022', 'cmitchelys@illinois.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (30, 'Catlee Lanney', '06.09.2022', 'clanneyt@discovery.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (31, 'Dione Wallege', '16.12.2022', 'dwallegeu@youtu.be');
insert into MOCK_DATA (id, first_name, birthday, email) values (32, 'Denyse Batson', '06.10.2022', 'dbatsonv@house.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (33, 'Aleen Rappport', '19.10.2022', 'arappportw@so-net.ne.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (34, 'Caryn Ludlamme', '17.11.2022', 'cludlammex@sun.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (35, 'Ardelle Kobera', '27.03.2022', 'akoberay@bizjournals.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (36, 'Wenonah Wytchard', '24.03.2022', 'wwytchardz@unicef.org');
insert into MOCK_DATA (id, first_name, birthday, email) values (37, 'Ardenia Terran', '22.02.2022', 'aterran10@cdbaby.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (38, 'Zacharia Albasini', '21.06.2022', 'zalbasini11@flickr.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (39, 'Isador Bamlet', '09.09.2022', 'ibamlet12@dailymotion.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (40, 'Brendis Pickrell', '15.01.2023', 'bpickrell13@goo.ne.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (41, 'Arlena Money', '09.10.2022', 'amoney14@utexas.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (42, 'Mohammed Maciaszczyk', '16.12.2022', 'mmaciaszczyk15@sbwire.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (43, 'Lamond Rowan', '13.05.2022', 'lrowan16@reddit.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (44, 'Malissa Riddiford', '15.09.2022', 'mriddiford17@virginia.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (45, 'Sarena Cammack', '26.10.2022', 'scammack18@statcounter.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (46, 'Hilarius Morecomb', '08.01.2023', 'hmorecomb19@yahoo.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (47, 'Thorpe McGow', '08.08.2022', 'tmcgow1a@upenn.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (48, 'Chickie McGirl', '07.02.2022', 'cmcgirl1b@senate.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (49, 'Dolli Gooder', '28.07.2022', 'dgooder1c@aol.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (50, 'Jolene Chateau', '28.03.2022', 'jchateau1d@dailymail.co.uk');

select * from employee;

- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

UPDATE employee
SET name = 'Deneme'
WHERE name LIKE 'S%'
RETURNING *;

UPDATE employee
SET birthday = '22.03.1907'
WHERE birthday = '07.02.2022'
RETURNING *;

UPDATE employee
SET name = REPLACE(name, 't','X')
WHERE name LIKE '%t%'
RETURNING *;

UPDATE employee
SET email = REPLACE(email, '@ödev.com','@patika.com.tr')
WHERE email LIKE '%@dgooder1c@aol.com'
RETURNING *;

UPDATE employee
SET id = id + 100
WHERE id > 30
RETURNING *;

select * from employee;

- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

DELETE FROM employee
WHERE name = 'Sonnnie Ranson'
RETURNING *;

DELETE FROM employee
WHERE id < 10
RETURNING *;

DELETE FROM employee
WHERE email LIKE 'a%'
RETURNING *;

DELETE FROM employee
WHERE birthday = '07.02.2022'
RETURNING *;

SELECT * FROM employee;

