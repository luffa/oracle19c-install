# Select statement

### select all

```sql
select * from table;
```

### select with condition

```sql
select * from table where filename = 'somevalue';
```

### select with join

```sql
select * from table1 t1
join table2 t2 on t1.t1fieldid2 = t2.t2field
join table3 t3 on t1.t1filedid3 = t3.t3field
```


## SQL Operators
 - Arithmetic Operators
 - Character Operators
 - Comparison Operators
 - Logical Operators
 - Set Operators

### Arithmetic Operators

|Operator|Description|Example|
|-----------|-----------------------------|----------------------|
| + (unary) | Makes operand positive |  SELECT +3 FROM DUAL;|
| - (unary) | Negates operand | SELECT -4 FROM DUAL; |
| / | Division (numbers and dates)| SELECT SAL / 10 FROM EMP; |
| * | Multiplication         | SSELECT SAL * 5 FROM EMP; |
| + | Addition (numbers and dates)         | SELECT SAL + 200 FROM EMP; |
| - | Subtraction (numbers and dates)         | SELECT SAL - 100 FROM EMP; |

### Character Operators

|Operator|Description|Example|
|-----------|-----------------------------|----------------------|
| \|\| | Concatenates character strings |  SELECT 'The Name of the employee is: ' \|\| ENAME FROM EMP;|

### Comparison Operators

|Operator|Description|Example|
|-----------|-----------------------------|----------------------|
|= | Equality test. | SELECT ENAME "Employee" FROM EMP WHERE SAL = 1500;|
|!=, ^=, <>|Inequality test.|SELECT ENAME FROM EMP WHERE SAL ^= 5000;|
|>|Greater than test.|SELECT ENAME "Employee", JOB "Title" FROM EMP WHERE SAL > 3000;|
|<|Less than test.|SELECT * FROM PRICE WHERE MINPRICE < 30;|
|>=|Greater than or equal to test.|SELECT * FROM PRICE WHERE MINPRICE >= 20;|
|<=|Less than or equal to test.|SELECT ENAME FROM EMP WHERE SAL <= 1500;|
|IN|"Equivalent to any member of" test. Equivalent to "=ANY".|SELECT * FROM EMP WHERE ENAME IN ('SMITH', 'WARD');|
|ANY/ SOME|Compares a value to each value in a list or returned by a query. Must be preceded by =, !=, >, <, <= or >=. Evaluates to FASLE if the query returns no rows.|SELECT * FROM DEPT WHERE LOC = SOME ('NEW YORK','DALLAS');|
|NOT IN|Equivalent to "!=ANY". Evaluates to FALSE if any member of the set is NULL.|SELECT * FROM DEPT WHERE LOC NOT IN ('NEW YORK', 'DALLAS');|
|ALL|Compares a value with every value in a list or returned by a query. Must be preceded by =, !=, >, <, <= or >=. Evaluates to TRUE if the query returns no rows.|SELECT * FROM emp WHERE sal >= ALL (1400, 3000);|
|[NOT] BETWEEN x and y|[Not] greater than or equal to x and less than or equal to y.|SELECT ENAME, JOB FROM EMP WHERE SAL BETWEEN 3000 AND 5000;|
|EXISTS|TRUE if a sub-query returns at least one row.|SELECT * FROM EMP WHERE EXISTS (SELECT ENAME FROM EMP WHERE MGR IS NULL);|
|x [NOT] LIKE y [ESCAPE z]|TRUE if x does [not] match the pattern y. Within y, the character "%" matches any string of zero or more characters except null. The character "_" matches any single character. Any character following ESCAPE is interpreted literally, useful when y contains a percent (%) or underscore (_).|SELECT * FROM EMP WHERE ENAME LIKE '%E%';|
|IS [NOT] NULL|Tests for nulls. This is the only operator that should be used to test for nulls.|SELECT * FROM EMP WHERE COMM IS NOT NULL AND SAL > 1500;|

