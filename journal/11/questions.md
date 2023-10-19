# A bit more CSharp and SQL
1. What does ***inheritance*** accomplish for us in C#?

  > Inheritance enables you to create new classes that reuse, extend, and modify the behavior defined in other classes. The class whose members are inherited is called the base class, and the class that inherits those members is called the derived class. A derived class can have only one direct base class.

2. How does ***member inheritance*** work in C#? Does a `Class` inherit all members of the base `Class`?

  > Yes, the class does inherit all members of the base class. 

3. How does ***accessibility*** affect inheritance?

  > A member's accessibility affects its visibility for derived classes as follows:

Private members are visible only in derived classes that are nested in their base class. Otherwise, they are not visible in derived classes.

4. What is the difference between a `PRIMARY KEY` and a `FOREIGN KEY`

  > A primary key is a column or set of columns that uniquely identify a row in a table. A foreign key is a column or set of columns in a second table that links data in one table to the data in another table

5. What is an ***alias***?

  > In SQL, an alias is a temporary name given to a table, column, or expression in a query. Aliases are used to: 
Make the output more readable and intuitive
Make it easier to display the results or to write your query
Make your queries shorter and more understandable

6. Demonstrate how you would query a join statement that would get all of a doctors patients from the following collections:

  ```SQL
  CREATE TABLE doctors (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patients (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patient_doctors (
    id INT NOT NULL AUTO_INCREMENT,
    doctorId INT NOT NULL,
    patientId INT NOT NULL,

    FOREIGN KEY (doctorId)
      REFERENCES doctors(id),
    FOREIGN KEY (patientId)
      REFERENCES patients(id),
  )

  ```

  > | ANSWER HERE |
