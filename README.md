## Create a query to find all movies in the Sci-Fi genre.
select * FROM movies WHERE Genre="Sci-Fi";

## Create a query to find all films that scored at least a 6.5 on IMDB.
select * FROM movies WHERE IMDBScore >= 6.5;

## For parents who have young kids, but who don't want to sit through long children's movies, create a query to find all of the movies rated G or PG that are less than 100 minutes long.
select * FROM movies WHERE Runtime < 100 AND Rating ="G" OR Rating = "PG";

## Create a query to show the average runtimes of movies scoring below a 7.5 on imdb, grouped by their respective genres.
select Genre, AVG(Runtime) FROM movies WHERE IMDBScore < 7.5 GROUP BY Genre;

## There's been a data entry mistake; Starship Troopers is actually rated R, not PG-13. Create a query that finds the movie by its title and changes its rating to R
update movies SET Rating ="R" WHERE Title="Starship Troopers";

## Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.
select MovieID, Rating FROM movies WHERE Genre IN ("Horror", "Documentary");

## This time let's find the average, maximum, and minimum IMDB score for movies of each rating.
select Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movies GROUP BY Rating;

## That last query isn't very informative for ratings that only have 1 entry. Use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.
select Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movies GROUP BY Rating HAVING COUNT(*)


# *** STRETCH GOAL ***
## Alter table and add a new column for the Year created.
ALTER TABLE moviesTable2
ADD Year INT UNSIGNED NOT NULL;

select * from moviesTable2;

## Update the values of the movies to reflect the Year Created.
UPDATE moviesTable2 
SET Year = 1986
WHERE MovieID = 1;

UPDATE moviesTable2 
SET Year = 1998
WHERE MovieID = 10;

UPDATE moviesTable2 
SET Year = 1995
WHERE MovieID = 11;

UPDATE moviesTable2 
SET Year = 2015
WHERE MovieID = 13;

UPDATE moviesTable2 
SET Year = 1997
WHERE MovieID = 14;

UPDATE moviesTable2 
SET Year = 2008
WHERE MovieID = 15;

UPDATE moviesTable2 
SET Year = 1987
WHERE MovieID = 16;

UPDATE moviesTable2 
SET Year = 2001
WHERE MovieID = 17;

## Find all movies whose titles end with the letter "A".
SELECT title FROM moviesTable2 WHERE title LIKE'%A';