
### GRANT
```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON APPDBA.TABLEAPP		TO MY_RULES; 
```
### Synonym

```sql
CREATE [PUBLIC] SYNONYM synonym_name FOR object_schema.object_name;
```
```sql
CREATE [PUBLIC] SYNONYM TABLEAPP FOR APPDBA.TABLEAPP;
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


