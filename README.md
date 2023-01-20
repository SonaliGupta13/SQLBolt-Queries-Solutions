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

### Q1 Find the domestic and international sales for each movie 

SELECT Title, International_sales, Domestic_sales FROM Movies 
JOIN Boxoffice ON Id=Movie_id;

### Q2 Show the sales numbers for each movie that did better internationally rather than domestically

SELECT Title, International_sales, Domestic_sales FROM Movies 
JOIN Boxoffice ON Id=Movie_id WHERE International_sales > Domestic_sales;

### Q3 List all the movies by their ratings in descending order

SELECT Title,Rating FROM Movies JOIN Boxoffice
ON ID=Movie_id ORDER BY Rating DESC;

## Lesson 7

### Q1 Find the list of all buildings that have employees

SELECT distinct building FROM employees;

### Q2 Find the list of all buildings and their capacity

SELECT building_name,capacity FROM buildings;

### Q3 List all buildings and the distinct employee roles in each building (including empty buildings)

SELECT DISTINCT Building_name, Role FROM Buildings 
LEFT JOIN employees ON building_name = building;

## Lesson 8

### Q1 Find the name and role of all employees who have not been assigned to a building

SELECT name,role FROM Employees LEFT JOIN Buildings
ON Building_name = Building WHERE Building IS NULL;

### Q2 Find the names of the buildings that hold no employees

SELECT * FROM Buildings LEFT JOIN Employees
ON Building_name = Building WHERE Building IS NULL;

## Lesson 9

### Q1 List all movies and their combined sales in millions of dollars 

SELECT Title, (Domestic_sales + International_sales)/1000000 As Total_Sales_Millions
FROM Movies LEFT JOIN Boxoffice ON Id=Movie_Id;

### Q2 List all movies and their ratings in percent

SELECT Title, Rating*10 as Percent FROM Movies
LEFT JOIN Boxoffice ON Id=Movie_Id;

### Q3 List all movies that were released on even number years

SELECT Title, Year FROM Movies LEFT JOIN Boxoffice ON Id=Movie_Id
WHERE Year % 2 = 0;

## Lesson 10

### Q1 Find the longest time that an employee has been at the studio

SELECT MAX(Years_employed) FROM Employees;

### Q2 For each role, find the average number of years employed by employees in that role

SELECT Role, AVG(Years_Employed)  FROM Employees GROUP BY Role;

### Q3 Find the total number of employee years worked in each building

SELECT Building, SUM(Years_Employed)  FROM Employees GROUP BY Building;

## Lesson 11

### Q1 Find the number of Artists in the studio (without a HAVING clause)

SELECT Role, COUNT(*) AS Number_of_Artists FROM Employees
WHERE Role = "Artist";

### Q2 Find the number of Employees of each role in the studio

SELECT Role, COUNT(*) as employee_count FROM Employees GROUP BY Role;

### Q3 Find the total number of years employed by all Engineers

SELECT Role, SUM(Years_Employed) FROM Employees
GROUP BY Role HAVING Role = "Engineer";

## Lesson 12

### Q1 Find the number of movies each director has directed

SELECT *, COUNT(Title) as movies_no FROM Movies GROUP BY Director;

### Q2 Find the total domestic and international sales that can be attributed to each director

SELECT Director, sum(Domestic_sales + International_Sales) as Total_Sales
FROM Movies LEFT JOIN Boxoffice ON Id = Movie_ID GROUP BY Director;

## Lesson 13

### Q1 Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)

INSERT INTO Movies VALUES (4, "Toy Story 4", "John Lasseter", 2023, 123);

### Q2 Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally.
Add the record to the BoxOffice table.

INSERT INTO Boxoffice VALUES (4, 8.7, 340000000, 270000000);

## Lesson 14

### Q1 The director for A Bug's Life is incorrect, it was actually directed by John Lasseter

UPDATE Movies SET Director = "John Lasseter" WHERE Id = 2;

### Q2 The year that Toy Story 2 was released is incorrect, it was actually released in 1999

UPDATE Movies SET Year = "1999" WHERE Id = 3;

### Q3 Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich

UPDATE Movies SET Title = "Toy Story 3", Director = "Lee Unkrich" WHERE Id = 11;

##  Lesson 15

### Q1 This database is getting too big, lets remove all movies that were released before 2005.

DELETE FROM Movies WHERE Year < 2005;

### Q2 Andrew Stanton has also left the studio, so please remove all movies directed by him.

DELETE FROM Movies WHERE Director = "Andrew Stanton";

## Lesson 16

### Q1 Create a new table named Database with the following columns:
– Name A string (text) describing the name of the database
– Version A number (floating point) of the latest version of this database
– Download_count An integer count of the number of times this database was downloaded
This table has no constraints.

CREATE TABLE Database (
    Name TEXT,
    Version FLOAT,
    Download_Count INTEGER);
    
## Lesson 17

### Q1 Add a column named Aspect_ratio with a FLOAT data type to store the aspect-ratio each movie was released in.

ALTER TABLE Movies ADD COLUMN Aspect_ratio FLOAT DEFAULT 3;

### Q2 Add another column named Language with a TEXT data type to store the language that the movie was released in.
Ensure that the default for this language is English.

ALTER TABLE Movies ADD COLUMN Language TEXT DEFAULT "English";

## Lesson 18

### Q1 We've sadly reached the end of our lessons, lets clean up by removing the Movies table

DROP TABLE Movies;

### Q2 And drop the BoxOffice table as well

DROP TABLE BoxOffice;
  
  

