# DATABASEBAITAP <h2>
# CREATE DATABASE school <h3>

CREATE TABLE teacher( </br>
    id INT PRIMARY KEY, </br>
    name TEXT NOT NULL, </br>
    email TEXT NOT NULL, </br>
    mobile VARCHAR NOT NULL, </br>
    address TEXT NOT NULL </br>
)</br>

INSERT INTO teacher(id, name, email, mobile, address) VALUES (11,'A1','A1@gmail.com','01233367899','HN');</br>
INSERT INTO teacher(id, name, email, mobile, address) VALUES (22,'B1','A1@gmail.com','01244467899','HN');</br>
INSERT INTO teacher(id, name, email, mobile, address) VALUES (33,'C1','A1@gmail.com','01255567899','HN');</br>

-----------------------------</br>
CREATE TABLE class ( </br>
    id INT PRIMARY KEY,</br>
    name TEXT NOT NULL,</br>
    id_teacher INT NOT NULL,</br>
    FOREIGN KEY (id_teacher) REFERENCES teacher(id)</br>
)</br>

INSERT INTO class(id, name, id_teacher) VALUES (1,'lop1',11);</br>
INSERT INTO class(id, name, id_teacher) VALUES (2,'lop2',22);</br>
INSERT INTO class(id, name, id_teacher) VALUES (3,'lop3',33);</br>

-----------------------------</br>

CREATE TABLE student(</br>
   id INT PRIMARY KEY,</br>
   name TEXT NOT NULL,</br>
   birthday DATE NOT NULL,</br>
   address TEXT NOT NULL,</br>
   mobile VARCHAR NOT NULL,</br>
   email TEXT NOT NULL,</br>
   id_class INT NOT NULL,</br>
   FOREIGN KEY (id_class) REFERENCES class(id)</br>
)</br>
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (1111,'A','1991-1-1','HN','A@gmail.com','01234567899',1);</br>
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (2222,'B','1990-2-2','BN','B@gmail.com','01234567899',2);</br>
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (3333,'C','1990-3-3','HCM','C@gmail.com','01234567899',2);</br>
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (4444,'D','1992-4-4','HY','D@gmail.com','01234567899',1);</br>
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (5555,'E','1993-5-5','TN','E@gmail.com','01234567899',3);</br>
-----------------------------</br>

CREATE TABLE subject(</br>
    id INT PRIMARY KEY,</br>
    name TEXT NOT NULL</br>
)</br>
INSERT INTO subject(id, name) VALUES (111,'monhoc1');</br>
INSERT INTO subject(id, name) VALUES (222,'monhoc2');</br>
INSERT INTO subject(id, name) VALUES (333,'monhoc3');</br>
-----------------------------</br>
CREATE TABLE point(</br>
    id INT PRIMARY KEY AUTO_INCREMENT,</br>
    id_subject INT NOT NULL,</br>
    FOREIGN KEY (id_subject) REFERENCES subject(id),</br>
    id_student INT NOT NULL,</br>
    FOREIGN KEY (id_student) REFERENCES student(id),</br>
    point FLOAT NOT NULL</br>
)</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,1111,9.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,1111,7.2);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,1111,8.3);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,2222,8.2);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,2222,8.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,2222,9.1);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,3333,7.7);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,3333,6.6);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,3333,8.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,4444,8.0);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,4444,7.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,4444,8.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,111,5555,6.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,222,5555,6.5);</br>
INSERT INTO point(id, id_subject, id_student, point) VALUES (null,333,5555,6.5);</br>

