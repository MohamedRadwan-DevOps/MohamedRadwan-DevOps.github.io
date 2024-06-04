---
layout: post
title:  "The Relational Algebra of Ramez Elmasri as MSSQL 2008 DB"
date:   2011-01-10 07:40:05 +0100
---

I used this post as DB SQL Kata, it's really perfect for this purpose, just give it a try to
finish all these queries in **5 minutes or less** from time to time and
you will see how this will help you:-) enjoy

From long time ago and I want to create this post that cover **Chapter 6, The Relational Algebra
and Calculus by Ramez Elmasri and Shamkant B. Navathe of Fundamentals of Database Systems,** 

I study this book in the Pre-Master and of course it's a great book, when I prepare for my exam I search for the Database as MDF file or MS SQL script file but I didn't found it so I decide to post an article that has the database and answer all question of Chapter 6 using SQL statements So you can download the scripts that create the database and insert the exactly data exist in Chapter 6 in the database, just click on the following link

[![Download](/assets/images/2011/01/download.jpg)](/assets/images/2017/08/Elmasri.zip)

So let's start by introduce the schema

![Schema](/assets/images/2011/01/Schema.png)

And now let's see the tables with the data that will be used throughout the chapter

![Employee](/assets/images/2011/01/Employee.png)

![Department](/assets/images/2011/01/Department.png)

![Dept_Locations](/assets/images/2011/01/Dept_Locations.png)

![Works_on](/assets/images/2011/01/Works_on.png)

![Instructor](/assets/images/2011/01/Instructor.png)

![Student](/assets/images/2011/01/Student.png)

The used Keywords

- intersect
- union
- except
- in
- not in
- is null
- is not null

Here is the code 

```sql

use CompanyElmasri
--Select the EMPLOYEEs whose department # is 4 
select Employee.Fname, Department.Dname,Department.Dnumber from Employee join Department on Employee.Dno =Department.Dnumber where Department.Dnumber =4
--==========================================================================
--Select the EMPLOYEEs whose salary > $30,000 
select Employee.Fname, Employee.Salary from Employee where Employee.Salary > 30000
--==========================================================================
--Intersection 
select Students.Fname from Students intersect select Instructors.Fname from Instructors 
-- intersection using join 
select Students.Fname from Students join Instructors on Students.InstructorId=Instructors.Id
--==========================================================================
--Union 
select Students.Fname from Students union select Instructors.Fname from Instructors
--==========================================================================
--difference student - instructors 
select Students.Fname from Students EXCEPT select Instructors.Fname from Instructors 
--difference instructors - student 
select Instructors.Fname from Instructors EXCEPT select Students.Fname from Students
--==========================================================================
--Give the SSNs of those managers have dependent(s). 
select Employee.Fname,Employee.Ssn from Employee where Employee.Ssn in(select distinct Dependent.Essn from Dependent)
--==========================================================================
--Give the SSNs non-manager employees 
select Employee.Fname , Employee.Ssn from Employee where Employee.Ssn not in (select distinct Employee.Super_ssn from Employee where Employee.Super_ssn is not null)
--==========================================================================
--Give the SSNs of employees who are both supervisors and supervisees 
select Employee.Fname,Employee.Ssn from Employee where Employee.Ssn in (select distinct Employee.Super_ssn from Employee) and Employee.Super_ssn is not null
--==========================================================================
--To find the dependents' names of all female employees 
select Employee.Fname, Dependent.Dependent_name from Dependent join Employee on Employee.Ssn=Dependent.Essn where Employee.Sex = 'F'
--==========================================================================
--List the names of those departments that have at least one female employee whose salary >= $25000. 
select distinct Department.Dname,Employee.Sex from Department join Employee on Employee.Dno=Department.Dnumber where Employee.Sex='F' and Employee.Salary >= 25000
--==========================================================================
--List the Names and SSNs of the managers of the above departments 
select Employee.Fname,Employee.Ssn, Department.Dname from Employee join Department on Employee.Dno=Department.Dnumber where Employee.Ssn in (select Employee.Super_ssn from Employee)
--==========================================================================
--find the dependents' names of all female employees 
select Dependent.Dependent_name from Dependent join Employee on Dependent.Essn =Employee.Ssn where Employee.Sex='F'
--==========================================================================
--List names and SSNs of those EMPLOYEE who work on some project(s) located in Houston 
select distinct Employee.Fname, Project.Plocation from Employee join Works_On on Employee.Ssn=Works_On.Essn join Project on Works_On.Pno=Project.Pnumber where Project.Plocation='Houston'
--==========================================================================
--List the names and birth dates of all female dependents born after 1980 
select Dependent.Dependent_name,Dependent.Bdate from Dependent where Dependent.Bdate >'1980'
--==========================================================================
--List the names of all employees who earns salary > $10,000 but does not supervise anyone 
select Employee.Fname from Employee where Employee.Salary > 10000 and Employee.Ssn not in (select distinct Employee.Super_ssn from Employee where Employee.Super_ssn is not null)
--==========================================================================
--Finished 

 ```

