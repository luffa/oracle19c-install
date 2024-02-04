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

```sql
CREATE [PUBLIC] SYNONYM synonym_name FOR object_schema.object_name;
```
