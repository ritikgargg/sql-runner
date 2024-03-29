**Submitter name:** Ritik Garg

**Roll No.:** 2019CSB1112

**Course:** CS305-Software Engineering

Link to repository: https://github.com/ritikgarg2701/cs305_2022

Link to branch : https://github.com/ritikgarg2701/cs305_2022/tree/assignment_1

=================================


**1. What does this program do?**

   The objective of this assignment is to develop a Java-based library that can be used to execute SQL queries for creating, reading, updating, and deleting records(CRUD operations) in an RDBMS. Here, the RDBMS used is **MySQL**. **MySQL Sakila sample DB** is used for testing the library operations. 
   
The queries are extracted from an XML file(**queries.xml**), which follows a particular structure. They are identified by unique query ids present in the 'sql' nodes of the XML file. Flexibility to update the parameters of the SQL queries using supplied objects, primitives, or collections of primitives is also provided.



**2. A description of how this program works (i.e. its logic)**

   This program consists of an interface `SqlRunner` with five primary functions viz. `selectOne()`, `selectMany()`, `update()`, `insert()` and `delete()`. The interface is implemented by the class `SqlRunnerAPI`.

   Two primary tasks, common among the five functions are parsing the XML file to obtain the required query and running the query after refining the extracted query string.

   `xmlParser()` function is responsible for parsing the XML file to extract the value of the attribute `paramType` and query string using the `queryId`(unique) argument for the purpose.

   The `interpolateValuesInQuery()` function is responsible for calling different handler functions based on the matching case. These handler functions are primarily responsible for replacing the placeholders in the MySQL query string with appropriate values. The different cases covered in the implementation are 
   * (i) Objects containing data members to replace the placeholders with matching names, 
   * (ii) Primitives supplied directly to replace placeholders, and 
   * (iii) arrays/collections of primitives to substitute the placeholders. 

These cases are handled by different helper functions like `handleObjects()`, `handlePrimitives()`, `handleCollectionOfPrimitives()`, and `handleArrayList()`.

   The `selectExecutor()` function serves as a common helper method to execute the `selectOne()` and `selectMany()` functions. This function returns the list of POJOs, after populating them with the results of SELECT queries.
   
   The `insertDeleteUpdateExecutor()` function serves as a command helper method to execute the `update()`, `insert()`, and `delete()` functions. It returns the number of inserted, updated or deleted rows as a result of the query.
   
   In the implementation, exceptions are thrown back to the user of the library in order to identify and handle the cause of the exceptions.



**3. How to compile and run this program**

   * The root of the project contains a `gradlew` script (`gradlew.bat` for Windows).

   * To run `App.java`, execute

   `./gradlew run`

   `App.Java` can be used to run the functions of `SqlRunnerAPI.java`
   
   * To run the tests, make sure you have setup the **MySQL Sakila sample database**.
   * Change the configuration (`username`, `password`, etc) in `app/src/test/java/assignment_1/SqlRunnerAPITest.java`
   * Finally, execute the following command:

   `./gradlew test`




   



