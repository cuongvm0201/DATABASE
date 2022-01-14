**Bài_1**
```sql
SELECT actor.*
FROM actor
INNER JOIN film_actor ON actor.actor_id = film_actor.actor_id
INNER JOIN film ON film.film_id = film_actor.film_id
WHERE film.title = 'ACADEMY DINOSAUR'
```
---
---
---
**Bài_2_Cách 1**
```sql
SELECT film.title, film.description , film.release_year , film.length , film.rating, COUNT(film_actor.actor_id) AS so_dien_vien
FROM film
INNER JOIN film_actor ON film.film_id = film_actor.film_id
INNER JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE film.rating = 'G'
GROUP BY film.film_id

```
---
---
**Bài_2_Cách 2**
```sql		
SELECT film.title, film.description , film.release_year , film.length , film.rating, COUNT(film_actor.actor_id) AS so_dien_vien
FROM film
INNER JOIN film_actor ON film.film_id = film_actor.film_id
WHERE film_actor.film_id IN (SELECT film.film_id
			     FROM film 
			     WHERE film.rating = 'G')
GROUP BY film.film_id		
```
---
---
---
**Bài_3**
```sql
SELECT AVG(film.rental_rate) AS AVG_Rental_rate
FROM film
INNER JOIN film_actor ON film.film_id = film_actor.film_id
INNER JOIN actor ON film_actor.actor_id = actor.actor_id
WHERE actor.first_name = 'CHRISTIAN' AND actor.last_name = 'GABLE' 
```
