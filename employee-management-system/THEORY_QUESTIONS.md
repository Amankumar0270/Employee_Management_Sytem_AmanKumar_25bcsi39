
#  Spring Boot Employee Management System - Debugging Assignment
Please DO NOT COPY FROM EXTERNAL SOURCES FOR YOUR OWN BETTER IF YOU WANT TO BE BETTER IN INTERVIEWS, I HAVE GIVEN THE HINTS AND INSTRUCTIONS, ANY DOUBTS OR HASSLES  PLS ,YOU ARE WELCOME TO REACH ME ON MY WHATSAPP, WILL BE HAPPY TO GUIDE YOU BETTER
---

#  Objective

Fix the broken Spring Boot project and make all APIs work correctly.

You are NOT allowed to rewrite everything.
You must debug and fix existing code.

---

#  SECTION 1: BUG FIX TASKS

##  1. Employee.java Issues

###  Problems in code:
- Entity is not properly mapped
- Missing annotations
- Getters and setters are incorrect
- Missing default constructor

###  Your Task:
Write answers for:

1. Which annotation is missing to make this a database table?
   Answer--> The missing annotation is '@Entity', for @Entity tells JPA/Hibernate that the class should be mapped to a database table.

   
2. Why do we need a default constructor in JPA?
   Answer--> JPA uses reflection to create objects when reading data from the database.Without a default constructor, Hibernate cannot create an object of the entity class and may throw an exception such as: "No default constructor for entity" Therefore, every JPA entity should have a no-argument constructor.
   
3. Fix all getter and setter methods
   Answer->>  All the getter methods will use a return type required of specific parameters with no needed parameter inside the parenthesis, whereas in setter methods the return type will be void whereas the parenthesis will have paramters inside of it for example as such: public Long getId() { return id; } public void setId(Long id) { this.id = id; }
    
4. What happens if @Id is missing?
Answer->>  JPA cannot identify the primary key of the entity. At application startup, Hibernate will throw an error similar to: Entity 'Employee' has no identifier OR No identifier specified for entity Because every JPA entity must have exactly one primary key field marked with @Id.

---

##  2. Repository Issues

### Problems:
- Repository is not extending JpaRepository

###  Your Task:

1. Why do we extend JpaRepository?
   Answer->> We extend JpaRepository because it provides ready-made CRUD operations without writing SQL queries or implementation code. By extending JpaRepository, we automatically get methods like: save,findAll,findById,etc.


2. What happens if we don't extend it?
 Answer->> If we don't extend it, then there will be no CRUD methods available to use, and we cannot call repository implementation such as, repo.save, repo.findAll, repo.findById, etc. because spring data JPA will not create a repository implementation automatically. Compilation errors such as: "The method save(Employee) is undefined" may show up.

3. Fix repository so CRUD works

Answer->> We extend EmployeeRepository to JpaRepository<Employee, Long>, where: -Employee → Entity class -Long → Data type of primary key (id) And even import, org.springframework.data.jpa.repository.JpaRepository & com.example.demo.entity.Employee.

##  3. Controller Issues

### Problems:
- Missing annotations (@RestController, @RequestMapping)
- Missing @RequestBody and @PathVariable
- Methods returning null
- Repository not injected properly

###  Your Task:

1. What does @RestController do?
   Answer-->>@RestController is used to create REST APIs in Spring Boot.
It combines @Controller and @ResponseBody.
It returns data directly as JSON or XML format.

2. Difference between @RequestBody and @PathVariable?
Answer:

@RequestBody                                 	@PathVariable
Reads data from the request body.      	        Reads data from the URL path.
Converts JSON into a Java object.	            Converts URL value into a method parameter.
Mostly used with POST and PUT requests.	     Mostly used with GET, PUT, and DELETE requests.

3. Fix all APIs (POST, GET, PUT, DELETE)

4. Explain flow: Postman → Controller → Repository → DB

   Answer->>>Answer:

Postman sends the HTTP request.
Controller receives the request.
Controller calls the Repository (or Service layer).
Repository interacts with the Database.
Database processes the request and returns data.
Repository receives the data.
Controller sends the response back to Postman.

##  4. application.properties Issues

### Problems:
- Incorrect datasource configuration
- Missing H2 settings
- App not starting

###  Your Task:

1. Why do we need application.properties?
   Answer:

application.properties is used to store application configuration settings.
It helps manage database configuration, server port, logging, and Spring Boot settings.
It avoids hardcoding configuration values in the application.
---

2. What is H2 database used for?
   Answer->>

H2 is an in-memory database.
It is mainly used for development, testing, and learning purposes.
It does not require separate installation.
Data is lost when the application stops.

3. Fix configuration so application runs
   Answer->>
server.port=9191

spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
---

#  SECTION 2: POSTMAN TESTING

Write answers after testing:

1. What is response of POST /employee/save?
   Answer:->>>>> A new employee record is saved in the database.
The saved employee details are returned in the response.

2. What happens if GET /employee/1 is called with invalid ID?
   Answer->>   Employee data is not found.
The API returns an error message or null response depending on the implementation.


4. What is returned in DELETE API?
   Answer->>>A success message indicating that the employee record has been deleted


   
5. Which method is used for update?
   Answer->>>PUT method is used for updating existing records.

---

#  SECTION 3: THEORY QUESTIONS

Answer briefly:

1. What is REST API?

   Answer->>>   REST API is an architectural style used for communication between client and server using HTTP methods.
It allows applications to exchange data over the internet.

   
2. What is CRUD?
  Answer->>>>

CRUD stands for:
Create
Read
Update
Delete
These are the basic operations performed on data.


3. Difference between POST and PUT?
   Answer->>>>>
   POST                                 	PUT
Used to create a new resource.          	Used to update an existing resource.
Creates new data.	                        Modifies existing data.
Not idempotent.	                           Idempotent.
   
5. What is dependency injection?

   Answer->>>>Dependency Injection is a design pattern where Spring automatically provides the required objects to a class.
It helps reduce tight coupling between classes.
   
6. Why do we use Spring Boot?
   Answer->>>   Spring Boot simplifies Spring application development.
It provides auto-configuration.
It reduces boilerplate code.
It contains embedded servers like Tomcat.
It helps build REST APIs quickly and efficiently.

---

#  SUBMISSION RULES

- Fix all bugs in code
- Run project successfully
- Test all APIs in Postman
- Push corrected code to GitHub
- Fill this THEORY_QUESTIONS.md file
