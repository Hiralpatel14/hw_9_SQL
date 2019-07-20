-- Exported from QuickDBD: https://www.quickdatabasediagrams.com/
-- Link to schema: https://app.quickdatabasediagrams.com/#/d/8N5Nie
-- NOTE! If you have used non-SQL datatypes in your design, you will have to change these here.

--Drop Table if exists Employees;
CREATE TABLE Employees (
    emp_no int Primary Key  NOT NULL,
    birth_date varchar(30)   NOT NULL,
    first_name varchar(30)   NOT NULL,
    last_name varchar(30)   NOT NULL,
    gender varchar(1)   NOT NULL,
    hire_date varchar(30)   NOT NULL
    );

--Drop Table if exists Departments;
CREATE TABLE Departments (
    dept_no varchar(4) PRIMARY KEY NOT NULL,
    dept_name varchar(30)   NOT NULL
);

--Drop Table if exists Dept_emp
CREATE TABLE Dept_emp (
    emp_no int   NOT NULL,
	dept_no varchar(4)   NOT NULL,
    from_date varchar(30)   NOT NULL,
    to_date varchar(30)   NOT NULL,
	Foreign key (emp_no) references Employees(emp_no), 
	Foreign key (dept_no) references Departments(dept_no)
);

--Drop Table if exists Dept_manager;
CREATE TABLE Dept_manager (
    dept_no varchar(4)  NOT NULL,
    emp_no int   NOT NULL,
    from_date varchar(30)   NOT NULL,
    to_date varchar(30)   NOT NULL,
	Foreign key (emp_no) references Employees(emp_no), 
	Foreign key (dept_no) references Departments(dept_no)
);

--Drop Table if exists Salaries;
CREATE TABLE Salaries (
    emp_no int   NOT NULL,
    salary int   NOT NULL,
    from_date varchar(30)   NOT NULL,
    to_date varchar(30)   NOT NULL
);

--Drop Table if exists Titles
CREATE TABLE Titles (
    emp_no int   NOT NULL,
    title varchar(30)   NOT NULL,
    from_date varchar(30)   NOT NULL,
    to_date varchar(30)   NOT NULL,
	Foreign key (emp_no) references Employees(emp_no)
);

select * from Employees
select * from Departments
select * from Dept_emp
select * from Dept_manager
select * from Salaries
select * from Titles

--1. List the following details of each employee: 
--employee number, last name, first name, gender, and salary.
select e.emp_no, e.last_name, e.first_name, e.gender, s.salary
from Employees as e 
left join Salaries as s 
on e.emp_no = s.emp_no
order by e.emp_no

--2. List employees who were hired in 1986.
select * from Employees
where hire_date between '1986-01-01'and '1987-01-01'

--3. List the manager of each department with the following information: 
-- department number, department name, 
--the manager's employee number, last name, first name, and start and end employment dates.
select d.dept_no, d.dept_name,dm.emp_no, e.last_name, e.first_name,dm.from_date Start_Date, dm.to_date End_Date
from Departments as d
inner join Dept_manager dm
on d.dept_no = dm.dept_no
inner join Employees as e
on e.emp_no= dm.emp_no

--4. List the department of each employee with the following information: 
--employee number, last name, first name, and department name.

select e.emp_no, e.last_name, e.first_name, d.dept_name
from Employees e
inner join dept_emp as de
on e.emp_no = de.emp_no
 inner join Departments as d
on de.dept_no = d.dept_no

--5. List all employees whose first name is "Hercules" and last names begin with "B."
select * from Employees
where first_name = 'Hercules' and last_name like 'B%'

--6. List all employees in the Sales department, 
--including their employee number, last name, first name, and department name.
select e.emp_no, e.last_name, e.first_name, d.dept_name
from Employees e
inner join dept_emp as de
on e.emp_no = de.emp_no
 inner join Departments as d
on de.dept_no = d.dept_no
--where d.dept_name = 'Sales'
where d.dept_name like 'Sales'

--7. List all employees in the Sales and Development departments, 
--including their employee number, last name, first name, and department name.
select e.emp_no, e.last_name, e.first_name, d.dept_name
from Employees e
inner join dept_emp as de
on e.emp_no = de.emp_no
 inner join Departments as d
on de.dept_no = d.dept_no
where d.dept_name = 'Sales' or d.dept_name = 'Developement'
--where d.dept_name like 'Sales' or d.dept_name like 'Developement';

--8. In descending order, list the frequency count of employee last names, 
--i.e., how many employees share each last name.
select last_name, Count(last_name) Frequency
from Employees
Group by last_name
order by Frequency desc;





