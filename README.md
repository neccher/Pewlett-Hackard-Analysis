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

- Development, Production, and Sales also have the highest number of employees eligible for the mentorship program
  - Luckily, if PH can find replacements quickly, they will have plenty of mentors to make the transition for these hardest hit departments as smooth as possible.
  (Count of emp_no in mentorship_eligibility table Grouped by Title) ![image](https://user-images.githubusercontent.com/79211628/115588103-02287f00-a294-11eb-8eff-97b39909d585.png)

## Summary
- How many roles will need to be filled as the "silver tsunami" begins to make an impact?
- Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
- Additional queries:
  - Unfortunately for Pewlett-Hackard, they will be in dire need of leadership after the "silver tsunami."  Every single one of their departments with a manager is managed by an employee expected to retire soon.  By writing a query to look at information in the manager_info table and connecting the retirement_info table using `INNER JOIN`, the results set will only display managers who are also of retirment age.
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
