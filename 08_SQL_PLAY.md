```sh
SELECT sql_text
FROM v$sqlarea
ORDER BY last_active_time DESC
FETCH FIRST 1 ROWS ONLY;
```
```sh
SELECT sql_text
FROM v$session
ORDER BY last_call_et DESC
FETCH FIRST 1 ROWS ONLY;
```
