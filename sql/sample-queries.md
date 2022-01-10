#Queries
#Simple Querying
1. SELECT * from "public"."employees"
2. Select count( * ) from "public"."departments"
3. select concat(emp_no, ' is a ', title) AS "employee title" from "public"."titles"
4. select * from customers where state = 'OR' or state = 'NY'
5. select * from customers where not age = 55
6. select count (*) from customers where state='OR'
7. select * from customers where age > 44 or income > 10000
8. select * from customers where (age between 30 and 50 )and income < 50000
9. select avg(income) from customers where age between 20 and 50 
11. select * from customers where  (country = 'Japan' OR country = 'Australia') AND income > 50000
12. select sum(totalamount) from Orders where totalamount> 100 and orderdate between '2004-06-01' and '2004-06-30'
13. select COALESCE(address2, 'No Adress') from customers 
14. select * from customers where address2 is not null
15. select COALESCE(lastname, 'Empty'), * from customers where age is not null
16. select age from customers  where age between 30 and 50  and  income < 50000
17. select avg(income) from customers where age between 30 and 50 
18. select * from orders where customerid in(7882, 12808, 623)
19. select * from city where district in ('Zuid-Holland')
20. select  first_name,extract(Year from AGE(birth_date)) as "age" from employees where first_name like 'M%'
21. select  count(*) from employees where first_name ilike 'A%R'
22. select count(customerid) from customers where zip::text like '%2%'
23. select count(customerid) from customers where zip::text like '2_1%'
24. select coalesce(state, 'No State') as "State" from customers where phone::text like '302%' 
25. select * from employees where (EXTRACT (YEAR from AGE(birth_date))) > 60
26. select * from employees where extract (Month from hire_date ) = 2
27. select * from employees where extract (Month from birth_date) = 10
28. select max(age(birth_date)) from employees
29. select * from orders where DATE_TRUNC('month', orderdate) = date '2004-01-01'
30. select distinct title from titles
31. select distinct birth_date from employees 
32. select distinct lifeexpectancy from country where lifeexpectancy is not null order by lifeexpectancy
33. select * from employees order by first_name, last_name desc 
34. select * from employees order by AGE(birth_date)
35. SELECT * from employees where first_name like '%k' order by hire_date desc
36. SELECT c.firstname, c.lastname, o.orderid FROM orders AS oINNER JOIN customers AS c ON o.customerid = c.customeridWHERE c.state IN ('NY', 'OH', 'OR')ORDER BY o.orderid;
37. SELECT p.prod_id, i.quan_in_stock FROM products as p INNER JOIN inventory AS i oN p.prod_id = i.prod_id 