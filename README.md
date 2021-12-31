# DATABASEBAITAP
# CREATE DATABASE school <h1>

## <table1>
CREATE TABLE teacher(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    mobile VARCHAR NOT NULL,
    address TEXT NOT NULL
)

INSERT INTO teacher(id, name, email, mobile, address) VALUES (11,'A1','A1@gmail.com','01233367899','HN');
INSERT INTO teacher(id, name, email, mobile, address) VALUES (22,'B1','A1@gmail.com','01244467899','HN');
INSERT INTO teacher(id, name, email, mobile, address) VALUES (33,'C1','A1@gmail.com','01255567899','HN');
## <table1>

-----------------------------

## <table2>
CREATE TABLE class (
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    id_teacher INT NOT NULL,
    FOREIGN KEY (id_teacher) REFERENCES teacher(id)
)

INSERT INTO class(id, name, id_teacher) VALUES (1,'lop1',11);
INSERT INTO class(id, name, id_teacher) VALUES (2,'lop2',22);
INSERT INTO class(id, name, id_teacher) VALUES (3,'lop3',33);
## <table2>

-----------------------------

## <table3>
CREATE TABLE student(
   id INT PRIMARY KEY,
   name TEXT NOT NULL,
   birthday DATE NOT NULL,
   address TEXT NOT NULL,
   mobile VARCHAR NOT NULL,
   email TEXT NOT NULL,
   id_class INT NOT NULL,
   FOREIGN KEY (id_class) REFERENCES class(id)
)

INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (1111,'A','1991-1-1','HN','A@gmail.com','01234567899',1);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (2222,'B','1990-2-2','BN','B@gmail.com','01234567899',2);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (3333,'C','1990-3-3','HCM','C@gmail.com','01234567899',2);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (4444,'D','1992-4-4','HY','D@gmail.com','01234567899',1);
INSERT INTO student(id, name, birthday, address, mobile, email, id_class) VALUES (5555,'E','1993-5-5','TN','E@gmail.com','01234567899',3);
## <table3>

-----------------------------

## <table4>
CREATE TABLE subject(
    id INT PRIMARY KEY,
    name TEXT NOT NULL
)
INSERT INTO subject(id, name) VALUES (111,'monhoc1');
INSERT INTO subject(id, name) VALUES (222,'monhoc2');
INSERT INTO subject(id, name) VALUES (333,'monhoc3');
## <table4>

-----------------------------

## <table5>
CREATE TABLE point(
    id INT PRIMARY KEY AUTO_INCREMENT,
    id_subject INT NOT NULL,
    FOREIGN KEY (id_subject) REFERENCES subject(id),
    id_student INT NOT NULL,
    FOREIGN KEY (id_student) REFERENCES student(id),
    point FLOAT NOT NULL
)
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
## <table5>
-----------------------------
