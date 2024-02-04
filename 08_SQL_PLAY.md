
### GRANT
```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON APPDBA.TABLEAPP		TO MY_RULES; 
```
### Synonym

```sql
CREATE [PUBLIC] SYNONYM synonym_name FOR object_schema.object_name;
```
```sql
CREATE  SYNONYM APPUSER.TABLEAPP FOR APPDBA.TABLEAPP;
```
### Sequence

```sql
CREATE SEQUENCE APPDBA.TABLEAPP_SEQ
  START WITH 1
  MAXVALUE 999999999999999999999999999
  MINVALUE 1
  NOCYCLE
  CACHE 20
  NOORDER;
```

### TRIGGER

```sql
create or replace
TRIGGER tableapp_trig
after insert or update
of extcode, extusername, extpwd
on tableapp
for each row
begin
  if inserting then
   insert into useraccess(userid, username)
    values(:new.id, :new.name);
  elsif updating then
   update useraccess set username = :new.name
   where userid = :old.id;
  end if;
end;
/
```
### Procedure

```sql
create or replace
PROCEDURE deletedatatemp(
id IN VARCHAR2) IS
idnumber NUMBER;
tmpname varchar2;
BEGIN

  idnumber := TO_NUMBER(id);

  -------- UPDATE test 1 ----------------------------------------------
  SELECT name INTO tmpname
  FROM tableapp
  WHERE (id = id);

  UPDATE test1
  SET name = tmpname || '=' || 'data from test 1'
  WHERE (id = nmae);
  ---------------------------------------------------------------------

END;
/
```
### Function
```sql
create or replace function A_TEST_FUNCTION RETURN VARCHAR2 AS 
aa VARCHAR2(20);
BEGIN
 select to_char( max(to_number(id))+1) into aa from tableapp;

  RETURN aa;
END A_TEST_FUNCTION;
```



### Monitor
```sql
SELECT sql_text
FROM v$sqlarea
ORDER BY last_active_time DESC
FETCH FIRST 1 ROWS ONLY;
```
```sql
SELECT sql_text
FROM v$session
ORDER BY last_call_et DESC
FETCH FIRST 1 ROWS ONLY;
```


