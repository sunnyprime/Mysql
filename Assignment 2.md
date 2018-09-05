# Assignment 2

#### 1. WAQ to show <employee last name> earns <salary> monthly but wants <3 times salary.>. Label the column Dream Salaries.

```select concat(last_name, ' earns ', salary, ' but wants ', salary*3) as 'Employees and Their Dream Salaries', salary*3 as 'Dream Salary' from employees;```

---

#### 2.Display each employee�s last name, hire date, and salary review date, which is the first Monday after six months of service. Label the column REVIEW. Format the dates to appear in the format similar to �Monday, the Thirty-First of July, 2000.�

```select last_name, hire_date, date_format((hire_date+interval 6 month)+7-(weekday(hire_date+interval 6 month)), '%Y-%m-%d') as 'Salary Review Date' from employees;```

---

#### 3. Display the last name, hire date, and day of the week on which the employee started. Label the column DAY. Order the results by the day of the week, starting with Monday.

```select last_name, hire_date, date_format((hire_date+interval 6 month)+ interval 7-(weekday(hire_date+interval 6 month)) day, '%Y-%m-%d') as 'Salary Review Date' from employees;```

---

#### 4. Create a query that displays the employees� last names and commission amounts. If an employee does not earn commission, show �No Commission.� Label the column COMM.

```select last_name as 'Last Name', ifnull(commission_pct,'No Commission')  as 'Commission'  from employees;```

---

#### 5. Using the Case function, write a query that displays the grade of all employees based on the value of the column JOB_ID, using the following data:
####	Job 			Grade	
####	AD_PRES			A	
####	ST_MAN			B	
####	IT_PROG			C	
####	SA_REP			D	
####	ST_CLERK		E	
####	None of the above	0

```select first_name, last_name, (case job_id
		when 'AD_PRES' then 'A'
		when 'ST_MAN' then 'B'
		when 'IT_PROG' then 'C'
		when 'SA_REP' then 'D'
		when 'ST_CLERK' then 'E'
		else 0
	end) AS 'Grade' from employees;
  ```
  
  ---

#### 6. Find the highest, lowest, sum, and average salary of all employees. Label the columnsas 	Maximum, Minimum, Sum, and Average, respectively. Round your results to the nearest whole 	number.

```select round(max(salary),0) 'Maximum', round(min(salary),0) 'Minimum', round(sum(salary),0) 'Total', round(avg(salary),0) 'Average' from employees;```

---

### 7. Modify the previous query to display the minimum, maximum, sum, and average salary for each job type.

```select round(max(salary),0) 'Maximum', round(min(salary),0) 'Minimum', round(sum(salary),0) 'Total', round(avg(salary),0) 'Average', job_id as 'Job ID' from employees group by job_id;```

---

#### 8.Write a query to display the number of people with the same job.

```select job_id as 'JOB_ID', count(employee_id) as '#EMPLOYEES' from employees group by job_id;```

---

#### 9. Create a report to display the manager number and the salary of the lowest-paid employee for that manager. Exclude anyone whose manager is not known. Exclude any groups where the minimum salary is $6,000 or less. Sort the output in descending order of salary.

```select manager_id, min(salary) from employees where manager_id is not NULL group by manager_id having min(salary) > 6000 order by min(salary) desc;```
 
