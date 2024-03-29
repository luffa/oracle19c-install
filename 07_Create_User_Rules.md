# User & Rules

```sh
alter session set "_ORACLE_SCRIPT"=true; 
CREATE TABLESPACE APP LOGGING DATAFILE '/u01/app/oracle/oradata/DBWU/APP1.DBF' SIZE 1000M,
'/u01/app/oracle/oradata/DBWU/APP2.DBF' SIZE 1000M,
'/u01/app/oracle/oradata/DBWU/APP3.DBF' SIZE 1000M EXTENT  MANAGEMENT LOCAL;
CREATE TABLESPACE INDX  LOGGING  DATAFILE '/u01/app/oracle/oradata/DBWU/INDX1.DBF' SIZE 1000M EXTENT   MANAGEMENT LOCAL;

ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/DBWU/APP1.DBF' AUTOEXTEND ON  NEXT 500M MAXSIZE UNLIMITED;
ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/DBWU/APP2.DBF' AUTOEXTEND ON  NEXT 500M MAXSIZE UNLIMITED;
ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/DBWU/APP3.DBF' AUTOEXTEND ON  NEXT 500M MAXSIZE UNLIMITED;
ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/DBWU/INDX1.DBF' AUTOEXTEND ON  NEXT 500M MAXSIZE UNLIMITED;
```


create rule
```sh
CREATE ROLE "MY_RULES"  NOT IDENTIFIED;
```
create user  as DBA

```sh
CREATE USER APPDBA PROFILE "DEFAULT" 
	IDENTIFIED BY "dbapassword" 
	DEFAULT TABLESPACE "APP" 
	TEMPORARY TABLESPACE "TEMP"
	ACCOUNT UNLOCK;
GRANT QUERY REWRITE TO "APPDBA";
GRANT UNLIMITED TABLESPACE TO "APPDBA";
GRANT "CONNECT" TO "APPDBA";
GRANT "DBA" TO "APPDBA";
GRANT "RESOURCE" TO "APPDBA" ;
GRANT "MY_RULES" TO "APPDBA";
```

create user other

```sh
CREATE USER "APPUSER" PROFILE "DEFAULT" 
	IDENTIFIED BY "appuserpassword"
	DEFAULT TABLESPACE "APP" 
	TEMPORARY TABLESPACE "TEMP"
	ACCOUNT UNLOCK;
GRANT QUERY REWRITE TO "APPUSER";
GRANT UNLIMITED TABLESPACE TO "APPUSER";
GRANT "CONNECT" TO "APPUSER";
GRANT "RESOURCE" TO "APPUSER";
GRANT "MY_RULES" TO "APPUSER";
```
### Tablespace

```sql
ALTER TABLESPACE SYSAUX ADD DATAFILE '/u01/app/oracle/oradata/DBWU/SYSAUX02.dbf'  SIZE 500M REUSE AUTOEXTEND ON  NEXT 500M  MAXSIZE UNLIMITED;
ALTER TABLESPACE SYSTEM ADD DATAFILE '/u01/app/oracle/oradata/DBWU/SYSTEM02.dbf'  SIZE 500M REUSE AUTOEXTEND ON  NEXT 500M  MAXSIZE UNLIMITED;
```


### Temp tablespace
```sql
CREATE TEMPORARY TABLESPACE TEMP1 TEMPFILE ‘/u01/app/oradata/DBACLASS/temp01′ SIZE 2G;

ALTER DATABASE DEFAULT TEMPORARY TABLESPACE TEMP1;

ALTER SYSTEM KILL SESSION 'SID,SERIAL#' IMMEDIATE;


DROP TABLESPACE temp INCLUDING CONTENTS AND DATAFILES;
```
