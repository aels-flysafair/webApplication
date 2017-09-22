# Web Application Basics

This project is intended as a guideline to the basic setup of a web application, based off of the _CourseWare_ workshop presented by Trevor Page. 

## Prerequisites

To be able to setup a basic web application, the following is required:
   1. [_MySQL community server_](https://dev.mysql.com/downloads/mysql) setup on local device.
   2. MySQL interface, I am using [_Toad_](https://www.toadworld.com/m/freeware/1656).
   3. Spring IDE, I am using [_Spring Tool Suite_](https://spring.io/tools/sts/all).

Once both of these are setup and running on your local device, you can continue with the project described here.

## Setup for Project

To start creating the web application: 
   1. Start by creating a new _Spring Starter Project_, available under _File -> New -> Spring Starter Project_.
   2. Suggested project setup:

   Property   | Description
   :---------:|---------------------
   Service URL| The URL that STS calls to generate the project, set to http://start.spring.io
   Name       | Name of the project, example here "CourseWare"
   Location   | File location on local device
   Type       | Maven
   Packaging  | JAR
   Java Version| Latest, it is version 1.8 at the time of making this document
   Language   | The programming language used, set to "Java"
   Group      | Package name for project origin, set to "com.ProjectName"
   Artifact   | Demo (Leave as is)
   Version    | 0.0.1-SNAPSHOT (Leave as is)
   Description| Description of the project
   Package    | Package name for project origin, set to "com.ProjectName"

   3. After clicking next, select the version of _Spring Boot_ preferably the latest version. Current version is 1.5.7
   4. Select the source packages to include in the project. Basics required in project for setup are
      + JPA
      + MySQL
      + ThymeLeaf
      + Web
   5. Click finish, and this will generate the project.
   Having completed this STS will create all the required project files, packages, and folders automatically. This project will contain a main application `.java` file named _projectNameApplication.java_ which defines the main public class for the application to run.

   6. Continuing with the setup of the project, a new database for the project has to be created on the local MySQL server. This can be done using the MySQL interface, along with creating the relevant user for the database to allow us to access it from our application.

   7. Now back in STS open the _application.properties_ file located in the _src/main/resource_ folder. Here we will set some key parameters for the application allowing it to access our database. The standard location for the MySQL local server to be located is _localhost:3306_.
   ```
     spring.datasource.url = jdbc:mysql://localhost:3306/databaseName
     spring.datasource.driver-class-name = com.mysql.jdbc.Driver
     spring.datasource.username = userName
     spring.datasource.password = Password
   
     spring.jpa.database-platform = org.hibernate.dialect.MySQLDialect
     spring.jpa.show-sql = true
     spring.jpa.hibernate.ddl-auto = update
   ```

   8. Next, in the _src/main/resource_ folder you will find the template folder. Create a new HTML document in the folder, generally opting for standard first page _index.html_. This HTML page will be linked to the application and act as it's main interface. 

   9. The final part of setting up the web application is linking the template and database, and this is done using a controller. So in the _src/main/java_ folder create a new package, name it _com.projectname.web_ and add a new class to it which is called _indexController.java_
   ```
     package com.coderscampus.web;

     import org.springframework.stereotype.Controller;
     import org.springframework.web.bind.annotation.RequestMapping;

     //Defines this class as controller
     @Controller
     public class indexController 
     {
     	//Maps any request received to specific action
     	@RequestMapping("")
     	public String index ()
     	{
     		return "index";
     	}
     }
   ```

 Run the application as a _Spring Boot App_ and connecting to _localhost:8080_ in your web browser, the web application should successfully load.
