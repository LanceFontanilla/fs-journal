# CSharp and SQL Fundamentals
01. What is the purpose of a `namespace`?

  > Namespaces are used in C# to keep one set of names separated from another. This is done to organize the classes so that they are easy to handle. If there are two classes with the same names in different namespaces, they do not conflict with one another.

02. What is the difference between a `class` and an `interface`?

  > The basic difference is that a class has both a definition and an implementation whereas an interface only has a definition. Interfaces are actually implemented via a class. 

03. What is the method that returns an instance of a class, yet it has no return type?

  > The method that returns an instance of a class but has no return type is a constructor.

05. In the Car example what is the access modifier of the `Start()` method?

  ```c#
  abstract class Car
  {
    public string Start()
    {

      return "Vroooom";

    }
  }
  ```

  > The access modifier of Start() is "public"

06. In the Car example what is `string` an indication of?

  > The 'string' is an indication of the return type of "Vroooom" being a string.  

07. In the Car example what is `abstract` preventing?

  > Abstract is preventing the class from being instantiated.  

08. In a SQL table, what is the difference between information in a row and information in a column?

  > A row contains information like an object and columns are the specific properties.  Rows are known as a tuple and it represents a single record or data point.  Columns are also know as an attribute and represents a specific piece of information or characteristic that all rows in the table share.

09. Demonstrate the necessary SQL for creating a table called `characters` with the values `name, age, description` as strings, and an `int` id.

  >  CREATE TABLE characters (
    id int NOT NULL,
    name VARCHAR(255) NOT NULL,
    age VARCHAR(50) NOT NULL,
    description VARCHAR(255) NOT NULL,
);

10. In SQL how can you query more than a single table? Provide an example.

  > You can query more than a single table in SQL using SQL joins.  

    SELECT * FROM classroomStudents cs
    INNER JOIN students s ON s.id = cs.studentId
    INNER JOIN classrooms c ON c.id = cs.classroomId;

