# Queries
1. SQL Query to update DateOfJoining to 15-Jul-2021 for empid=1
```
UPDATE 
    EMPLOYEE 
SET 
    DateOfJoining = '15-Jul-2021'
WHERE   
    emp_id = 1
```
2. SQL query to select all student name where age is greater than 22
```
SELECT 
    student_name
FROM 
    Student
WHERE 
    AGE > 22
```
3. SQL Query to find all  employee with salary between 30000 and 50000
```
SELECT 
    * 
FROM 
    Employee
WHERE 
    Salary BETWEEN 30000 and 40000
````
4. SQL query to find name of employee beginning with S
````
SELECT 
    *
FROM 
    Employee
WHERE 
    Emp_Name like 'S%'

````
5. SQL Query to display full name 
```
SELECT 
    CONCAT(FirstName, LastName) As FullName
From 
    Employee
```
6. Write a query to fetch details of emp whose employee FirstName end with and alphabet a and contains 4 Alphabets 
```
SELECT 
    * 
FROM 
    EMPLOYEE    
WHERE 
    Emp_Name like '___A'
```
7. Write a query to fetch details of all employees excluding the employees with first names, 'ANUSHKA' and 'SOMNATH' from the employee table
```
SELECT 
    * 
FROM 
    EMPLOYEE
WHERE 
    Emp_Name in ('ANUSHKA', 'SOMNATH')
```
8. SQL query to display the current date?
```
SELECT 
    SYSDATE, 
    CURRENT_DATE,
    CURRENT_TIMESTAMP, 
    SYSTIMESTAMP
FROM
    DUAL 
```
9. SQL query to get day of last day of the previous month?
```
SELECT 
    TO_CHAR(LAST_DAY(ADD_MONTHS(SYSDATE, -1)), 'DAY') 
FROM 
    DUAL
```
10. Write an SQL query to fetch the employee first names and replace A with '@'
```
SELECT 
    REPLACE(FIRST_NAME, 'A', '@')
FROM
    Employee
```
11. Write a SQL query to fetch the domain from an email address 
```
SELECT 
    SUBSTR(EMAIL_ID, INSTR(EMAIL_ID, '@')+ 1)
FROM 
    EMPLOYEE
```
12. Write an SQL query to update the employees names by removing leading and trailing spaces
```
UPDATE 
SET Emp_NAME = LTRIM(RTRIM(Emp_Name))
```
13. Write and query to fetch all the emplioyees details from employee tvale  whom joined in the year 2022 
```
SELECT 
    *
FROM
    EMPLOYEE
WHERE
    DATEOFJOINING BETWEEN '01-JAN-2022' AND '31-DEC-2022'
```
14. Write an SQL query to fetch only odd rows/ even rows from the table 
```
SELECT * FROM EMPLOYEE WHERE MOD(EMP_ID, 2) = 0
SELECT * FROM EMPLOYEE WHERE MOD(EMP_ID, 2) <> 0
```
15. Write an SQL query to create a new table with data and structure copied from another table. 
```
CREATE TABLE EMPLOYEE_NEW AS (SELECT * FROM EMPLOYEE)
```
16. Write an SQL query to create an empty table with the same structure as some other table 
```
CREATE TABLE EMP2 AS (SELECT * FROM EMPLOYEE WHERE 1=2)
```
17. Write an SQL query to fetch top 3 highest salaries
```
SELECT 
    DISTINCT TOP(4) SALARY 
FROM 
    EMPLOYEE
ORDER BY SALARY DESC
    //or\\
SELECT
    SALARY 
FROM (
    SELECT DISTINCT SALARY FROM EMPLOYEE ORDER BY SALARY DESC
)
WHERE ROWNUM < 4
```
18. Select the first employee and the last employee from employee table 
```
SELECT 
    * 
FROM 
    EMPLOYEE
WHERE   
    EMP_ID = SELECT MIN(EMP_ID) FROM EMPLOYEE
```
19. List the ways to get the count of records in the table?
```
SELECT COUNT(*) FROM EMPLOYEE
SELECT COUNT(EMP_ID) FROM EMPLOYEE --it can be any column
```
20. Write a query to fetch the department-wise count of employees sorted by department's count in ascending order? 
````
SELECT 
    , DEPT_NAME, COUNT(*) AS 'NUMBER OF EMPLOYEES'
FROM
    EMPLOYEE
GROUP BY 
        DEPT_NAME
````
21. Write a query to retrieve Departments who have less than 4 employees working in it. 
```
SELECT 
    DEPT_NAME, COUNT(*) AS 'NoOfEMP'
FROM 
    EMPLOYEE
GROUP BY DEPT_NAME
HAVING COUNT(*) < 4
```
22. Write a query to retrieve department wise maximum salary 
````
SELECT 
    DEPARTMENT, MAX(SALARY)
FROM
    EMPLOYEE
GROUP BY DEPARTMENT
````
23. Write a query to fetch employee earning maximum salary in his/her department. 
```
SELECT 
    * 
FROM Employee E1 
JOIN (
    SELECT DEPT, 
           MAX(SALARY) AS 'Salary'
    FROM
        EMPLOYEE
    GROUP BY 
        DEPT
) E2
ON 
    E1.DEPT = E2.DEPT
AND 
    E1.Salary = E2.Salary
```
25. Write an SQL query to fetch the first 50% of records from a table 
```
SELECT 
    * 
FROM 
    Employee
WHERE 
    ROWNUM <= (SELECT COUNT(*) FROM EMPLOYEE)/2
```
26. Query to fetch employee details along with the computer details who have been assigned with a computer. 
```
SELECT * 
FROM EMPLOYEE E
JOIN COMPUTER C
ON E.CompId = C.Id
```
27. Fetch all employee dtails along with the computer name assigned to them 
```
SELECT E.EmpId, E.FirstName || ' ' || E.LastName, NVL(C.BRAND, 'NOT ASSIGNED')
FROM EMPLOYEE E 
LEFT JOIN COMPUTER C 
ON E.COMP_ID = C.COMP_ID
```
28. Fetch all computers details along with employee name using it
```
SELECT C.BRAN, C.COMP_MODEL, E.FIRST_NAME || ' ' || E.LAST_NAME 
FROM EMPLOYEE E 
RIGHT JOIN COMPUTER C 
ON E.COMP_ID = C.COMP_ID
```
29. Delete duplicate records from a table
```
DELETE FROM EMPLOYEE 
WHERE EMP_ID IN (
    SELECT EMP_ID 
    FROM (
        SELECT *, ROW_NUMBER() OVER (PARTITION BY EMP_NAME ORDER BY EMP_ID) AS ROW_NUM
        FROM EMPLOYEE
    ) 
    WHERE 
        ROW_NUMBER <> 1
)
```
30. Find the Nth Highest Salary
```
SELECT * FROM (
    SELECT E-NAME, SALARY, 
           DENSE_RANK() OVER( ORDER BY SAL DESC) rank
    FROM EMPLOYEE
    )
WHERE rank = N  
```
