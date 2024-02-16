# View

### ตัวอย่างคำสั่งการสร้าง view

```sql
create or replace view view1 as
select t1.fieldId,t2.fieldname from table1 t1,table2
where t1.filed1Id = t2.file2Id
```

```sql
CREATE OR REPLACE VIEW StudentEnrollmentView AS
SELECT s.StudentID, s.Name AS StudentName, s.Age AS StudentAge, s.Gender AS StudentGender,
       c.CourseID, c.CourseName, e.Grade
FROM Students s
JOIN Enrollments e ON s.StudentID = e.StudentID
JOIN Courses c ON e.CourseID = c.CourseID;
```
