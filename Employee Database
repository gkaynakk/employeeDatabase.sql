
CREATE TABLE DEPARTMENTS
(
dept_no int not null IDENTITY PRIMARY KEY,
dept_name varchar(20) not null,
location varchar(20) not null
) 

DROP TABLE DEPARTMENTS
SELECT * FROM DEPARTMENTS 
INSERT INTO DEPARTMENTS VALUES('finance','tvm')
INSERT INTO DEPARTMENTS VALUES('testing','klm')
INSERT INTO DEPARTMENTS VALUES('design','ekm')
INSERT INTO DEPARTMENTS VALUES('coding','tvm')
INSERT INTO DEPARTMENTS VALUES('hr','new york')
INSERT INTO DEPARTMENTS VALUES('marketing','knr')






----------------------------

CREATE TABLE EMPLOYEES
(
emp_no int not null primary key,
emp_name varchar(20),
job varchar(20) not null,
mgr varchar(20) not null,
hire_date datetime not null,
dept_no int not null,
sal money,
comm money
FOREIGN KEY (dept_no) REFERENCES DEPARTMENTS (dept_no)on delete cascade on update cascade
) 



DROP TABLE EMPLOYEES
SELECT * FROM EMPLOYEES
DELETE FROM EMPLOYEES
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(100,'geo','programming','D04','2006/10/10',4,6000,2000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(200,'tom','designing','D03','2006/09/14',3,10000,5000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(300,'shyam','accounting','D01','2006/11/10',1,10000,5000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(400,'kiran','tester','D02','2006/11/14',2,5000,1000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(500,'tiss','tester','D05','2006/12/11',5,10000,3000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(600,'jim','tester','D05','2006/11/14',5,2000,1000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(7756,'ann','tester','D05','2006/11/20',5,90000,5000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(800,'tina','tester','D05','2006/10/14',5,10000,5000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(900,'riju','salesman','D06','2006/10/14',6,17000,5000)
INSERT  INTO EMPLOYEES (emp_no,emp_name,job,mgr,hire_date,dept_no,sal,comm) VALUES(230,'sijo','salesman','D06','2006/10/14',6,6000,5000)

          Simple Queries



1.Get the name of all employees

SELECT emp_name from EMPLOYEES


2.Get details of all employees


SELECT * from employees


3.Get details of all departments

SELECT * FROM DEPARTMENTS


4.Get emp. Name & salary of  employees having salary > 7600


SELECT emp_name,sal FROM EMPLOYEES WHERE sal>7600 


5.Get the listing of all columns in employee table

sp_help EMPLOYEES
--(similar to describe table in oracle)


6.Display the name, no & salary of employees in the ascending order of their names
--Ascending order is the default sorting order hence no need of specifying the ASC explicitly

  SELECT emp_name,emp_no,sal FROM EMPLOYEES ORDER BY emp_name ASC
or
SELECT emp_name,emp_no,sal FROM EMPLOYEES ORDER BY emp_name 

7.Select the details of employees arranged in the descending order of their names


  SELECT * FROM EMPLOYEES ORDER BY emp_name DESC 

8.Display the names, deptnumbers and salary of employees in ascending order of dept. nos 
and descending order of salary.

  SELECT dept_no,sal FROM EMPLOYEES    ORDER BY dept_no ASC,sal DESC

9.Get the details of an employee with employee no 7756.


  SELECT * FROM EMPLOYEES WHERE emp_no=7756


10.Get the details of all salesmen in the descending order of salaries


  SELECT * FROM EMPLOYEES WHERE JOB='salesman'


11.Get the name of employees in the company who earn >900$


  SELECT emp_name FROM EMPLOYEES WHERE sal>900

12.Display the emp first name last name in UPPERCASE

select upper(emp_name) FROM EMPLOYEES 



13.Display the emp name, length of the name string

 SELECT  emp_name, len(emp_name) FROM EMPLOYEES



JOINS ,GROUPING

1.	Get the employee details & dept. names.

    SELECT e.emp_name,e.job,d.dept_name,e.sal  FROM DEPARTMENTS d inner join EMPLOYEES e ON d.dept_no=e.dept_no

2.	Select the employee name, dept. name of employees with department number value greater than 10.

    SELECT e.emp_name,d.dept_name  FROM DEPARTMENTS d inner join EMPLOYEES e ON d.dept_no=e.dept_no and d.dept_no > 5


3.	Calculate the total amount spent on salary.
User defined headings can be given

    SELECT 'Total salary'=sum(sal) FROM EMPLOYEES


4.	Find the maximum and minimum salary of the employees.

    SELECT 'Maximum'=max(sal), 'Minimum'=min(sal) FROM EMPLOYEES 


5.	List the different job roles and the number of employees in that job roles.

 Here count of the employees are required for each job role
    SELECT  job , COUNT(emp_no) FROM EMPLOYEES GROUP BY job

     

6.	List the companys average salary for a given job within a dept.

    SELECT 'Avg Salary'=AVG(sal),dept_no,job  FROM EMPLOYEES 
group by dept_no,job
    
7.	Order the output of the above query that highest average salary comes on the top so that we can figure out which depts and jobs pay most
 
SELECT 'Avg Salary'=AVG(sal),deptno,job  FROM EMPLOYEES 
group by dept_no,job order by avg(sal) desc.

8.	Modify the above query so that it displays avg salary which is greater than 2000 $

    SELECT 'Avg Salary'=AVG(sal),dept_no,job  FROM EMPLOYEES 
group by dept_no,job having avg(sal)>2000
order by avg(sal) desc.



Sub Queries:

1.	Get Name, Dept number salaries for employees working in New York.
   
    SELECT emp_name, sal FROM EMPLOYEES  WHERE dept_no IN (SELECT dept_no FROM DEPARTMENTS  WHERE  location='new york')
    

2.get	Dept. no, emp name of employees in depts (accounting & sales)

 here only deptnos,empnames are asked.

 
SELECT emp_name, deptno FROM EMPLOYEES  WHERE dept_no IN (SELECT dept_no from departments where dept_name IN('Sales','Accounts')
     
3.    get depts. and job titles of emps where avg (sal) is greater than what the company pays to MARTIN the sales man.


     SELECT dept_no,avg(sal),job FROM EMPLOYEES group by dept_no,job having avg(sal)>(SELECT sal FROM EMPLOYEES  where e_name='MARTIN')  






