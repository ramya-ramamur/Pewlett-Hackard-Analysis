# Pewlett-Hackard-Analysis

# Overview of Project

Pewlett Hackard, a very large organization has a large chunk of employees are reaching retirement age. The purpose of this analysis is to conduct a Database analysis on a set of 6 csv files pertaining to employee background information in order to find out how many current employees will be retiring and which departments these retiring employees work in so the organization can plan accordingly. 

The analysis will show 
1. The Number of Retiring Employees by Title
2. Identify employees who are eligible to participate in a mentorship program.

### Entity Relationship Diagram
* Data Sources: titles.csv, salaries.csv, employees.csv, dept_manager.csv, dept_emp.csv, departments.csv
* Software: PostgreSQL 12.5, quickdatabasediagrams.com, PgAdmin 4.20

# Initial Analysis
An ERD (Entity Relationship Diagram) is used to visualize the relationship between the data sources and the employee structure of the company. 

<img width="660" alt="EmployeeDB1" src="https://user-images.githubusercontent.com/75961057/145745495-4297741e-f7f8-4b18-a830-d0d87edc3266.png">

# Results: 

 ### Deliverable 1: The Number of Retiring Employees by Title 
 Using the ERD created as a reference, a Retirement Titles and count of Retiring Titles tables that holds all the titles of current employees who were born between January 1, 1952 and December 31, 1955 is created by writing SQL queries. 
 
 * Retirement Titles Table queries emp_no, first_name, and last_name columns from the Employees table(employees.csv) and title, from_date, and to_date columns from the Titles table by joining the tables on the primary key. Then the data is filtered on the birth_date column to retrieve the employees who were born between 1952 and 1955. Then, ordered by the employee number.
 * Unique Titles Table is then created by querying the Retirement Titles Table to retrieve the employee number, first and last name, and title columns using DISTINCT ON statement. 
 
 <img width="839" alt="Screen Shot 2021-12-12 at 7 23 24 PM" src="https://user-images.githubusercontent.com/75961057/145747509-9880317d-29db-480f-b68a-7cba30f90d42.png">
 
* Another query is written to retrieve the number of employees by their most recent job title who are about to retire from the Unique Titles Table

<img width="456" alt="Screen Shot 2021-12-12 at 7 36 27 PM" src="https://user-images.githubusercontent.com/75961057/145748552-74a71ba1-a744-4565-8672-0cdb4ca66f89.png">

### Deliverable 2: The Employees Eligible for the Mentorship Program
A Mentorship Eligibility table is created that holds the employees who are eligible to participate in a mentorship program. This table is created by querying emp_no, first_name, last_name, and birth_date columns from the Employees table and retrieving the from_date and to_date columns from the Department Employee table joining the tables on the primary key and using DISTINCT ON statement. 



Number of Retiring Employees by Title
A total of 90,398 will be retiring in the near future
The majority of employees that will be retiring soon are in Senior positions
Only 2 managers are due to retire
Employees Eligible for Mentorship Program
1,549 employees set to retire are eligible for the mentorship program
Summary
As the "silver tsunami" begins to make an impact, there are 90,398 roles that will need to be filled across 7 different categories in the organization. Most of these are senior positions, and lukcily only 2 manager positions will be left to fill.
challenge_count

With 1,549 employees available for the mentorship program, it seems that there are not enough qualified employees ready for retirement in the departments to mentor the next generation of employees. Each mentor would have to have about 58 mentees, which is much too large of a workload for any employee, especially part-time retiring employees. By breaking down the mentorship eligible employees by department in the query below, we can see that the employees are proportionally spread to the employees that are retiring but there is still too few employees to mentor the retiring employees.
SELECT COUNT(title), title
FROM mentorship_eligibility
GROUP BY title
ORDER BY COUNT(title) DESC;
mentorship_eligible

However if we extend the mentorship eligibility by 1 year to employees born in 1964 there are 19,905 eligible employees which is much more manageable. The 'WHERE' line of the query extending the eligible employees and visualize the department breakdown of the extended filter is shown below.

WHERE (e.birth_date BETWEEN '1964-01-01' AND '1965-12-31')
extended_eligibility
