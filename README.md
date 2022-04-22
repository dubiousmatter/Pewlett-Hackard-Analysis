# Pewlett-Hackard-Analysis

## Overview
The company tasked us with helping to plan for tha mass wave of retirements looming for those workers born roughly between 1955 and 1965. In order to illustrate the "silver tsunami", we put together a series of tables formulated using the company database of employees. Those tables were able to show management the number of retiring employees by title and those employees elgible for the in-house mentorship program.

## Results
Our analysis produced several notable results which will be illustrative to management planning:

- There are roughly 72,000 employees who are within the specified retirement window of birth between 1955 and 1965
- Of those 72,000 retirement age employees, just over 50,000 are Senior Engineers or Senior Staff
- There are 10,375 Engineers or Assistant Engineers who could possibly be mentored up into senior roles
- There are 1,549 employees born in 1965 who are eligible for the company mentorship program

## Summary
Our analysis shows that roughly 72,000 roles will need to be filled as the "silver tsunami" begins to unfold. As we stated earlier, the vast majority of those positions will be in engineering. 

![image](https://user-images.githubusercontent.com/101157423/164774673-01cd343b-2b97-4744-901f-f72f09450610.png)

After running the following query to look for those employees who might be eligible for the mentorship program, we found a large number of potential mentors to get new employees up to speed.

- SELECT DISTINCT ON (e.emp_no)
- e.emp_no,
- e.first_name,
- e.last_name,
- e.birth_date,
- de.from_date,
- de.to_date,
- t.title
- INTO mentorship_all
- FROM employees AS e
- INNER JOIN dept_emp AS de
- ON (e.emp_no = de.emp_no)
- INNER JOIN titles AS t
- ON (e.emp_no = t.emp_no)
- WHERE (de.to_date = '9999-01-01')
	- AND (e.birth_date BETWEEN '1955-01-01' AND '1965-12-31')
- ORDER BY e.emp_no;

