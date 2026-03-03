--------------------------------------------------
my-secret-pw
docker stop some-mysql
docker rm some-mysql

netstat -a -n -o | findstr 3306
tasklist /fi "PID eq <PID>"
tasklist /fi "PID eq 3192"
net stop MySQL80

---------------------------------------------------------------------------------------------------
// mysql connect with the phpmyadmin to access with chrome browser

docker run --name some-phpmyadmin -d \
  --link some-mysql:db \
  -p 8080:80 \
  phpmyadmin/phpmyadmin
  
---------------------------------------------------------------------------------------------------

docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=@#123 -d mysql:8.0.45-debian
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=@#123 -p 3306:3306 -d mysql:8.0.45-debian
docker network create some-network
docker network connect some-network some-mysql
docker run -it --network some-network --rm mysql:8.0.45-debian mysql -h some-mysql -u root -p

---------------------------------------------------------------------------------------------------

Container name: some-mysql
Root password: my-secret-pw
Port mapping: Host 3306 → Container 3306
Image: mysql:8.0.45-debian

---------------------------------------------------------------------------------------------------

CREATE USER 'demo-user'@'%' IDENTIFIED BY 'demo';
GRANT ALL PRIVILEGES ON *.* TO 'demo-user'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;

docker run -it --network some-network --rm mysql:8.0.45-debian mysql -h some-mysql -u demo-user -p

---------------------------------------------------------------------------------------------------

docker run -it --network some-network --rm mysql mysql -hsome-mysql -uexample-user -p

SHOW DATABASES;
create database demo;
use demo;
SHOW DATABASES;
desc students;
SELECT * FROM users;


CREATE TABLE students (
    roll_number INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    phone_number VARCHAR(15),
    email VARCHAR(100),
    department VARCHAR(50),
    section VARCHAR(5),
    hod VARCHAR(50),
    admission_date DATE,
    address VARCHAR(200)
);


INSERT INTO students (first_name, last_name, phone_number, email, department, section, hod, admission_date, address) VALUES
('Shadab', 'sheakh', '555-1234', 'Shadab@example.com', 'Computer Science', 'A', 'Dr. Brown', '2023-08-15', '123 Maple St'),
('Alam', 'ji', '555-5678', 'alam@example.com', 'Mechanical', 'B', 'Dr. Green', '2022-07-10', '456 Oak St'),
('Shahnwaz', 'aalam', '555-9012', 'shahnwaz@example.com', 'Electrical', 'A', 'Dr. White', '2021-06-20', '789 Pine St'),
('Asif', 'sheakh', '555-3456', 'asiif@example.com', 'Civil', 'C', 'Dr. Black', '2023-01-05', '101 Elm St'),
('samir', 'aalam', '555-7890', 'samir@example.com', 'Computer Science', 'B', 'Dr. Brown', '2022-09-12', '202 Birch St');

SELECT * FROM users;

INSERT INTO students (first_name, last_name, phone_number, email, department, section, hod, admission_date, address) VALUES
('Rahul', 'kumar', '555-1234', 'rahul@example.com', 'civil', 'A', 'Dr. Brown', '2023-08-15', '123 Maple St');

