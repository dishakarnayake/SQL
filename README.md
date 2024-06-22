# 🧭: LeetCode SQL Question and Answer - 
-https://github.com/dishakarnayake/SQL.git
  
##  :dart: `Difficulty Level - Easy`
  
 ### Q.1 Write a solution to find the ids of products that are both low-fat and recyclable. Return the result table in any order.
 
   `Table Name - Product`
   
| Column Name | Type |
| ----------- | ---  |
| product_id  | int  |
| low_fats    | enum |
| recyclable  | enum |

product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

The result format is in the following example.

**Example 1:** 

**Input:**

Products table:
| product_id   | low_fats  | recyclable  |
| ----------- | ---------  | ----------  |
|      0      |  Y  | N |
|      1      |  Y  | Y |
|      2      |  N  | Y |
|      3      |  Y  | Y |
|      4      |  N  | N |

 ###  Solution - 
    
    SELECT product_id
    FROM products 
    WHERE low_fats = "Y" AND recyclable = "Y";

**Output:**

| product_id |
|----------- |
| 1 |
| 3 |

 ### Q.2 Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.
 
   `Table Name - Customer `
  
| Column Name | Type | 
| ----------- | ---  |
| id          | int  |
| name        | varchar |
| referee_id    | int |

In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

The result format is in the following example.

**Example 1:** 

**Input:**

Customer table:
| id    | name   | referee_id   |
| ----------- | ---------  | ----------  |
|      1      |  Will   | null        |
|      2      |  Jane   | null        |
|      3      |  Alex   | 2           |
|      4      |  Bill   | null        |
|      5      |  Zack   | 1           |
|      6      |  Mark   |  2          |
 ###  Solution - 
    
    SELECT name 
    FROM customer
    WHERE referee_id != 2 OR referee_id is null;

**Output:**

| name |
|----------- |
| Will  |
| Jane  |
| Bill  |
| Zack  |

 ### Q.3 A country is big if: it has an area of at least three million (i.e., 3000000 km2), or it has a population of at least twenty-five million (i.e., 25000000). Write a solution to find the name, population, and area of the big countries. Return the result table in any order.
 
   `Table Name - World `
  
| Column Name | Type | 
| ----------- | ---  |
| name        | int  |
| continent   | varchar |
| area     | int |
|population| int |
| gdp |  bigint  |

name is the primary key (column with unique values) for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.

The result format is in the following example.

**Example 1:** 

**Input:**

World table:
| name    | continent   | area   | population | gdp |
| ----------- | ---------  | ----------  | ---| ---|
|   Afghanistan       |  Asia         | 652230          |25500100   |20343000000  |
|      Albania           |  Europe       | 28748           |2831741    |12960000000  |
|      Algeria           |  Africa       | 2381741            |37100000   |188681000000 |
|      Andorra           |  Europe       | 468             |78115      |3712000000   |
|      Angola            |  Africa       | 1246700            |20609294   |100990000000 |

 ###  Solution - 
    
    SELECT name , population , area
    FROM world
    WHERE area >= 3000000 or population >= 25000000 ;

**Output:**

| name | population | area |
|----------- |------|------|
| Afghanistan   |25500100   |652230  |
| Algeria       |37100000   |2381741 |

 ### Q.4 Write a solution to find all the authors that viewed at least one of their own articles. Return the result table sorted by id in ascending order.
 
   `Table Name - Views `
  
| Column Name | Type | 
| ----------- | ---  |
| article_id            | int  |
| author_id        | int |
| viewer_id          | int |
|view_date     | date |

There is no primary key (column with unique values) for this table, the table may have duplicate rows.
Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.

The result format is in the following example.

**Example 1:** 

**Input:**

Views table:
| article_id     | author_id    | viewer_id    | view_date   | 
| ----------- | ---------  | ----------  | --- |
|   1       |  3         | 5          |2019-08-01   |
|      1           |  3       | 6           |2019-08-02    |
|      2           |  7       | 7            |2019-08-01   |
|      2           |  7       | 6             |2019-08-02       |
|      4            |  7       | 1            |2019-07-22   |
|      3            |  4       | 4            |2019-07-21   |
|      3            |  4       | 4            |2019-07-21   |

 ###  Solution - 
    
    SELECT DISTINCT author_id as id 
    FROM Views
    WHERE author_id=viewer_id
    ORDER BY author_id;

**Output:**

| id | 
|----------- |
| 4   |
| 7       |

 ### Q.5 Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15. Return the result table in any order.
 
   `Table Name - Tweets `
  
| Column Name | Type | 
| ----------- | ---  |
| tweet_id      | int  |
| content        | varchar |

tweet_id is the primary key (column with unique values) for this table.
This table contains all the tweets in a social media app.

The result format is in the following example.

**Example 1:** 

**Input:**

Tweets table:
| tweet_id    | content    | 
| ----------- | ---------  | 
|   1         |  Vote for Biden   | 
|      2      |  Let us make America great again!  | 


 ###  Solution - 
    
    SELECT tweet_id 
    FROM Tweets
    WHERE len(content)>15;

**Output:**

| tweet_id | 
|----------- |
| 2   |

 ### Q.6 Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null. Return the result table in any order.
 
   `Table Name - Employees `
  
| Column Name | Type | 
| ----------- | ---  |
| id      | int  |
| name        | varchar |

id is the primary key (column with unique values) for this table.
Each row of this table contains the id and the name of an employee in a company.

   `Table Name - EmployeeUNI `
  
| Column Name | Type | 
| ----------- | ---  |
| id      | int  |
| unique_id             | int |

(id, unique_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.

The result format is in the following example.

**Example 1:** 

**Input:**

Employees  table:
| id    | name    | 
| ----------- | ---------  | 
|   1         | Alice      | 
|      7      |  Bob       | 
|      11     |  Meir      | 
|      90     | Winston   |
|      3      | Jonathan   | 

EmployeeUNI   table:
| id     | unique_id     | 
| -----------| ---------| 
|   3        | 1         | 
|      11    |  2       | 
|      90    | 3        |


 ###  Solution - 
    
    SELECT eU.unique_id, e.name 
    FROM Employees as e
    LEFT JOIN EmployeeUNI as eU ON e.id=eU.id;

**Output:**

| unique_id | name     |
|-----------|----------|
| null      |Alice     |
| null      |Bob       |
| 2         |Meir      |
| 3         |Winston   |
| 1         |Jonathan  |

 ### Q.7 Write a solution to report the product_name, year, and price for each sale_id in the Sales table. Return the resulting table in any order.
 
   `Table Name - Sales `
  
| Column Name | Type | 
| ----------- | ---  |
| sale_id           | int  |
| product_id          | int |
| year                  | int |
| quantity              | int |
| price                 | int |

(sale_id, year) is the primary key (combination of columns with unique values) of this table.
product_id is a foreign key (reference column) to Product table.
Each row of this table shows a sale on the product product_id in a certain year.
Note that the price is per unit.

   `Table Name - Product `
  
| Column Name | Type | 
| ----------- | ---  |
| product_id         | int  |
| product_name              | varchar |

product_id is the primary key (column with unique values) of this table.
Each row of this table indicates the product name of each product.

The result format is in the following example.

**Example 1:** 

**Input:**

Sales   table:
| sale_id      | product_id      | year |quantity |price |
| -----------| ---------| ---|--|--|
|   1        | 100         |2008 |10|5000|
|      2    |  100       | 2009|12|5000|
|      3    | 200        |2011|15|9000|

Product  table:

| product_id       | product_name       | 
| -----------| ---------| 
|   100        | Nokia               |
|      200    |  Apple               | 
|      300    | Samsung              |

 ###  Solution - 
    
    SELECT product_name, year, price 
    FROM Sales as s
    INNER JOIN Product as p ON s.product_id=p.product_id;

**Output:**

| product_name  | year       |price|
|-----------|----------|--|
| Nokia              |2008       |5000  |
| Nokia              |2009         |5000  |
| Apple                 |2011        |9000  |

 ### Q.8 Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits. Return the result table sorted in any order.
 
   `Table Name - Visits `
  
| Column Name | Type | 
| ----------- | ---  |
| visit_id               | int  |
| customer_id           | int |

visit_id is the column with unique values for this table.
This table contains information about the customers who visited the mall.

   `Table Name - Transactions `
  
| Column Name | Type | 
| ----------- | ---  |
| transaction_id  | int  |
| visit_id        | int |
| amount          | int |

transaction_id is the column with unique values for this table.
This table contains information about the transactions made during the visit_id.

The result format is in the following example.

**Example 1:** 

**Input:**

Visits table:
| visit_id       | customer_id       | 
| -----------| ---------| 
|   1        | 23                   |
|   2        |  9                  |
|   4        | 30                  |
|   5       | 54                   |
|   6       |  96                 |
|   7      | 54                  |
|   8       | 54     |


Transactions  table:

| transaction_id        | visit_id        |amount  |
| -----------| ---------| ----|
|   2        | 5               |310|
|      3    |  5               |300 |
|      9    | 5              |200|
|      12    |  1               | 910|
|      13    | 2              |970|

 ###  Solution - 
    
    SELECT v.customer_id, count(v,visit_id) as count_no_trans
    FROM Visit as v
    LEFT JOIN Transactions as t ON v.visit_id=t.visit_id
    WHERE t.visit_id is null
    GROUP BY v.customer_id;

**Output:**

| customer_id   | count_no_trans        |
|-----------|----------|
| 54              |2       |
| 30              |1         |
| 96                 |1        |

 ### Q.9 Write a solution to find all dates' Id with higher temperatures compared to its previous dates (yesterday). Return the result table in any order.
 
   `Table Name - Weather `
  
| Column Name | Type | 
| ----------- | ---  |
| id  | int  |
| recordDate        | date |
| temperature          | int |

id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.

The result format is in the following example.

**Example 1:** 

**Input:**



Weather table:

| id        | recordDate        |temperature  |
| -----------| ---------| ----|
|   1        | 2015-01-01           |10|
|      2    |  2015-01-02            |25 |
|      3    | 2015-01-03            |20|
|      4    | 2015-01-04               | 30|

 ###  Solution - 
    
    WITH cte AS
    (SELECT id, temperature, LAG(temperature) OVER(ORDER BY recordDate) as preious_tempure
    FROM Weather )
    SELECT id
    FROM cte
    WHERE preious_tempure IS NOT NULL AND temperature > preious_tempure

**Output:**

| customer_id  | 
|-----------|
| 2         |
| 4        |

 ### Q.10 There is a factory website that has several machines each running the same number of processes. Write a solution to find the average time each machine takes to complete a process. The time to complete a process is the 'end' timestamp minus the 'start' timestamp. The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run. The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places. Return the result table in any order.
 
   `Table Name - Activity  `
  
| Column Name | Type | 
| ----------- | ---  |
| machine_id  | int  |
| process_id        | date |
| activity_type            | enum |
| timestamp                  | float |

The table shows the user activities for a factory website.
(machine_id, process_id, activity_type) is the primary key (combination of columns with unique values) of this table.
machine_id is the ID of a machine.
process_id is the ID of a process running on the machine with ID machine_id.
activity_type is an ENUM (category) of type ('start', 'end').
timestamp is a float representing the current time in seconds.
'start' means the machine starts the process at the given timestamp and 'end' means the machine ends the process at the given timestamp.
The 'start' timestamp will always be before the 'end' timestamp for every (machine_id, process_id) pair.
The result format is in the following example.

**Example 1:** 

**Input:**

Weather table:

| machine_id         | process_id         |activity_type   |timestamp |
| -----------| ---------| ----|---|
| 0          | 0          | start         | 0.712     |
| 0          | 0          | end           | 1.520     |
| 0          | 1          | start         | 3.140     |
| 0          | 1          | end           | 4.120     |
| 1          | 0          | start         | 0.550     |
| 1          | 0          | end           | 1.550     |
| 1          | 1          | start         | 0.430     |
| 1          | 1          | end           | 1.420     |
| 2          | 0          | start         | 4.100     |
| 2          | 0          | end           | 4.512     |
| 2          | 1          | start         | 2.500     |
| 2          | 1          | end           | 5.000     |

 ###  Solution - 
    
    select a.machine_id, round(avg(b.timestamp - a.timestamp),3) as processing_time
    from activity as a 
    join activity as b
    on a.machine_id = b.machine_id and a.process_id = b.process_id
    and a.activity_type = 'start' and b.activity_type = 'end'
    group by a.machine_id;

**Output:**

| machine_id | processing_time |
|-----------|--|
| 0          | 0.894           |
| 1          | 0.995           |
| 2          | 1.456           |

 ### Q.11 Write a solution to report the name and bonus amount of each employee with a bonus less than 1000. Return the result table in any order.
 
   `Table Name - Employee  `
  
| Column Name | Type | 
| ----------- | ---  |
| empId         | int  |
| name          | varchAR|
| supervisor   | int |
| salary       | int |

empId is the column with unique values for this table.
Each row of this table indicates the name and the ID of an employee in addition to their salary and the id of their manager.

   `Table Name - Bonus  `
  
| Column Name | Type | 
| ----------- | ---  |
| empId       | int  |
| bonus       | int  |

empId is the column of unique values for this table.
empId is a foreign key (reference column) to empId from the Employee table.
Each row of this table contains the id of an employee and their respective bonus.

The result format is in the following example.

**Example 1:** 

**Input:**

Employee  table:

| empId | name   | supervisor | salary |
| -----------| ---------| ----|---|
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |

Bonus  table:

| empId | bonus |
|-----------|---------| 
| 2     | 500   |
| 4     | 2000  |

 ###  Solution - 
    
    select e.name, b.bonus 
    from Employee as e
    left join Bonus as b on e.empId=b.empId
    where bonus <1000 or bonus is null;

**Output:**

| name | bonus |
|-----------|--|
| Brad | null  |
| John | null  |
| Dan  | 500   |

 ### Q.12 Write a solution to find the number of times each student attended each exam. Return the result table ordered by student_id and subject_name.
 
   `Table Name - Students  `
  
| Column Name | Type | 
| ----------- | ---  |
| student_id    | int     |
| student_name  | varchar |

student_id is the primary key (column with unique values) for this table.
Each row of this table contains the ID and the name of one student in the school.
 
   `Table Name - Subjects  `
  
| Column Name | Type | 
| ----------- | ---  |
| subject_name | varchar |

subject_name is the primary key (column with unique values) for this table.
Each row of this table contains the name of one subject in the school.

  `Table Name - Examinations  `
  
| Column Name | Type | 
| ----------- | ---  |
| student_id   | int     |
| subject_name | varchar |

There is no primary key (column with unique values) for this table. It may contain duplicates.
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.
 

**Example 1:** 

**Input:**

Students  table:

| student_id | student_name |
| -----------| ---------| 
| 1          | Alice        |
| 2          | Bob          |
| 13         | John         |
| 6          | Alex         |

Subjects   table:

| subject_name |
|-----------|
| Math         |
| Physics      |
| Programming  |

Examinations    table:

| student_id | subject_name |
|-----------|-------------|
| 1          | Math         |
| 1          | Physics      |
| 1          | Programming  |
| 2          | Programming  |
| 1          | Physics      |
| 1          | Math         |
| 13         | Math         |
| 13         | Programming  |
| 13         | Physics      |
| 2          | Math         |
| 1          | Math         |

 ###  Solution - 
    
    select s.student_id,
           s.student_name,
           sub.subject_name,
           count(e.subject_name) as attended_exams
    from Students as s
    cross join Subjects as sub
    left join Examinations as e on s.student_id=e.student_id and sub.subject_name=e.subject_name
    group by s.student_id, s.student_name, sub.subject_name
    order by s.student_id, s.student_name;

**Output:**

| student_id | student_name | subject_name | attended_exams |
|-----------|--             |---           |--              |
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |
| 6          | Alex         | Math         | 0              |
| 6          | Alex         | Physics      | 0              |
| 6          | Alex         | Programming  | 0              |
| 13         | John         | Math         | 1              |
| 13         | John         | Physics      | 1              |
| 13         | John         | Programming  | 1              |

 ### Q.13 Write a solution to report the movies with an odd-numbered ID and a description that is not "boring". Return the result table ordered by rating in descending order.
 
   `Table Name - Cinema   `
  

| Column Name    | Type     |
|----------------|----------|
| id             | int      |
| movie          | varchar  |
| description    | varchar  |
| rating         | float    |

id is the primary key (column with unique values) for this table.
Each row contains information about the name of a movie, its genre, and its rating.
rating is a 2 decimal places float in the range [0, 10]


The result format is in the following example.

**Example 1:** 

**Input:**

Cinema table:

| id | movie      | description | rating |
|----|------------|-------------|--------|
| 1  | War        | great 3D    | 8.9    |
| 2  | Science    | fiction     | 8.5    |
| 3  | irish      | boring      | 6.2    |
| 4  | Ice song   | Fantacy     | 8.6    |
| 5  | House card | Interesting | 9.1    |

 ###  Solution - 
    
    select * from Cinema
    where id%2!=0 and description != 'boring'
    order by rating desc;

 ### Q.14 Write a solution to find the average selling price for each product. average_price should be rounded to 2 decimal places. Return the result table in any order.
 
 Table: Prices

| Column Name   | Type    |
+---------------+---------+
| product_id    | int     |
| start_date    | date    |
| end_date      | date    |
| price         | int     |

(product_id, start_date, end_date) is the primary key (combination of columns with unique values) for this table.
Each row of this table indicates the price of the product_id in the period from start_date to end_date.
For each product_id there will be no two overlapping periods. That means there will be no two intersecting periods for the same product_id.
 
Table: UnitsSold

| Column Name   | Type    |
+---------------+---------+
| product_id    | int     |
| purchase_date | date    |
| units         | int     |

This table may contain duplicate rows.
Each row of this table indicates the date, units, and product_id of each product sold. 
 
The result format is in the following example.

Example 1:

Input: 

Prices table:

| product_id | start_date | end_date   | price  |
|------------|------------|------------|--------|
| 1          | 2019-02-17 | 2019-02-28 | 5      |
| 1          | 2019-03-01 | 2019-03-22 | 20     |
| 2          | 2019-02-01 | 2019-02-20 | 15     |
| 2          | 2019-02-21 | 2019-03-31 | 30     |

UnitsSold table:

| product_id | purchase_date | units |
|------------|---------------|-------|
| 1          | 2019-02-25    | 100   |
| 1          | 2019-03-01    | 15    |
| 2          | 2019-02-10    | 200   |
| 2          | 2019-03-22    | 30    |

 ###  Solution - 
    
    select * from Cinema
    where id%2!=0 and description != 'boring'
    order by rating desc;
    
Output: 

| product_id | average_price |
|------------|---------------|
| 1          | 6.96          |
| 2          | 16.96         |

 ### Q.15 Write an SQL query that reports the average experience years of all the employees for each project, rounded to 2 digits. Return the result table in any order.
 
Table: Project

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| project_id  | int     |
| employee_id | int     |
+-------------+---------+
(project_id, employee_id) is the primary key of this table.
employee_id is a foreign key to Employee table.
Each row of this table indicates that the employee with employee_id is working on the project with project_id.
 

Table: Employee

+------------------+---------+
| Column Name      | Type    |
+------------------+---------+
| employee_id      | int     |
| name             | varchar |
| experience_years | int     |
+------------------+---------+
employee_id is the primary key of this table. It's guaranteed that experience_years is not NULL.
Each row of this table contains information about one employee.

The result format is in the following example.

Example 1:

Input: 

Project table:

| project_id  | employee_id |
+-------------+-------------+
| 1           | 1           |
| 1           | 2           |
| 1           | 3           |
| 2           | 1           |
| 2           | 4           |

Employee table:

| employee_id | name   | experience_years |
+-------------+--------+------------------+
| 1           | Khaled | 3                |
| 2           | Ali    | 2                |
| 3           | John   | 1                |
| 4           | Doe    | 2                |
+-------------+--------+------------------+

 ###  Solution - 
    
    select p.project_id, round(avg(e.experience_years*1.0),2) as average_years 
    from Project as p
    left join Employee as e on p.employee_id=e.employee_id
    group by p.project_id
    
Output: 

| product_id | average_price |
|------------|---------------|
| 1          | 6.96          |
| 2          | 16.96         |


##  :dart: `Difficulty Level - Medium`

 ### Q.1 Write a solution to find managers with at least five direct reports. Return the result table in any order. 
 
   `Table Name - Employee `
  
| Column Name | Type | 
| ----------- | ---  |
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |

id is the primary key (column with unique values) for this table.
Each row of this table indicates the name of an employee, their department, and the id of their manager.
If managerId is null, then the employee does not have a manager.
No employee will be the manager of themself.

The result format is in the following example.

**Example 1:** 

**Input:**

Employee  table:

| id  | name  | department | managerId |
| -----------| ---------| ----|-----|
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |

 ###  Solution - 
    
    select name 
    from Employee
    where id in (
                 select managerId 
                 from Employee 
                 group by managerId 
                 having (count(distinct id)>=5));

**Output:**

| name |
|-----------|
| John |

 ### Q.2 The confirmation rate of a user is the number of 'confirmed' messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. Round the confirmation rate to two decimal places. Write a solution to find the confirmation rate of each user. Return the result table in any order. 
 
   `Table Name - Signups `
  
| Column Name | Type | 
| ----------- | ---  |
| user_id        | int      |
| time_stamp     | datetime |

user_id is the column of unique values for this table.
Each row contains information about the signup time for the user with ID user_id.

   `Table Name - Confirmations `
  
| Column Name | Type | 
| ----------- | ---  |
| user_id        | int      |
| time_stamp     | datetime |
| action         | ENUM     |

(user_id, time_stamp) is the primary key (combination of columns with unique values) for this table.
user_id is a foreign key (reference column) to the Signups table.
action is an ENUM (category) of the type ('confirmed', 'timeout')
Each row of this table indicates that the user with ID user_id requested a confirmation message at time_stamp and that confirmation message was either confirmed ('confirmed') or expired without confirming ('timeout').

The result format is in the following example.

**Example 1:** 

**Input:**

Signups   table:

| user_id | time_stamp          |
| -----------| ---------| 
| 3       | 2020-03-21 10:16:13 |
| 7       | 2020-01-04 13:57:59 |
| 2       | 2020-07-29 23:09:44 |
| 6       | 2020-12-09 10:39:37 |

Confirmations table:

| user_id | time_stamp          | action    |
| -----------| ---------| ------|
| 3       | 2021-01-06 03:30:46 | timeout   |
| 3       | 2021-07-14 14:00:00 | timeout   |
| 7       | 2021-06-12 11:57:29 | confirmed |
| 7       | 2021-06-13 12:58:28 | confirmed |
| 7       | 2021-06-14 13:59:27 | confirmed |
| 2       | 2021-01-22 00:00:00 | confirmed |
| 2       | 2021-02-28 23:59:59 | timeout   |

 ###  Solution - 
    
    select name 
    from Employee
    where id in (
                 select managerId 
                 from Employee 
                 group by managerId 
                 having (count(distinct id)>=5));

##  :dart: `Difficulty Level - Hard`

 ### Q.1 A company's executives are interested in seeing who earns the most money in each of the company's departments. A high earner in a department is an employee who has a salary in the top three unique salaries for that department. Write a solution to find the employees who are high earners in each of the departments. Return the result table in any order.

 The result format is in the following example.
 
   `Table Name - Employee `
   
| Column Name  | Type    |
|--------------|---------|
| id           | int     |
| name         | varchar |
| salary       | int     |
| departmentId | int     |

id is the primary key (column with unique values) for this table.
departmentId is a foreign key (reference column) of the ID from the Department table.
Each row of this table indicates the ID, name, and salary of an employee. It also contains the ID of their department.
 

Table: Department

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |

id is the primary key (column with unique values) for this table.
Each row of this table indicates the ID of a department and its name.

The result format is in the following example.

**Example 1:** 

**Input:**

Employee table:

| id | name  | salary | departmentId |
|----|-------|--------|--------------|
| 1  | Joe   | 85000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
| 5  | Janet | 69000  | 1            |
| 6  | Randy | 85000  | 1            |
| 7  | Will  | 70000  | 1            |

Department table:

| id | name  |
|----|-------|
| 1  | IT    |
| 2  | Sales |


 ###  Solution - 
    
    with cte as 
           (select d.name as department, 
                   e.name as employee, 
                   salary as salary
           from Employee as e
           join Department as d on e.departmentId=d.id),
   cte1 as
         (select *,
                dense_rank()over(partition by department order by salary desc) as rnk 
          from cte)
    select  Department, 
            employee,
            salary 
    from cte1
    where rnk<=3;
    
**Output:**


| Department | Employee | Salary |
|------------|----------|--------|
| IT         | Max      | 90000  |
| IT         | Joe      | 85000  |
| IT         | Randy    | 85000  |
| IT         | Will     | 70000  |
| Sales      | Henry    | 80000  |
| Sales      | Sam      | 60000  |






    

      
