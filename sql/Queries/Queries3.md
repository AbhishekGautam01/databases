# Queries

![Tables ](./img/Screenshot%202022-02-13%20185914.png)

## Duplicate Records in a Table 
```
SELECT EmpName, Salary, Count(*) As Cnt
FROM Employees 
GROUP BY EmpName, Salary
Having COUNT(*) > 1
    // OR \\
SELECT 
    *, 
    ROW_NUMBER() OVER (PARTITION BY EmpName, DeptName ORDER BY EmpId) as Rank
FROM Employee 
WHERE rank <> 1 
```

## DELETE all the duplicate records in a table 
```
WITH cte AS (
    SELECT EmpName, Salary, 
    ROW_NUMBER() OVER (
        PARTITION BY 
            EmpName, Salary
        ORDER BY 
            EmpName, Salary
    ) row_num 
    FROM Employees
)
DELETE FROM cte WHERE row_num <> 1
```

## Find the manager name for the employee where EmpId and ManagerId are in same table 
````
SELECT e.EmpId, e.EmpName, m.EmpName
FROM Employee e
LEFT JOIN Employee m 
ON e.ManagerId = m.EmpId 
````

## Find the second highest salary 
```
SELECT MAX(Salary) as Salary
From Employee 
WHERE Salary < (Select MAX(Salary) from Employee)

// OR \\ 

SELECT * FROM (
    SELECT E-NAME, SALARY, 
           DENSE_RANK() OVER( ORDER BY SAL DESC) rank
    FROM EMPLOYEE
    )
WHERE rank = N  

```
## Find the employee with Second Highest Salary 
```
SELECT * FROM Employee WHERE SALARY in (
    SELECT max(Salary) as Salary 
    FROM Employee 
    WHERE Salary < (SELECT Max(Salary) FROM Employee)
)
```