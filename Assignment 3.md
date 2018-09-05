# Assignment 3

#### 1.	The HR department needs a report of all employees. Write a query to display the last name, department number, and department name for all the employees.

```select last_name as 'Last Name', department_id as 'Department ID', department_name from employees e inner join departments d on e.department_id = d.department_id;```

---

#### 2. 	The HR department needs a report of employees in Toronto. Display the last name, job, department number, and the department name for all employees who work in Toronto.

```select last_name as 'Last Name', job_id as 'Job ID', d.department_id as 'Department ID', department_name as 'Department Name' from employees e inner join departments d on e.department_id = d.department_id inner join locations l on d.location_id=l.location_id where l.city = "Toronto";```

---

#### 3. 	Create a report to display employees� last name and employee number along with their manager�s last name and manager number. Label the columns Employee, Emp#, Manager, and Mgr#, respectively. 

```select e1.last_name as 'Employee(Last Name)',e1.employee_id as 'Employee ID', e2.first_name as 'Manager(First Name)' from employees e1 inner join employees e2 on e1.manager_id = e2.employee_id;```

---

#### 4. 	WAQ to display all employees including King, who has no manager. Order the results by the employee number. 

```select * from employees group by employee_id;```

---

#### 5.	Create a report for the HR department that displays employee last names, department numbers, and all the employees who work in the same department as a given employee. Give each column an appropriate label.

```select last_name as 'Last Name', department_id as 'Department ID' from employees where department_id = (select department_id from employees where last_name = 'Davies');```

---

#### 6. 	The HR department needs a report on job grades and salaries. To familiarize yourself with the JOB_GRADES table, first show the structure of the JOB_GRADES table. Then create a query that displays the name, job, department name, salary, and grade for all employees.

```select e.first_name, e.last_name, (case e.job_id
		when 'AD_PRES' then 'A'
		when 'ST_MAN' then 'B'
		when 'IT_PROG' then 'C'
		when 'SA_REP' then 'D'
		when 'ST_CLERK' then 'E'
		else 0
	end) AS 'Grade', d.department_name from employees e inner join departments d on e.department_id = d.department_id;
  ```
  
  ---

#### 7. 	WAQ to determine the names of all the employees who were hired after Davies. Create a query to display the name and hire date of any employee hired after employee Davies.

```select concat(first_name, ' ', last_name) as 'Name', hire_date as 'Hire Date' from employees where hire_date > (select hire_date from employees where last_name = 'Davies' );```

---

#### 8. 	Write a query to display the last name and hire date of  any employee in the same department as Zlotkey. Exclude Zlotkey.

``` select last_name, hire_date, department_id from employees where last_name != 'Zlotkey' and department_id in (select department_id from employees where last_name = 'Zlotkey') ;```

---

#### 9. 	Create a query to display the employee numbers and last names of all employees who earn more than the average salary. Sort the results in ascending order of salary.

``` select employee_id, last_name, salary from employees where salary > (select avg(salary) from employees);```

---

#### 10. Write a query that displays the employee numbers and last names of all employees who work in a department with any employee whose last name contains a 'u'. 

```select employee_id, last_name from employees where department_id in (select department_id from employees where last_name like '%u%');```

---

#### 11. Display the last name, department number, and job ID of all employees whose	department location ID is 1700.

``` select last_name, d.department_id, job_id, d.location_id from employees e inner join departments d on e.department_id = d.department_id where d.location_id = 1700;```

---

#### 12. Display the last name and salary of every employee who reports to King.

```select last_name, salary from employees where manager_id in (select employee_id from employees where last_name = 'King');```

---
        
#### 13. Display the department number, last name, and job ID for every employee in the Executive department.

```select d.department_id, e.last_name, e.job_id, d.department_name from employees e inner join departments d on e.department_id = d.department_id where d.department_name = 'Executive';```

---
        
#### 14. WAQ  to display the employee numbers, last names, and salaries of all employees who earn more than the average salary and who work in a department with any employee with a u in their name.

```select employee_id, last_name, salary from employees where salary > (select avg(salary) from employees) and department_id in (select department_id from employees where last_name like '%u%');```

