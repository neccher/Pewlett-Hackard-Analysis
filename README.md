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
