# Aggregate Function 
* Used to perform calculation on one more values and returns a single value. 
* Commonly used with **SELECT, GROUP BY & HAVING** 
* **Syntax**: `aggregate_function_name(DISTINCT | ALL expression)`
    * **aggregate_function_name**: name of function we want to apply 
    * **Distinct**: if we want that function to only work on distinct records provided. 
    * **All**: If we want that aggregate function to consider duplicate records also. If nothing is specified the by default all is selected. 
    * **Expression** - can be any column value of table or an expression which returns multiple values. 

# Aggregate Function List 

| Aggregate Function | Description | 
| :--- | :---: | 
| AVG  | The AVG() aggregate function calculates the average of non-NULL values in a set. | 
| CHECKSUM_AGG | The CHECKSUM_AGG() function calculates a checksum value based on a group of rows. | 
| COUNT | The COUNT() aggregate function returns the number of rows in a group, including rows with NULL values. | 
| COUNT_BIG | The COUNT_BIG() aggregate function returns the number of rows (with BIGINT data type) in a group, including rows with NULL values. | 
| MAX | The MAX() aggregate function returns the highest value (maximum) in a set of non-NULL values. | 
| MIN | The MIN() aggregate function returns the lowest value (minimum) in a set of non-NULL values. | 
| STDEV | The STDEV() function returns the statistical standard deviation of all values provided in the expression based on a sample of the data population. | 
| STDEVP | The STDEVP() function also returns the standard deviation for all values in the provided expression, but does so based on the entire data population. | 
| SUM | The SUM() aggregate function returns the summation of all non-NULL values a set. | 
| VAR | The VAR() function returns the statistical variance of values in an expression based on a sample of the specified population. | 
| VARP | The VARP() function returns the statistical variance of values in an expression but does so based on the entire data population. | 

<br/>


