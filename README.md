# SQLODEV12

SELECT COUNT(*) FROM film
WHERE length > 
(
SELECT AVG(length) FROM film
);

SELECT COUNT(*) FROM film
WHERE rental_rate = ANY 
(
SELECT MAX(rental_rate) FROM film
);

SELECT * FROM film
WHERE rental_rate = ANY 
(
SELECT MIN(rental_rate) FROM film
)
UNION
SELECT * FROM film
WHERE replacement_cost = ANY 
(
SELECT MIN(replacement_cost) FROM film
);

SELECT customer_id, COUNT(customer_id) FROM payment
GROUP BY customer_id
ORDER BY COUNT(customer_id) DESC;
