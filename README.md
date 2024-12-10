# Oracle 19c Install

0. [command](https://github.com/luffa/oracle19c-install/blob/main/00_Oracle_Linux_Commands.md)
   00. [OracleSqldeveloper](https://drive.google.com/file/d/1uZA0oWSpKmi8-EKZkgLOLA5wO8uM3794/view?usp=drive_link)
------
1. [Prerequisites](https://github.com/luffa/oracle19c-install/blob/main/01_Prerequisites.md)
2. [Installation](https://github.com/luffa/oracle19c-install/blob/main/02_Installtation.md)
3. [Install with GUI](https://github.com/luffa/oracle19c-install/blob/main/03_Installation_GUI.md)
4. [Create database](https://github.com/luffa/oracle19c-install/blob/main/04_Create_Database.md)
5. [Create databse with GUI](https://github.com/luffa/oracle19c-install/blob/main/05_Create_Database_GUI.md)
------
6. [Oracle Architecture](https://github.com/luffa/oracle19c-install/blob/main/06_Oracle_Architecture.md)

7. [User Rule](https://github.com/luffa/oracle19c-install/blob/main/07_Create_User_Rules.md#user--rules)
8. [SQL PLAY](https://github.com/luffa/oracle19c-install/blob/main/08_SQL_PLAY.md#grant)
------
9. [Create Table](https://github.com/luffa/oracle19c-install/blob/main/09_Create_Table.md#create-table)





แนะนำและโครงสร้างข้อมูล (3 ชั่วโมง)
คำศัพท์สำคัญ:

Tables: โครงสร้างสำหรับเก็บข้อมูลในรูปแบบตาราง (แถว/คอลัมน์)
ตัวอย่าง: "Table employees คือที่เก็บข้อมูลพนักงานทั้งหมด"
Data Types: ประเภทของข้อมูล เช่น VARCHAR2 (ข้อความ), NUMBER (ตัวเลข), DATE (วันที่)
Primary Key: คอลัมน์ที่ไม่ซ้ำกันในตาราง ใช้สำหรับระบุตัวตนของข้อมูล เช่น employee_id
Foreign Key: คอลัมน์ที่เชื่อมโยงไปยัง Primary Key ในอีกตารางหนึ่ง
Indexes: โครงสร้างที่ช่วยเพิ่มความเร็วในการค้นหา
ตัวอย่าง: "สร้าง Index ในคอลัมน์ last_name เพื่อค้นหาข้อมูลเร็วขึ้น"
กิจกรรม: สร้าง Table พร้อมข้อมูลตัวอย่าง และทดลอง Query เบื้องต้น

คำสั่ง SQL พื้นฐาน (3 ชั่วโมง)
คำศัพท์สำคัญ:

DML (Data Manipulation Language): คำสั่งสำหรับจัดการข้อมูลในตาราง
INSERT: เพิ่มข้อมูลใหม่
UPDATE: แก้ไขข้อมูล
DELETE: ลบข้อมูล
DDL (Data Definition Language): คำสั่งสำหรับจัดการโครงสร้าง เช่น สร้าง/แก้ไข Table
TCL (Transaction Control Language): คำสั่งควบคุมการเปลี่ยนแปลงข้อมูล เช่น COMMIT, ROLLBACK
กิจกรรม:

ทดลองใช้คำสั่ง SQL เพิ่ม/แก้ไข/ลบข้อมูลใน Table
การบริหารผู้ใช้และสิทธิ์ (2 ชั่วโมง)
คำศัพท์สำคัญ:

User: บัญชีผู้ใช้งานฐานข้อมูล
Roles: กลุ่มของสิทธิ์ที่กำหนดให้ผู้ใช้ เช่น CONNECT, RESOURCE
Privileges: สิทธิ์ในการทำงาน เช่น SELECT, INSERT
REVOKE: คำสั่งเพิกถอนสิทธิ์ที่เคยให้
กิจกรรม:

สร้าง User ใหม่ และกำหนดสิทธิ์ในการเข้าถึง Table
