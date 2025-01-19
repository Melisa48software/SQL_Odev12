# SQL_Odev12
lcw bootcamp sql 12.ödev reposudur.

-- 1. Film Tablosunda, Film Uzunluğu Ortalama Film Uzunluğundan Fazla Olan Filmleri Sıralamak
SELECT COUNT(*) AS total_movies_above_average_length
FROM film
WHERE length > (SELECT AVG(length) FROM film);

-- 2. Film Tablosunda, En Yüksek rental_rate Değerine Sahip Olan Filmleri Saymak
SELECT COUNT(*) AS total_movies_with_highest_rental_rate
FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);

-- 3. Film Tablosunda, En Düşük rental_rate ve En Düşük replacement_cost Değerlerine Sahip Filmleri Sıralamak
SELECT title, rental_rate, replacement_cost
FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);

-- 4. Payment Tablosunda, En Fazla Sayıda Alışveriş Yapan Müşterileri (customer) Sıralamak
SELECT customer_id, COUNT(*) AS total_payments
FROM payment
GROUP BY customer_id
ORDER BY total_payments DESC
LIMIT 1;

