# SQLBolt-Queries-Solutions

## Lesson 1

### Q1 Find the title of each film

SELECT title FROM movies;

### Q2 Find the director of each film 

SELECT director FROM movies;

### Q3 Find the title and director of each film

SELECT title,director FROM movies;

### Q4 Find the title and year of each film

SELECT title,year FROM movies;

### Q5 Find all the information about each film

SELECT * FROM movies;

## Lesson 2

### Q1 Find the movie with a row id of 6

SELECT * FROM movies WHERE id='6';

### Q2 Find the movies released in the years between 2000 and 2010 

SELECT * FROM movies WHERE year between 2000 and 2010;

### Q3 Find the movies not released in the years between 2000 and 2010

SELECT * FROM movies WHERE year NOT between 2000 and 2010;

### Q4 Find the first 5 Pixar movies and their release year

SELECT * FROM movies  LIMIT 5;

## Lesson 3

### Q1 Find all the Toy Story movies

SELECT * FROM movies WHERE title LIKE 'Toy Story%';

### Q2 Find all the movies directed by John Lasseter

SELECT * FROM movies WHERE director='John Lasseter';

### Q3 Find all the movies (and director) not directed by John Lasseter

SELECT * FROM movies WHERE director!='John Lasseter';

### Q4 Find all the WALL-* movies

SELECT * FROM movies WHERE title LIKE 'WALL%'

## Lesson 4

### Q1 List all directors of Pixar movies (alphabetically), without duplicates

SELECT DISTINCT director FROM movies ORDER BY director ASC;

### Q2 List the last four Pixar movies released (ordered from most recent to least)

SELECT * FROM movies ORDER BY year DESC LIMIT 4;

### Q3 List the first five Pixar movies sorted alphabetically

SELECT *  FROM movies ORDER BY title ASC LIMIT 5 ;

### Q4 List the next five Pixar movies sorted alphabetically

SELECT *  FROM movies ORDER BY title ASC LIMIT 5 OFFSET 5;

## Lesson 5  

### Q1 List all the Canadian cities and their populations

SELECT city,population FROM north_american_cities WHERE country='Canada';

### Q2 Order all the cities in the United States by their latitude from north to south

SELECT * FROM north_american_cities WHERE country='United States' ORDER BY latitude DESC;

### Q3 List all the cities west of Chicago, ordered from west to east

SELECT * FROM north_american_cities WHERE longitude<-87.69
ORDER BY longitude ASC;

### Q4 List the two largest cities in Mexico (by population)

SELECT * FROM North_american_cities WHERE country LIKE "Mexico"
ORDER BYpPopulation DESC LIMIT 2;

### Q5 List the third and fourth largest cities (by population) in the United States and their population

SELECT * FROM North_american_cities WHERE country LIKE "United States"
ORDER BY population DESC LIMIT 2 OFFSET 2;

## Lesson 6
