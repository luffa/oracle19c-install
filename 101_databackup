### Data pump 
```
CREATE DIRECTORY DIR_BACKUP AS 'D:\oracle_backup\data_pump';

```

#### 1.1 สร้าง Folder บน Windows Server

สร้างโฟลเดอร์สำหรับเก็บไฟล์ Dump (เช่น `C:\OracleBackup\datapump`)

#### 1.2 สร้าง Directory Object ใน Oracle Database

เชื่อมต่อกับฐานข้อมูลในฐานะผู้ใช้ที่มีสิทธิ์สูง (เช่น `SYS` หรือ `SYSTEM`) และรันคำสั่ง:

```sql
-- สร้าง Directory Object ชื่อ MY_DP_DIR ชี้ไปยังโฟลเดอร์จริงบน Server
CREATE DIRECTORY MY_DP_DIR AS 'C:\OracleBackup\datapump';

-- ให้สิทธิ์ในการอ่านและเขียนแก่ผู้ใช้ที่จะทำการ Export/Import (เช่น SYSTEM)
GRANT READ, WRITE ON DIRECTORY MY_DP_DIR TO SYSTEM;
```

### 2\. การส่งออกข้อมูล (Export - expdp)

คำสั่ง `expdp` จะรันที่ **Command Prompt (CMD)** ของ Windows Server (ไม่ใช่ใน SQL\*Plus)

#### โครงสร้างคำสั่งหลัก:

```bash
expdp [USERNAME]/[PASSWORD]@[SERVICE_NAME] \
    DIRECTORY=[DIRECTORY_OBJECT] \
    DUMPFILE=[FILE_NAME].dmp \
    LOGFILE=[LOG_FILE_NAME].log \
    [LEVEL_PARAMETER]=[VALUE]
```

#### ตัวอย่างการใช้งานที่พบบ่อย:

| ระดับการ Export | คำสั่งตัวอย่าง | คำอธิบาย |
| :--- | :--- | :--- |
| **Schema Level** | `expdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=hr_schema.dmp LOGFILE=hr_exp.log SCHEMAS=HR,SCOTT` | ส่งออกทั้งหมดของ Schema HR และ SCOTT |
| **Full Database** | `expdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=full_db.dmp LOGFILE=full_exp.log FULL=Y` | ส่งออกฐานข้อมูลทั้งหมด (ต้องมีสิทธิ์ EXP\_FULL\_DATABASE) |
| **Table Level** | `expdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=emp_tbl.dmp LOGFILE=tbl_exp.log TABLES=HR.EMPLOYEES` | ส่งออกเฉพาะตาราง EMPLOYEES ใน Schema HR |
| **เฉพาะโครงสร้าง (Metadata)** | `expdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=meta_only.dmp LOGFILE=meta_exp.log SCHEMAS=HR CONTENT=METADATA_ONLY` | ส่งออกเฉพาะโครงสร้าง (ไม่รวมข้อมูล) |
| **ใช้บีบอัด** | `expdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=comp.dmp LOGFILE=comp.log SCHEMAS=HR COMPRESSION=ALL` | บีบอัดข้อมูลในไฟล์ Dump |

### 3\. การนำเข้าข้อมูล (Import - impdp)

คำสั่ง `impdp` จะรันที่ **Command Prompt (CMD)** ของ Windows Server เช่นกัน

#### โครงสร้างคำสั่งหลัก:

```bash
impdp [USERNAME]/[PASSWORD]@[SERVICE_NAME] \
    DIRECTORY=[DIRECTORY_OBJECT] \
    DUMPFILE=[FILE_NAME].dmp \
    LOGFILE=[LOG_FILE_NAME].log \
    [REMAP_PARAMETER]=[OLD_VALUE]:[NEW_VALUE]
```

#### ตัวอย่างการใช้งานที่พบบ่อย:

| การใช้งาน | คำสั่งตัวอย่าง | คำอธิบาย |
| :--- | :--- | :--- |
| **Import Schema เดิม** | `impdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=hr_schema.dmp LOGFILE=hr_imp.log SCHEMAS=HR` | นำเข้า Schema HR กลับเข้าที่เดิม (ต้องมี Schema HR อยู่แล้ว) |
| **ย้าย/เปลี่ยน Schema** | `impdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=hr_schema.dmp LOGFILE=hr_new.log REMAP_SCHEMA=HR:HR_NEW` | นำเข้าข้อมูลจาก HR ไปยัง Schema ชื่อ **HR\_NEW** |
| **เมื่อตารางมีอยู่แล้ว** | `impdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=emp_tbl.dmp LOGFILE=tbl_replace.log TABLES=HR.EMPLOYEES TABLE_EXISTS_ACTION=REPLACE` | กำหนดให้ **REPLACE** ตารางที่มีอยู่แล้ว (ตัวเลือกอื่นคือ `APPEND`, `SKIP`, `TRUNCATE`) |
| **Import เฉพาะข้อมูล** | `impdp system/password@orcl DIRECTORY=MY_DP_DIR DUMPFILE=hr_schema.dmp LOGFILE=data_only.log SCHEMAS=HR CONTENT=DATA_ONLY` | นำเข้าเฉพาะข้อมูล (โครงสร้างตารางต้องมีอยู่แล้ว) |

