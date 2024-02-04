# Oracle Architecture

![arch](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.23.54.png)

จะแบ่งออกเป็นสองส่วนด้วยกัน คือ Oracle Instance และ ส่วนของ Oracle Database

### 1. Oracle Instance 

![arch](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.23.39.png)

##### คือหน่วยความจำที่ใช้เก็บข้อมูล และควบคุมการทำงานของ Oracle server ที่เรียกว่า SGA (System Global Area) รวมกับ Oracle Process ที่ใช้ในการทำงานของ Oracle
  ###### SGA (System Global Area) ประกอบด้วย

![sga](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.23.24.png)
  
      · shared pool
      · database buffer cache
      · redolog buffer
      · large pool
      · java pool
      · stream pool
  ###### Oracle Process ประกอบด้วย

![procress](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.25.02.png)
  
      · database writer(DBW)
      · log writer process(LGWR)
      · system monitor(SMON)
      · process monitor(PMON)
      · checkpoint process(CKPT)
      · archiver process(ARC)


# Physical file

oracle database นั้นจะประกอบไปด้วยไฟล์ที่รวมกันเป็นฐานข้อมูลอยู่ 3 ประเภท คือ
![systemdatafile](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.26.02.png)


      · control file
      · redo log file
      · data file (Tablespace)

#### Data File

![datafile](https://github.com/luffa/oracle19c-install/blob/main/image/memory/Screenshot%202567-02-04%20at%2006.59.49.png)


ตัวอย่าง คำสั่ง
```sh
CREATE TABLESPACE APP  LOGGING  DATAFILE '/u01/app/oracle/oradata/mydb1/INDX1.DBF' SIZE 1000M EXTENT   MANAGEMENT LOCAL;
```

กำหนดให้สามารถขายแบบ Auto
```sh
ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/mydb1/INDX1.DBF' AUTOEXTEND ON  NEXT 500M MAXSIZE UNLIMITED;
```




[ที่มา](https://www.oracle.com/webfolder/technetwork/tutorials/architecture-diagrams/19/database-technical-architecture.html)
