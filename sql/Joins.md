# Joins
* SQL has 4 types of joins: 
    1. **INNER JOIN** aka Simple Join
    2. **LEFT OUTER JOIN** aka Left Join
    3. **RIGHT OUTER JOIN** aka Right Join
    4. **FULL OUTER JOIN** aka Full Join

## Inner Join (Simple Join)
![2](./img/2.gif)
* Inner joins returns all the rows from multiple tables where join condition is met. 
```
select columns 
from table1
inner join table2 
on table1.column = table2.column
```

## Left Outer Join (Left Join)
![3](./img/3.gif)
* It returns all rows from the left hand table specified in the ON condition and only those rows from the other table where the joined fields are equal (join condition is met)
```
select columns
from table1
left [outer] join table2
on table1.column = table2.column
```

## Right Outer Join (Right Join)
![4](./img/4.gif)
* This type of join returns all rows from the right-hand table specified in the ON condition and only those rows from the other table where the joined fields are equal. 
```
select columns 
from table1 
right [outer] join table2
on table1.column = table2.column
```

## Full Outer Join (Full Join)
![5](./img/5.gif)
* This type of join returns all rows from the left hand table and right hand table with nulls in place where the join condition is not met. 
```
select columns 
from table1
full [outer] join table2
on table1.column = table2.column
```