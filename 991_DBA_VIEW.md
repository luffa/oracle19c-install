# DBA VIEW

Provides information about each user in the database.
```sql
select * from DBA_USERS;
```

Provides information about each tablespace in the database.
```sql
select * from DBA_TABLESPACES;
```

Shows the source code for stored functions, triggers, and Java objects
```sql
select * from DBA_SOURCE;
```

Gives information about the datafiles.
```sql
select * from DBA_DATAFILES;
```

Lets the DBA view information about any table.
```sql
select * from DBA_TABLES where owner = 'APPDBA';
```

Provides detailled information about each column of a table.
```sql
select * from DBA_TAB_COLUMNS where owner = 'APPDBA';
```

Show information about table indexes; helps when trying to decide if some index is useful or not.  A related view is DBA_IND_COLUMNS which tells which columns of a table are indexed.
```sql
select * from DBA_INDEXES where owner = 'APPDBA';
```

Lists the restristions that have been placed on the contents of columns of tables and views.  More detailed information comes from the related view DBA_CONS_COLUMNS.
```sql
select * from DBA_CONSTRAINTS where owner = 'APPDBA';
```

### Performance Monitoring Views
|View|Description|
|-----|-----------|
|V$SYSSTAT|	Statistics such as the amount of data changed and the number of transactions executed.|
|V$SQL|	The actual SQL commands recently executed, how many time it was executed and how much CPU time it took.|
|V$SESSTAT|	Shows resources consumed per session.  (Related: V$SESSION_WAIT)|
|V$FILESTAT	|The number of reads and writes per file, and time spent on disk I/O.|
|V$DATAFILE|	Lists the file number and name for each DB file.  In many views and tables Oracle identifies files by the number rather than name.  (Related: V$DATAFILE_HEADER)|
|V$DATABASE|	General information about the database|
|V$DBFILE|	Shows file name to numbers|
|V$FIXED_TABLE|	Shows the names of all dynamic tables and views.|
|V$INSTANCE	|General information about each instance.|
|V$PARAMETER|	Shows all the initializatino parameters and their current values.|
|V$SGA	|Summary statistics for the use of space in the SGA.|
|V$TEMPFILE	|Shows Statistics for locally-managed temporary tablespace fil|
