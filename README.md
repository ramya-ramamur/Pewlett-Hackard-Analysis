# Pewlett-Hackard-Analysis

# Overview of Project

Pewlett Hackard, a very large organization has a large chunk of employees are reaching retirement age. The purpose of this analysis is to conduct a Database analysis on a set of 6 csv files pertaining to employee background information in order to find out how many current employees will be retiring and which departments these retiring employees work in so the organization can plan accordingly. 

The analysis will show 
1. The Number of Retiring Employees by Title
2. Identify employees who are eligible to participate in a mentorship program.

### Resources
* Data Sources: titles.csv, salaries.csv, employees.csv, dept_manager.csv, dept_emp.csv, departments.csv
* Software: PostgreSQL 12.5, quickdatabasediagrams.com, PgAdmin 4.20

# Entity Relationship Diagram
An ERD (Entity Relationship Diagram) is used to visualize the relationship between the data sources and the employee structure of the company. 

<img width="660" alt="EmployeeDB1" src="https://user-images.githubusercontent.com/75961057/145745495-4297741e-f7f8-4b18-a830-d0d87edc3266.png">

# Results: 
###### 1. From The Number of Retiring Employees by Title Analysis
* 90,398 employees will be retiring in the near future
* 64% of employees retiring in senior positions.
* Only 2 managers are due to retire.
###### 2.The Employees Eligible for the Mentorship Program Analysis
* 1,549 employees set to retire are eligible for the mentorship program

 ### Deliverable 1: The Number of Retiring Employees by Title 
 
 Using the ERD created as a reference, a Retirement Titles and count of Retiring Titles tables that holds all the titles of current employees who were born between January 1, 1952 and December 31, 1955 is created by writing SQL queries. 
 
 * Retirement Titles Table queries emp_no, first_name, and last_name columns from the Employees table(employees.csv) and title, from_date, and to_date columns from the Titles table by joining the tables on the primary key. Then the data is filtered on the birth_date column to retrieve the employees who were born between 1952 and 1955. Then, ordered by the employee number.
 * Unique Titles Table is then created by querying the Retirement Titles Table to retrieve the employee number, first and last name, and title columns using DISTINCT ON statement. 

 <img width="839" alt="Screen Shot 2021-12-12 at 7 23 24 PM" src="https://user-images.githubusercontent.com/75961057/145747509-9880317d-29db-480f-b68a-7cba30f90d42.png">
 
* Another query is written to retrieve the number of employees by their most recent job title who are about to retire from the Unique Titles Table

<img width="456" alt="Screen Shot 2021-12-12 at 7 36 27 PM" src="https://user-images.githubusercontent.com/75961057/145748552-74a71ba1-a744-4565-8672-0cdb4ca66f89.png">

### Deliverable 2: The Employees Eligible for the Mentorship Program

A Mentorship Eligibility table is created that holds the employees who are eligible to participate in a mentorship program. This table is created by querying emp_no, first_name, last_name, and birth_date columns from the Employees table and retrieving the from_date and to_date columns from the Department Employee table joining the tables on the primary key and using DISTINCT ON statement. 

<img width="884" alt="Screen Shot 2021-12-12 at 7 39 19 PM" src="https://user-images.githubusercontent.com/75961057/145748736-aef15af1-94db-4d3c-8c24-2d56c7194e83.png">

# Summary

* There are 90,398 roles that will need to be filled in the next four years from Senior Engineer to Manager levels across seven designations in the company as the "Silver Tsunami" makes an impact. 
* 1,549 employees are available for the mentorship program, to mentor 90,398 employees, which means that every mentor will have ~60 employees to mentor which is disproportionate number. There are not enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees.
