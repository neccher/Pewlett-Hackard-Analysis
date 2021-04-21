# Pewlett-Hackard-Analysis

## Overview

Pewlett-Hackard has a large number of employees from the Baby Boomer Generation.  As these employees approach retirement age, Pewlett-Hackard expects they will need to fill thousands of job openings these Boomers will be leaving behind.  In order to combat decreases in productivity, we have been asked to perform an analysis on PH's employees and determine the number of employees retiring per job title as well as identify employees who are eligible to participate in a mentorship program.  These numbers could prove crucial in preparing for the approaching "silver tsunami."

## Results

There are a few takeaways that Pewlett_Hackard should be aware of and try to act upon immediately:

- Senior level employees will be the most impacted
  - There are 90,398 current employees retiring soon.  Of those ~90K, 57,668 of have Senior in their Title.
  (retiring_titles table) ![image](https://user-images.githubusercontent.com/79211628/115584681-9395f200-a290-11eb-9831-024f355bc3f4.png)
  
  Pewlett-Hackard must start looking internally or externally for qualified candidates to fill these senior positions.

- Mentorship Eligibility has a larger representation of Senior level employees
  - Luckily, the representation of mentorship eligible employees also skews heavy towards Senior level employees.
  (Count of emp_no in mentorship_eligibility table Grouped by Title) 
  
  ![image](https://user-images.githubusercontent.com/79211628/115585999-c096d480-a291-11eb-8d4b-8f2cd6fe61a3.png)

  PH should recruit employees to figure out replacements for these Senior level positions earlier rather than later in order to take advantage of the mentorship program before the Boomers leave.

- Development, Production, and Sales are the hardest hit departments
  - PH cannot only focus on replacing leadership.  It is also important to look at which departments will see the largest out flows of workers. (Retiring Workers Grouped by Department) ![image](https://user-images.githubusercontent.com/79211628/115587298-25066380-a293-11eb-9be7-47a3092479be.png)
  
  As you can see, most of the exodus from Pewlett-Hackard will be coming from three departments and should be prioritized in finding new employees to take over the work. 

- Development, Production, and Sales also have the highest number of employees eligible for the mentorship program but nowhere near enough to mentor a replacement for each retiree.
  - There is a siginificant gap between the number of retirees retiring in each department and the number of retirees who are also eligible to become a mentor in each department.
  (Count of emp_no in mentorship_eligibility table Grouped by Title) ![image](https://user-images.githubusercontent.com/79211628/115588103-02287f00-a294-11eb-8eff-97b39909d585.png)

## Summary
- How many roles will need to be filled as the "silver tsunami" begins to make an impact?
	- By looking at the count of emp_no in the unique_titles table, we see that 90,398 positions will need to be filled.
	- 
- Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
	- 
- Additional queries:
  - Unfortunately for Pewlett-Hackard, they will be in dire need of leadership after the "silver tsunami."  Every single one of their departments with a manager is managed by an employee expected to retire soon.  By writing a query to look at information in the manager_info table and connecting the retirement_info table using `INNER JOIN`, the results set will only display managers who are also of retirement age.
  ```
  SELECT mi.dept_no
	, mi.dept_name
	, ri.emp_no
	, ri.first_name
	, ri.last_name
  FROM manager_info mi
  INNER JOIN retirement_info ri
	  ON mi.emp_no = ri.emp_no 
  ```
  The output confirms that every current manager is in the cohort retiring soon.
  
- Even worse news for Pewlett-Hackard is that the retiring employees have a lower average salary ($52,909.00) than their non-retiring counterparts ($52,997.00), despite their level of seniority and management positions.  This means that they should expect to have to pay the replacements of these soon to be retirees more than what the current position is requiring.
```
-- Create Unique Retiring Salaries Table
SELECT DISTINCT ON (rt.emp_no) rt.emp_no
	, rt.first_name
	, rt.last_name
	, s.salary
INTO unique_retirement_salaries
FROM salaries s
INNER JOIN retirement_titles rt
	ON s.emp_no = rt.emp_no
ORDER BY rt.emp_no, s.to_date DESC

-- Create Unique NonRetiring Salaries Table
SELECT DISTINCT ON (e.emp_no) e.emp_no
	, e.first_name
	, e.last_name
	, s.salary
INTO unique_non_retirement_salaries
FROM salaries s
INNER JOIN employees e
	ON s.emp_no = e.emp_no
LEFT JOIN retirement_titles rt
	ON s.emp_no = rt.emp_no
WHERE rt.emp_no is null
ORDER BY e.emp_no, s.to_date DESC

-- Sum of Retiring Salaries
SELECT SUM(salary)
FROM unique_retirement_salaries

-- Sum of NonRetiring Salaries
SELECT SUM(salary)
FROM unique_non_retirement_salaries

-- Count of Retiring employees
SELECT COUNT(emp_no)
FROM unique_retirement_salaries

-- Count of NonRetiring employees
SELECT COUNT(emp_no)
FROM unique_non_retirement_salaries

--Average of Retirement Salaries 
SELECT (SUM(salary)/COUNT(emp_no)) AS AverageSalary
FROM unique_retirement_salaries

--Average of NonRetirement Salaries 
SELECT (SUM(salary)/COUNT(emp_no)) AS AverageSalary
FROM unique_non_retirement_salaries
```
