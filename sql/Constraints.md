# Unique And Check Constraint
**WHY** Used to `enforce data integrity in db tables`. These are important db objects. 
* These are rules that database engine enforces for you. 

## UNIQUE Constraints 
* It can be used to make sure that no duplicate values are entered in specific columns that do not participate in a primary key. 
* This should be used on a column or group of columns where we want to ensure uniqueness for column/s that is not PK 
* It allows for **one null** value. 
* A unique constraint can be referenced by foreign keys. 
* if this is added to column which already has duplicate values then this constraint is not applied. 
* Unless a clustered index is explicitly specified, a unique, non clustered index is created by default to enforce the UNIQUE constraint. 

## CHECK Constraints 
* It enforces `domain integrity` by limiting the values that are accepted by one or more columns. 
* You can put check constraint with any logical(BOOLEAN) expression. 
* You can apply multiple check constraints to a single column. You can also apply a single check constraint to multiple columns by creating it at the table level. 
* **Limitation** CHECK constraints reject values that evaluate to FALSE. Because null values evaluate to
UNKNOWN, their presence in expressions may override a constraint.

```
CREATE TABLE CheckTbl (col1 int, col2 int); 
GO 
CREATE FUNCTION CheckFnctn() 
RETURNS int 
AS 
BEGIN 
 DECLARE @retval int 
 SELECT @retval = COUNT(*) FROM CheckTbl 
 RETURN @retval 
END; 
GO 
ALTER TABLE CheckTbl 
ADD CONSTRAINT chkRowCount CHECK (dbo.CheckFnctn() >= 1 ); 
GO 
```