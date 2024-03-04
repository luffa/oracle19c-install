# Workshop 2
1. สร้าง view แสดงข้อมูลนักเรียน ที่มี GPA 3.00 ขึ้นไป

```sql
CREATE OR REPLACE FORCE NONEDITIONABLE VIEW "APPDBA"."V_01_STUDGPA" ("STUDENTID", "STUDENNAME", "AGE", "GENDER", "GRADELEVEL", "GPA") AS 
  SELECT studentid,name as studenName, age,gender,gradelevel,gpa   
  FROM students
  where gpa > 2.99
```

2. หารายชื่อของนักเรียน ที่ได้คะแนนสูงสุดและตำ่สุดแต่ละวิชา
3. อาจารย์แต่ละคน สอนกี่วิชา
4. วิชาอะไรที่มีการลงทะเบียนเรียนเยอะที่สุด
5. แสดงคะแนนรายวิชาของนักเรียนแต่ละคน (ระบุรหัส)
6. นักเรียนแต่ละคนเรียนกับ อาจารย์คนไหนบ้้าง
