# Create Table

### คำสั่งในการสร้างตาราง 

```sql
CREATE TABLE TABLENAME
```

```sql
CREATE TABLE Students (
    StudentID NUMBER PRIMARY KEY,
    Name VARCHAR2(100),
    Age NUMBER,
    Gender VARCHAR2(10),
    GradeLevel NUMBER,
    GPA NUMBER(3, 2)
);

CREATE TABLE Teachers (
    TeacherID NUMBER PRIMARY KEY,
    Name VARCHAR2(100),
    Age NUMBER,
    Gender VARCHAR2(10),
    Department VARCHAR2(100)
);

CREATE TABLE Courses (
    CourseID NUMBER PRIMARY KEY,
    CourseName VARCHAR2(100),
    Description VARCHAR2(4000),
    TeacherID NUMBER,
    Credits NUMBER,
    FOREIGN KEY (TeacherID) REFERENCES Teachers(TeacherID)
);

CREATE TABLE Enrollments (
    EnrollmentID NUMBER PRIMARY KEY,
    StudentID NUMBER,
    CourseID NUMBER,
    Grade NUMBER(3, 2),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

```
