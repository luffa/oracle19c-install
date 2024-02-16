# Create Table

### คำสั่งในการสร้างตาราง 

```sql
CREATE TABLE Table1 (
colkey NUMBER PRIMARY KEY,
column1 datatype,
column2 datatype,
FOREIGN KEY (column2) REFERENCES Table2(table2key2)
)
```

```sql
CREATE TABLE Students (
    StudentID NUMBER PRIMARY KEY,
    Name VARCHAR2(100 CHAR),
    Age NUMBER,
    Gender VARCHAR2(10 CHAR),
    GradeLevel NUMBER,
    GPA NUMBER(3, 2)
);

CREATE TABLE Teachers (
    TeacherID NUMBER PRIMARY KEY,
    Name VARCHAR2(100 CHAR),
    Age NUMBER,
    Gender VARCHAR2(10 CHAR),
    Department VARCHAR2(100 CHAR)
);

CREATE TABLE Courses (
    CourseID NUMBER PRIMARY KEY,
    CourseName VARCHAR2(100 CHAR),
    Description VARCHAR2(4000 CHAR),
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
### Insert data to table

```sql
-- Inserting sample data into Students table
INSERT INTO Students (StudentID, Name, Age, Gender, GradeLevel, GPA)
VALUES (1, 'John Doe', 18, 'Male', 12, 3.8);

INSERT INTO Students (StudentID, Name, Age, Gender, GradeLevel, GPA)
VALUES (2, 'Jane Smith', 17, 'Female', 11, 3.9);

-- Inserting sample data into Teachers table
INSERT INTO Teachers (TeacherID, Name, Age, Gender, Department)
VALUES (101, 'Mr. Brown', 35, 'Male', 'Mathematics');

INSERT INTO Teachers (TeacherID, Name, Age, Gender, Department)
VALUES (102, 'Ms. Johnson', 40, 'Female', 'Science');

-- Inserting sample data into Courses table
INSERT INTO Courses (CourseID, CourseName, Description, TeacherID, Credits)
VALUES (501, 'Algebra I', 'Introductory algebra course', 101, 4);

INSERT INTO Courses (CourseID, CourseName, Description, TeacherID, Credits)
VALUES (502, 'Biology', 'Study of living organisms', 102, 4);

-- Inserting sample data into Enrollments table
INSERT INTO Enrollments (EnrollmentID, StudentID, CourseID, Grade)
VALUES (1001, 1, 501, 92.5);

INSERT INTO Enrollments (EnrollmentID, StudentID, CourseID, Grade)
VALUES (1002, 2, 502, 88.0);

```
