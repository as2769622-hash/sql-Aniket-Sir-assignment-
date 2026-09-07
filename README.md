CREATE DATABASE University;
USE University;

-- University table
CREATE TABLE Students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    grade VARCHAR(10)
);

INSERT INTO students (name, age, grade)
VALUES
("john", 20, "A"),
("Satyam",18,"A+"),
("Shivam",20,"B");

INSERT INTO students(name,age)
VALUES
("RAJU",23);

Select * from students;
-- Select * from students where grade=null; ye galat hai
Select * from students where grade is null;

Select * from students where age<25 AND grade = "A";

Select * from students where (name="Satyam" or age!=18) AND (grade ="A");

Select * from students where age between 18 AND 22;

Select * from students where age  not between 18 AND 22;

-- single charac;- %A_
-- like is used to predict the charac after and above 
-- %A. , _%A , %A_

Select * from students 
WHERE name LIKE 'S%';

CREATE TABLE customer (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    company_name VARCHAR(100)
);
INSERT INTO customer (id, name, company_name)
VALUES
(1, 'Satyam', 'Google'),
(2, 'Rahul', 'Microsoft'),
(3, 'Priya', 'Amazon');


-- Create and switch to the database 
CREATE DATABASE IF NOT EXISTS company_db; 
USE company_db; 
 

-- Drop table if it already exists to start fresh 
DROP TABLE IF EXISTS class_employees; 
 

-- Create the demo employees table 
CREATE TABLE class_employees ( 
    emp_id INT AUTO_INCREMENT PRIMARY KEY, 
    first_name VARCHAR(50), 
    last_name VARCHAR(50), 
    salary DECIMAL(10,2), 
    hire_date DATE, 
    birth_date DATE 
); 
 

-- Insert demo records (containing leading/trailing spaces and mixed letter casing) 
INSERT INTO class_employees (first_name, last_name, salary, hire_date, birth_date) VALUES 
('  Alice ', 'Johnson', 75000.55, '2020-05-10', '1990-12-15'), 
('Bob', '  Smith ', 48000.00, '2021-03-15', '1985-06-22'), 
('charlie', 'brown', 62000.40, '2022-07-20', '1995-02-05'), 
('Diana', 'Lee', 95000.99, '2018-11-01', '1988-09-30'), 
(' Ethan', 'Miller  ', 54000.12, '2023-01-12', '1992-04-18'); 

Select * from class_employees;
use class_employees;
Select first_name,last_name,
concat(first_name,'',last_name)
As full_name
from class_employees;


 Select last_name,
 LCASE (last_name)
 as lower_part,
 UCASE (last_name)
 as upper_part
 from class_employees;
 
 SELECT first_name as raw_name,trim(first_name) as trim_data from class_employees;
 SELECT last_name as raw_name,trim(last_name) as trim_data from class_employees;
 
 
 SELECT first_name as raw_name,
 length(first_name) as raw_length,
 length(trim(first_name)) as trim_length
 from class_employees;
 
 Select first_name,
 substring(first_name,1,3) as f3
 from class_employees;
 
 Select first_name,
 substring(first_name,1,3)as f3,
  substring(first_name,-1,3)as l3
  from class_employees;
  
SELECT salary as raw_salary,
round(salary,1) as round_up_1,
round(salary,2) as round_up_2
from class_employees;

SELECT salary as raw_salary,
truncate(salary,1) as truncate_up_1,
truncate(salary,2) as truncate_up_2
from class_employees;

-- SELECT * FROM class_employees
-- WHERE MOD(emp_id , 2) = 0;

SELECT emp_id,first_name,
 MOD(emp_id , 2) as remainder,
 if(mod(emp_id,2)=0,'even','odd') as id_type
 from class_employees;

SELECT salary as raw_salary,
power(salary,1) as power_up_1,
power(salary,2) as power_up_2
from class_employees;

SELECT SQRT(emp_id) AS square_root
FROM class_employees;

select curdate() as today_date;
select now() as today_date_time;
select sysdate() as todays_sys_date,
now() as today_date_time;

SELECT DATE_FORMAT(hire_date, '%a, %d, %m') AS pretty_date 
FROM class_employees;
