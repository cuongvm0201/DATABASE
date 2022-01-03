```sql
CREATE DATABASE school
```

**_Tạo bảng teacher_**
```sql
CREATE TABLE teacher(
    id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    mobile VARCHAR NOT NULL,
    address TEXT NOT NULL
)
```

**_Thêm dữ liệu bảng teacher_**
```sql
INSERT INTO teacher(id, name, email, mobile, address) VALUES (11,'Tùng','tung@gmail.com','01233367899','HN');
INSERT INTO teacher(id, name, email, mobile, address) VALUES (22,'Hoàng','hoang@gmail.com','01244467899','BG');
INSERT INTO teacher(id, name, email, mobile, address) VALUES (33,'Minh','minh@gmail.com','01255567899','HY');
```
-------------------------------------------------------------------------------------------------------------------
**_Tạo bảng class_**
```sql
CREATE TABLE class (
id INT PRIMARY KEY,
name TEXT NOT NULL,
id_teacher INT NOT NULL,
FOREIGN KEY (id_teacher) REFERENCES teacher(id)
)
```

**_Thêm dữ liệu bảng class_**
```sql
INSERT INTO class(id, name, id_teacher) VALUES (1,'Lớp A',11);
INSERT INTO class(id, name, id_teacher) VALUES (2,'Lớp B',22);
INSERT INTO class(id, name, id_teacher) VALUES (3,'Lớp C',33);
```
-------------------------------------------------------------------------------------------------------------------
**_Tạo bảng student_**
```sql
CREATE TABLE student(
id INT PRIMARY KEY,
name TEXT NOT NULL,
birthday DATE NOT NULL,
address TEXT NOT NULL,
mobile VARCHAR(11) NOT NULL,
email TEXT NOT NULL,
id_class INT NOT NULL,
FOREIGN KEY (id_class) REFERENCES class(id)
)
```
**_Thêm dữ liệu bảng student_**
```sql
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (1111,'Tuấn','1991-1-1','HN','01224267899','A@gmail.com',1);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (2222,'Dương','1990-2-2','BN','03535456899','B@gmail.com',2);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (3333,'Dung','1990-3-3','HCM','01535567899','C@gmail.com',2);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (4444,'Trang','1992-4-4','HY','01222267899','D@gmail.com',1);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (5555,'Toàn','1993-5-5','TN','01333367899','E@gmail.com',3);
```
-------------------------------------------------------------------------------------------------------------------
**_Tạo bảng subject_**
```sql
CREATE TABLE subject(
id INT PRIMARY KEY,
name TEXT NOT NULL
)
```
**_Thêm dữ liệu bảng subject_**
```sql
INSERT INTO subject(id, name) VALUES (111,'monhoc1');
INSERT INTO subject(id, name) VALUES (222,'monhoc2');
INSERT INTO subject(id, name) VALUES (333,'monhoc3');
```
-------------------------------------------------------------------------------------------------------------------
**_Tạo bảng point_**
```sql
CREATE TABLE point(
id INT PRIMARY KEY AUTO_INCREMENT,
id_subject INT NOT NULL,
FOREIGN KEY (id_subject) REFERENCES subject(id),
id_student INT NOT NULL,
FOREIGN KEY (id_student) REFERENCES student(id),
point FLOAT NOT NULL
)
```
**_Thêm dữ liệu bảng point_**
```sql
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,1111,9.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,1111,7.2);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,1111,8.3);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,2222,8.2);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,2222,8.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,2222,9.1);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,3333,7.7);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,3333,6.6);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,3333,8.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,4444,8.0);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,4444,7.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,4444,8.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,5555,6.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,5555,6.5);
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,5555,6.5);
```
