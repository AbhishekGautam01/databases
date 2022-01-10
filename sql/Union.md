# Union 

* It is a set of operator provided by SQL 
* It is used to combine the result of 2 SELECT statement into a single result set adn returns the result set. 
* **Syntax**: `query_1 UNION query_2`
* It has following requirements:    
    * The **number & order of columns** in first query must be same in second
    * Data types of corresponding columns must be same or compatible 

## Union vs Union All 
* By default **Union removes all the duplicated** but if we want to keep the duplicates we should use union all. 
