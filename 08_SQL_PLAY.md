
### GRANT
```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON APPDBA.TABLEAPP		TO MY_RULES; 
```
### Synonym

```sql
CREATE [PUBLIC] SYNONYM synonym_name FOR object_schema.object_name;
```
```sql
CREATE  SYNONYM TABLEAPP FOR APPDBA.TABLEAPP;
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

### Trig

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


