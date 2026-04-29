Step 1 : create security group
 [Uploading pic…]()


Step 2 : Launch EC2 instance (Ubuntu) and connect it
 

Step 3 : create mysql database (aws rds)
 
 

 

Step 4 : Connect to instance and Install MySQL Client on EC2
sudo apt update
sudo apt install mysql-client -y
________________________________________
Step 5 : Login to RDS
mysql -h <rds-endpoint> -u admin -p
mysql -h database-1.cpewieq0eux7.us-west-1.rds.amazonaws.com -u admin -prds-database123

 
________________________________________
Step 6 : Create Database
CREATE DATABASE student_db;
USE student_db;
________________________________________
Create Students Table
CREATE TABLE students (
id bigint NOT NULL AUTO_INCREMENT,
name varchar(255),
email varchar(255),
course varchar(255),
student_class varchar(255),
percentage double,
branch varchar(255),
mobile_number varchar(255),
PRIMARY KEY (id)
);
 
Exit MySQL
exit

Step 7 : Setup Backend (Spring Boot)
Clone Repository
git clone https://github.com/abhipraydhoble/project-studentapp-aws.git
________________________________________
Install Java 17
sudo apt install openjdk-17-jdk -y
Verify:
java -version
________________________________________
Install Maven
sudo apt install maven -y
Verify:
mvn -version
________________________________________
Navigate to Backend Directory
cd studentapp_updated/backend
________________________________________
Configure Database Connection
Edit file:
vim src/main/resources/application.properties
 

Also Edit pom.xml(backend)  add dependency for mysql
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <scope>runtime</scope>
</dependency>

 



Step 8 : Build Backend Application
mvn clean package -DskipTests
 


Step 9 : Setup Frontend (React)
Navigate to Frontend Directory
cd ../Frontend
________________________________________
Install Node.js and npm
sudo apt install nodejs npm -y
________________________________________
Configure Backend API URL
Edit file:
vim src/api/userService.js
 

Install Frontend Dependencies
npm install
________________________________________
Run Frontend Application
npm start
________________________________________
Build Frontend Application
npm run build
 

Step 10 : Host Frontend Using Apache
Install Apache
sudo apt install apache2 -y
________________________________________
Copy Build Files
sudo cp -r dist/* /var/www/html/
________________________________________
Start Apache
sudo systemctl start apache2
 

Step 11 : Run Backend Application
•	go to backend dir
cd ../Backend/target/
java -jar student-app.jar
 

Step 12 : Access Website
http://EC2-IP
 
 

 

