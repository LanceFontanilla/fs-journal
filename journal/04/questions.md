# Understanding Asynchronous Code, and API's
01. What is the difference between `asynchronous` code and `synchronous` code?

  > Asynchronous code is executed in a non blocking manner as synchronous code is executed in a blocking manner.
>   Asynchronous code uses callbacks, promises, or async/await to handle the results of its tasks as to synchronus code uses a call stack.
> Synchronous must complete an individual task before another one is begun. Asynchronous tasks can run other tasks before one is completed.

02. What is an event listener?

  > An event listener is a way that you can wait for user interaction, like a click or keypress and then run some code once that action happens. It is a method that waits for an event to occur then responds to that event.

03. What does *REST* stand for, and in simple terms what does it mean??

  > REST stands for representational state transfer.  It is a type of software architecture designed to ensure interoperability between different internet computer sysstems. It imposes conditions on how and API should work.  It's more of a guideline to manage communication on a complex network, like the internet. 

04. What is a callback / higher order function?

  > A callback is a function that is passed as an argument to another function.  A higher order function is also a function but it takes at least one function as an input and/or returns a function as an output.

05. What is a `promise`? How do you capture an error from a `promise`?

  > A promise is a guarantee that when the time comes it will be resolved or it will get rejected.  There are 3 states of a promise: pending, resolved and rejected.  You can capture an error from a promise by using the Promise catch() method.  This method itself returns a promise so it can also be used to chain promises.  

06. Name three processes used to make requests over `HTTP`?

  > The most commonly used HTTP request methods are GET, POST, PUT, PATCH, and DELETE.

07. What does the `API` acronym stand for?

  > API stands for Application Programming Interface. It is a software intermediary that allows two applications to talk to each other.

08. What must you do in order to `await` a promise inside of a function?

  > You muct use the await keyword before a call to a function. 

09. What is the purpose of encapsulation in programming?

  > The purpose of encapsulation in programmin is that it is one of the key features of object-oriented programming. Encapsulation refers to the bundling of fields and methods inside a single class. It prevents outer classes from accessing and changing fields and methods of a class.

10. What is `HTTP` response code for a successful request?

  > The HTTP response code for a successful request is the 200 OK status code.  

11. What is a 400 error?

  > A 400 error is a HTTP Bad Resquest response status code that indicates the server cannot or will not process the request due to something that is perceived to be a client error.
