# Intro to JavaScript
01. Which keywords are used to declare a variable in JavaScript?

    > The keywords that can be used to declare a variable in JavaScript are var, let and const.

02. What is the definition of a function?

    > |A function is a subprogram designed to perform a task.

03. What are the `SOLID` principles?

    >The SOLID principles are object-oriented design concepts relevant to software development. 
    
    SOLID is an acronym for:

    Single Responsibility Principle
    Open-Closed Principle
    Liskov Substitution Principle
    Interface Segregation Principle
    Dependency Inversion Principle


04. Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ['apple', 'banana', 'pineapple', 'orange', 'strawberry']
    ```

    > fruit.pop(2)

05. Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
        name: "You",
        hair: true,
        friends: []
    }
    let them = {
        name: "Them",
        hair: false,
        friends: []
    }
    ```

    > you.push(Them)
    them.push(You)

06. Give an example of a JavaScript `Conditional`:

    > Conditional statements control behavior in JavaScript and determine whether or not pieces of code can run. 
    
    An example of a conditional is the If Statement.

    if (2 > 1){
        console.log('True')
    }
    
    CONSOLE OUTPUT:

    True

07. What is the main difference between `parameters` and `arguments`?

    > The main difference between parameters and arguments is that parameters are the names created in the function and arguments are the values the functions receives. 

08. Instead of writing everything to the console, what is a better way to debug your code?

    > A better way to debug your code would be to use a web browser developer tool such as the Chrome Developer tools.

09. What is the difference between a `primitive` value and a `reference` value?

    > A primitive variable's information is stored as the value of that variable. There are 8 primitives defined in Java, they are: int, byte, short, long, float, double, boolean, and char.

    A reference variable holds a reference to information related to that variable. It points to an object of a given class, letting you access the value of an object. Reference variables do not store its own values.

10. Demonstrate a loop that prints the numbers between -100 and 100?

    > for (let i = -100; i <= 100; i++){
        return i
    }

