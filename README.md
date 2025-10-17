# Spring MVC Electricity Bill Calculator 💡
A sample web application built with Spring MVC and JSP that calculates a customer's electricity bill. This project demonstrates a classic Spring MVC setup using JdbcTemplate for database connectivity and JUnit for testing.
The application retrieves customer data, including their consumed units, from a MySQL database and calculates the total charges based on a tiered slab rate.

## Features
Search for customers by Name or Service Number.

Retrieve consumed electricity units from a MySQL database.

Calculate electricity charges based on a progressive slab system.

Display the customer details and the calculated bill amount.

## Technology Stack 🔧
Backend: Java 1.8, Spring MVC 5.1.1

Database: MySQL 8, Spring JdbcTemplate

Frontend: JSP, JSTL

Build Tool: Apache Maven

Testing: JUnit 4, Mockito, Spring Test

Server: Apache Tomcat 9 (or any Servlet 3.0+ container)

## Prerequisites
Before you begin, ensure you have the following installed:

JDK 1.8 or later

Apache Maven

MySQL Server

An IDE like Eclipse or IntelliJ IDEA

Apache Tomcat 9 or a compatible web server 

## Installation & Setup 🚀
Follow these steps to get the project up and running on your local machine.

### 1. Clone the Repository

git clone https://github.com/your-username/SpringMVCElectricityBillCalculation.git
cd SpringMVCElectricityBillCalculation

### 2. Database Setup
You need to set up the database and the table with the sample data.

Open your MySQL client (like MySQL Workbench).

Run the following SQL script to create the database, table, and insert the required data.

DROP DATABASE IF EXISTS test;
CREATE DATABASE test;
USE test;

CREATE TABLE personsdetails (
  id int(6) unsigned NOT NULL,
  Name varchar(50) NOT NULL,
  serviceNumber varchar(10) NOT NULL,
  consumedUnits int(11) NOT NULL,
  gender varchar(10) DEFAULT NULL,
  PRIMARY KEY (id)
) ENGINE=InnoDB;

INSERT INTO personsdetails (id, Name, serviceNumber, consumedUnits, gender) VALUES
(1, 'personA', '123-456', 250, 'Female'),
(2, 'personB', '246-468', 350, 'male'),
(3, 'personC', '123-678', 150, 'Female'),
(4, 'personD', '246-789', 220, 'male'),
(5, 'personE', '146-189', 500, 'female');

### 3. Configure Database Connection
Open the project in your IDE.

Navigate to the Spring configuration file located at: src/main/webapp/WEB-INF/spring-servlet.xml

Find the dataSource bean and update the username and password properties with your MySQL credentials.

<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
    <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
    <property name="url" value="jdbc:mysql://localhost:3306/test" />
    <property name="username" value="your_mysql_username" /> <property name="password" value="your_mysql_password" /> </bean>

### 4. Build and Run the Application
You can run this project either by deploying it to an external Tomcat server or by running it directly from your IDE.

Using an IDE (Eclipse/IntelliJ):

Configure your Tomcat server in the IDE.

Right-click the project and select Run As -> Run on Server.

Choose your configured Tomcat server.

Using Maven:

Build the project to generate a .war file:
mvn clean install

This will create a SpringMVCElectricityBillCalculation.war file in your target/ directory.

Deploy this .war file to your Tomcat server's webapps directory.

## Usage
Once the application is running, open your web browser and navigate to: http://localhost:8080/SpringMVCElectricityBillCalculation/

You will see a form where you can enter either a Person Name (e.g., "personA") or a Service Number (e.g., "123-456").

Click the "Calculate Electricity charge" button to view the bill details.

## Author
Aman Manwatkar
