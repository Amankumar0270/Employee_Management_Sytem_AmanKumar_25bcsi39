
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
ANS → @Entity tells JPA that this class represents a database table.
2. Why do we need a default constructor in JPA?
ANS → Without a no-argument constructor, JPA cannot instantiate the entity.
3. Fix all getter and setter methods
ANS →
→ Getters should return the corresponding field value.
→ Setters should assign the parameter value to the field using this.<that name>
5. What happens if @Id is missing?
ANS → JPA will not know which field is the primary key.
---

##  2. Repository Issues

### Problems:
- Repository is not extending JpaRepository

###  Your Task:

1. Why do we extend JpaRepository?
ANS : to save , find all , findby id and also deleteby id
2. What happens if we don't extend it?
ANS : Repository will not get built-in database methods.
3. Fix repository so CRUD works
ANS :
We would have to write database code manually.
---

##  3. Controller Issues

### Problems:
- Missing annotations (@RestController, @RequestMapping)
- Missing @RequestBody and @PathVariable
- Methods returning null
- Repository not injected properly

###  Your Task:

1. What does @RestController do?
ANS : Handles HTTP requests
2. Difference between @RequestBody and @PathVariable?
ANS :Used to receive data from the request body & Used to receive values from the URL respectivily
3. Fix all APIs (POST, GET, PUT, DELETE)

ANS :
POST :
@PostMapping
public Employee addEmployee(@RequestBody Employee employee)

GET :
@GetMapping
public List<Employee> getAllEmployees()

PUT:
@PutMapping("/{id}")
public Employee updateEmployee(@PathVariable Long id,@RequestBody Employee employee)

DELETE : 
@DeleteMapping("/{id}")
public String deleteEmployee(@PathVariable Long id)

4. Explain flow: Postman → Controller → Repository → DB
Postman
   |
Controller
   |
Repository
   |↓
Database
   |↑
Repository
   |
Controller
   |
Postman
---

##  4. application.properties Issues

### Problems:
- Incorrect datasource configuration
- Missing H2 settings
- App not starting

###  Your Task:

1. Why do we need application.properties?
ANS :
Database configuration
Server port configuration
2. What is H2 database used for?
ANS:
Lightweight
Fast
No separate installation required
3. Fix configuration so application runs

---

#  SECTION 2: POSTMAN TESTING

Write answers after testing:

1. What is response of POST /employee/save?
ANS {
  "id": 1,
  "name": "Prateek",
  "department": "CSE",
  "salary": 50000
}
2. What happens if GET /employee/1 is called with invalid ID?
ANS : 
3. What is returned in DELETE API?
Employee Deleted Successfully
4. Which method is used for update?

---

#  SECTION 3: THEORY QUESTIONS

Answer briefly:

1. What is REST API? 
ANS : REST API is a way for two applications to talk to each other using the internet . Like a bridge
2. What is CRUD?
ANS : create ,read ,update ,delete
3. Difference between POST and PUT?
ANS : used to add a new data & update the exiting data respectivily
4. What is dependency injection?
ANs : it means if we have a function for a perticular work we can use the function for multiple purpose
5. Why do we use Spring Boot?
Ans : because it helps in  not building extra objects which saves time . alsp project setup
---

#  SUBMISSION RULES

- Fix all bugs in code
- Run project successfully
- Test all APIs in Postman
- Push corrected code to GitHub
- Fill this THEORY_QUESTIONS.md file
