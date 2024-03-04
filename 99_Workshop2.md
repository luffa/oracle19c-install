# Workshop 2
1. สร้าง view แสดงข้อมูลนักเรียน ที่มี GPA 3.00 ขึ้นไป

```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_01_STUDGPA" ("STUDENTID", "STUDENNAME", "AGE", "GENDER", "GRADELEVEL", "GPA") AS 
  SELECT studentid,name as studenName, age,gender,gradelevel,gpa   
  FROM students
  where gpa > 2.99
```

2. หารายชื่อของนักเรียน ที่ได้คะแนนสูงสุดและตำ่สุดแต่ละวิชา

```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_STUDMAXGRADE" ("STUDENTID", "STUDENNAME", "COURSEID", "COURSENAME", "GRADE") AS 
  select  e.STUDENTID, s.name as studenName,ec.courseid,c.coursename,ec.grade from enrollments e
  join (select courseid, max(grade) as grade from enrollments 
  group by courseid) ec on e.courseid = ec.courseid and ec.grade =e.grade
  left join students s on e.studentid = s.studentid
  left join courses c on e.courseid = c.courseid;
```
```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_STUDMINGRADE" ("STUDENTID", "STUDENNAME", "COURSEID", "COURSENAME", "GRADE") AS 
  select  e.STUDENTID, s.name as studenName,ec.courseid,c.coursename,ec.grade from enrollments e
  join (select courseid, min(grade) as grade from enrollments 
  group by courseid) ec on e.courseid = ec.courseid and ec.grade =e.grade
  left join students s on e.studentid = s.studentid
  left join courses c on e.courseid = c.courseid;
```
```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_02_STUDMINMAX" ("COURSEID", "COURSENAME", "STUDENMAXGRADE", "STUDENTMINGRADE") AS 
  select m.courseid,m.coursename,m.studenname as studenMaxGrade,n.studenname as studentMinGrade
  from v_studmaxgrade m
  join v_studmingrade n on n.courseid = m.courseid
```

3. อาจารย์แต่ละคน สอนกี่วิชา

```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_03_TCOUNT" ("TEACHERID", "NAME", "COUNTT") AS 
  select t.teacherid,t.name,tc.countT as countT from teachers t
  left join (select teacherid, count(teacherid) as countT from courses group by teacherid) tc on t.teacherid = tc.teacherid;
```

4. วิชาอะไรที่มีการลงทะเบียนเรียนเยอะที่สุด
5. แสดงคะแนนรายวิชาของนักเรียนแต่ละคน (ระบุรหัส)
6. นักเรียนแต่ละคนเรียนกับ อาจารย์คนไหนบ้้าง
