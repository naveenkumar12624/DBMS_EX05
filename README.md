# Exp-5 SQL query to fetch duplicate records having matching data in some fields of a table.
## AIM:
To write a sql query to fetch duplicate records having matching data in some fields of a table.
## PROCEDURE:
### STEP 1:
create database ORG.
### STEP 2:
create table Worker,Bonus,Title.
### STEP 3:
Insert Value to the tables.
### STEP 4:
Select records having matching data in some fields.
## PROGRAM:
```sql
CREATE DATABASE ORG;
SHOW DATABASES;
USE ORG;
CREATE TABLE Worker (
WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
FIRST_NAME CHAR(25),
LAST_NAME CHAR(25),
SALARY INT(15),
JOINING_DATE DATETIME,
DEPARTMENT CHAR(25)
);
INSERT INTO Worker
(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE,
DEPARTMENT) VALUES
(001, 'Monika', 'Arora', 100000, '14-02-20
09.00.00', 'HR'),
(002, 'Niharika', 'Verma', 80000, '14-06-11
09.00.00', 'Admin'),
(003, 'Vishal', 'Singhal', 300000, '14-02-20
09.00.00', 'HR'),
(004, 'Amitabh', 'Singh', 500000, '14-02-20
09.00.00', 'Admin'),
(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00',
'Admin'),
(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00',
'Account'),
(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00',
'Account'),
(008, 'Geetika', 'Chauhan', 90000, '14-04-11
09.00.00', 'Admin');
CREATE TABLE Bonus (
WORKER_REF_ID INT,
BONUS_AMOUNT INT(10),
BONUS_DATE DATETIME,
FOREIGN KEY (WORKER_REF_ID)
REFERENCES Worker(WORKER_ID)
ON DELETE CASCADE
);
INSERT INTO Bonus
(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
(001, 5000, '16-02-20'),
(002, 3000, '16-06-11'),
(003, 4000, '16-02-20'),
(001, 4500, '16-02-20'),
(002, 3500, '16-06-11');
CREATE TABLE Title (
WORKER_REF_ID INT,
WORKER_TITLE CHAR(25),
AFFECTED_FROM DATETIME,
FOREIGN KEY (WORKER_REF_ID)
REFERENCES Worker(WORKER_ID)
ON DELETE CASCADE
);
INSERT INTO Title
(WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
(001, 'Manager', '2016-02-20 00:00:00'),
(002, 'Executive', '2016-06-11 00:00:00'),
(008, 'Executive', '2016-06-11 00:00:00'),
(005, 'Manager', '2016-06-11 00:00:00'),
(004, 'Asst. Manager', '2016-06-11 00:00:00'),
(007, 'Executive', '2016-06-11 00:00:00'),
(006, 'Lead', '2016-06-11 00:00:00'),
(003, 'Lead', '2016-06-11 00:00:00');
SELECT DEPARTMENT, COUNT(*) as duplicate_count
FROM Worker
GROUP BY DEPARTMENT
HAVING COUNT(*) > 1;
```
## OUTPUT:
![image](https://github.com/Karthikeyan21001828/DBMS_EX05/assets/93427303/026191c8-ce92-43e3-b1af-46f0579e7a20)
## RESULT:
A sql query to fetch duplicate records having matching data in some fields of a table has been executed.
