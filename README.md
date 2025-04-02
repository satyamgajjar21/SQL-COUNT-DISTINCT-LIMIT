# Hands-on Lab: COUNT, DISTINCT, LIMIT

## Estimated Time: 30 minutes

In this lab, you will learn a few useful expressions used with `SELECT` statements:
- **COUNT**: An aggregate function that retrieves the number of rows matching the query criteria.
- **DISTINCT**: Removes duplicate values from a specified result set and returns only unique values.
- **LIMIT**: Restricts the number of rows retrieved from the table.

---

## Software Used in This Lab
- **Datasette**: An open-source multi-tool for exploring and publishing data.

## Database Used in This Lab
- **SanFranciscoFilmLocations Database** (under PDDL: Public Domain Dedication and License)

---

## Objectives
After completing this lab, you will be able to:
- Retrieve the number of rows that match a query criterion.
- Remove duplicate values from a result set and return unique values.
- Restrict the number of rows retrieved from a table.

---

## Exploring the Database
Use Datasette to explore the `SanFranciscoFilmLocations` database:

### Steps:
1. Run the following SQL query to display all records:
    ```sql
    SELECT * FROM FilmLocations;
    ```
2. Click **Submit Query**.
3. Scroll through the table to examine its columns and rows.
4. The `FilmLocations` table includes the following attributes:
   - **Title**: Titles of the films
   - **ReleaseYear**: Time of public release
   - **Locations**: Filming locations in San Francisco
   - **FunFacts**: Interesting facts about the filming locations
   - **ProductionCompany**: Companies that produced the films
   - **Distributor**: Companies that distributed the films
   - **Director**: People who directed the films
   - **Writer**: People who wrote the films
   - **Actor1, Actor2, Actor3**: Lead actors in the films

---

## Using COUNT Statement

1. Count the number of records (rows) in `FilmLocations`:
    ```sql
    SELECT COUNT(*) FROM FilmLocations;
    ```
2. Count the number of locations where films written by "James Cameron" were shot:
    ```sql
    SELECT COUNT(Locations) FROM FilmLocations WHERE Writer='James Cameron';
    ```

---

## Using DISTINCT Statement

1. Retrieve distinct film titles:
    ```sql
    SELECT DISTINCT Title FROM FilmLocations;
    ```
2. Count distinct release years of films produced by "Warner Bros. Pictures":
    ```sql
    SELECT COUNT(DISTINCT ReleaseYear) FROM FilmLocations WHERE ProductionCompany='Warner Bros. Pictures';
    ```

---

## Using LIMIT Statement

1. Retrieve only the first 25 rows:
    ```sql
    SELECT * FROM FilmLocations LIMIT 25;
    ```
2. Retrieve 15 rows starting from row 11:
    ```sql
    SELECT * FROM FilmLocations LIMIT 15 OFFSET 10;
    ```

---

## Practice Exercises

### COUNT
1. Retrieve the number of locations of films directed by Woody Allen:
    ```sql
    SELECT COUNT(Locations) FROM FilmLocations WHERE Director='Woody Allen';
    ```
2. Retrieve the number of films shot at Russian Hill:
    ```sql
    SELECT COUNT(Title) FROM FilmLocations WHERE Locations='Russian Hill';
    ```
3. Retrieve the number of rows with a release year older than 1950:
    ```sql
    SELECT COUNT(*) FROM FilmLocations WHERE ReleaseYear < 1950;
    ```

### DISTINCT
1. Retrieve unique films released in the 21st century (2001 and onwards) along with their release years:
    ```sql
    SELECT DISTINCT Title, ReleaseYear FROM FilmLocations WHERE ReleaseYear >= 2001;
    ```
2. Retrieve distinct directors and their films shot at "City Hall":
    ```sql
    SELECT DISTINCT Title, Director FROM FilmLocations WHERE Locations='City Hall';
    ```
3. Retrieve the number of distributors who distributed films starring Clint Eastwood:
    ```sql
    SELECT COUNT(DISTINCT Distributor) FROM FilmLocations WHERE Actor1='Clint Eastwood';
    ```

### LIMIT
1. Retrieve the first 50 film titles:
    ```sql
    SELECT DISTINCT Title FROM FilmLocations LIMIT 50;
    ```
2. Retrieve the first 10 film titles released in 2015:
    ```sql
    SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 10;
    ```
3. Retrieve the next 3 film titles after the first 5 released in 2015:
    ```sql
    SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 3 OFFSET 5;
    ```

---

## Conclusion
Congratulations! You have completed this lab. You are now able to:
- Use `COUNT` to determine the number of entries in a database based on filtering conditions.
- Use `DISTINCT` to determine unique entries in a database based on filtering conditions.
- Use `LIMIT` to restrict the number of rows returned by a query.
- Combine these statements to execute more complex queries.

---

## Author(s)
- **Sandip Saha Joy**

### Other Contributor(s)
- **Abhishek Gagneja**

© IBM Corporation 2023. All rights reserved.
