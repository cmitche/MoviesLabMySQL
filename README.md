# Movies Lab MySQL

## 1. Create a query to find all movies in the Sci-Fi genre.
select * FROM movies WHERE Genre="Sci-Fi";

## 2. Create a query to find all films that scored at least a 6.5 on IMDB.
select * FROM movies WHERE IMDBScore >= 6.5;

## 3. For parents who have young kids, but who don't want to sit through long children's movies, create a query to find all of the movies rated G or PG that are less than 100 minutes long.
select * FROM movies WHERE Runtime < 100 AND Rating ="G" OR Rating = "PG";

## 4. Create a query to show the average runtimes of movies scoring below a 7.5 on imdb, grouped by their respective genres.
select Genre, AVG(Runtime) FROM movies WHERE IMDBScore < 7.5 GROUP BY Genre;

## 5. There's been a data entry mistake; Starship Troopers is actually rated R, not PG-13. Create a query that finds the movie by its title and changes its rating to R
update movies SET Rating ="R" WHERE Title="Starship Troopers";

## 6. Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.
select MovieID, Rating FROM movies WHERE Genre IN ("Horror", "Documentary");

## 7. This time let's find the average, maximum, and minimum IMDB score for movies of each rating.
select Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movies GROUP BY Rating;

## 8. That last query isn't very informative for ratings that only have 1 entry. Use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.
select Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movies GROUP BY Rating HAVING COUNT(*) > 1;


# *** STRETCH GOAL ***
## Alter table and add a new column for the Year created.
ALTER TABLE movies
ADD Year INT UNSIGNED NOT NULL;


## Update the values of the movies to reflect the Year created.
UPDATE movies 
SET Year = 1986
WHERE MovieID = 1;

UPDATE movies 
SET Year = 1998
WHERE MovieID = 2;

UPDATE movies 
SET Year = 1995
WHERE MovieID = 3;

UPDATE movies 
SET Year = 2015
WHERE MovieID = 4;

UPDATE movies 
SET Year = 1997
WHERE MovieID = 5;

UPDATE movies 
SET Year = 2008
WHERE MovieID = 6;

UPDATE movies 
SET Year = 1987
WHERE MovieID = 7;

UPDATE movies 
SET Year = 2001
WHERE MovieID = 8;

## Find all movies whose titles END with the letter "A".
SELECT title FROM movies WHERE title LIKE'%A';
