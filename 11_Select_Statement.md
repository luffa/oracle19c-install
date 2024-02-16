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
| || | Concatenates character strings |  SELECT 'The Name of the employee is: ' || ENAME FROM EMP;|

