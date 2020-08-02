# Network

**Compare version of HTTP**

- HTTP
- HTTP 1.1
- HTTP 2.0
- HTTPs

**Headers**

**OSI Model**

**TCP/IP Model**

**TCP**

**UDP**

**FTP**

**SSH**

**Long polling /short polling**

**Websocket**

**GET / POST / PUT / DELETE / OPTIONS**

**Session-cookie**

# Crypto

## Hash function

**Bcrypt**

**HMAC**

## Encrypt function

**MD5**

**RSA**

**AES**

# Security

**XSS**

**SQL Injection**

# ElasticSearch

**How it work**

**Cluser / node**

**Analyzer / tokenizer**

**Query / aggregation**

# Database

**B-tree**

**Hash**

**Spatial/dense index b-tree and hash**

**Transaction**

**Normalization / Denormalization**

## MySQL

# System

**Processes, Threads, Concurrency issues**

**Difference between processes and threads**

**Processes**

**Threads**

**Locks**

**mutexes**

**semaphores**

**monitors**

**deadlock**

**livelock**

**scheduling**

# Testing

**How unit testing works**

**What are mock objects**

**What is integration testing**

**What is dependency injection**

# DSA

## Data structures

**Array**

**Linked List**

**Queue**

- Priority Queue
- Min/Max heap

**Stack**

**Tree**

- Binary tree
- Binary search tree
- AVL tree
- Red-black tree
- B/B+ tree

**Trie**

**Graph**

**Hash table**

## Algorithms

### Sorting

- Selection sort
- Insertion sort
- Bubble sort
- Quick sort
- Merge sort
- Heap sort
- Radix sort
- Bucket sort

### Searching

- Linear search
- Binary search

### Hashing

### Compressing

# Design pattern

**Singleton**

**Dependcy injection**

**Inversion of control**

**Strategy**

**Adapter**

**Prototype**

**Decorator**

**Visitor**

**Factory, abstract factory**

**Builder**

**Facade**

**Observer**

**Proxy**

**Delegate**

**Command**

**state**

**Memento**

**Iterator**

**Composite**

**Flyweight**

# Java

**JDK / JVM / JRE**

**Garbage collection**

**Equals vs ==**

**Heap and Stack memory in Java**

## Servlet

## Spring

## Maven

# Linux

## Commands / Tools

# Front-end

## React

**Life cycle hook**

**Virtual DOM**

**Compare to other view framework**

**Compare to serverside rendering**

## Javascript

**Async / await / promise**

**Event loop**

**Scope**

# Microservices

**Docker**

**Thrift**

- Thrift generate the client and server code completely, including the datastuctures you are passing, so you don't have to deal with anything other than writing the handlers and invoking client. And things like parameters, returns are automatically validated and parsed
- Thrift is more compact than HTTP
- Thrift has a binary serialization and deserialization which is much faster than text serialization and deserialization of REST
- Using Thrift to comunication between services in the microservice architecture

**REST API**

- is an API protocol
- Representational State Transfer
- Is much simpler to debug than Thrift protocols
- Using REST API to comunication between client side like web browser, mobile application, or 3rd parties support

# Others

**Caching**

**Nginx**

**Websocket**

**Request dispatcher**

# Principle

**OOP**

**S.O.L.I.D**

- **Single responsibility:** every module or class should have a single responsibilty. 
  - This principle makes the code more organized, it improves the readability of the code, it also make the code more flexible and more reuseable

- **Open / closed:** Software entities should be open for extension and closed for modification. 
  - The code should be able to add new features without breaking existing code.

- **Liskov substitution:** mean that every child class should substituable for their parent class without alerting the correctness of the program. In other words, the objects of your subclass should behave in the same way as the objects of your superclass.

- **Interface segregation:** states that a client should never forced to depend on methods it does not use. 
  - Achieving it by **making your interfaces small and focused**.
  - Split large interfaces into more specific ones that are focused on a specific set of functionalities so that the clients can choose to depend only on the functionalities they need.

- **Dependency inversion:** tries to avoid tight coupling between software modules. It states that high-level modules should not depend on low-level modules, but only their abstraction. In simple words,  It suggests that you should use interfaces instead of concrete implementations wherever possible.
  - This decouples a module from the implementation details of its dependencies. The module only knows about the behavior on which it depends, not how that behavior is implemented. This allows you to change the implementation whenever you want without affecting the module itself.
  - One should depend upon abstraction, not concretions.

**KISS**

- Keep It Simple, Stupid
- Software system work best when they kept simple.
- Avoiding unnessary complexity
- The more simple, the less bug software system has
- Easy to understand so that easy to maintain and debug
- Complexity generate bugs

**DRY**

- Don't Repeat Your Self
- An efficient code can be highly reusable
- Avoid repeating piece of code because you will have to keep them sync, and any changes to the code at once place will require changes at other place as well.
- Repeating code make it cost more resources and hard to maintain, extend and more buggy

**YAGNI**

- You Ain't gonna Need It
- Like KISS principle, YAGNI also aims at avoiding complexity.
- Avoid implement too complex and abstract methods at the begining just because you think it'll be need on the future
- Avoid implement methods that you don't need it right now but you think it will be needed in the future.
- It cost resources and you may even never use them in the future
- The more abstract method, the hard to read, maintain and debug them.

**Clean code**

We could certainly say that the code follows some of the criteria of what makes code easy to understand

- easy to understand the execution flow of the entire application
- easy to understand how the different objects collaborate with each other
- easy to understand the role and responsibility of each class
- easy to understand what each method does
- easy to understand what is the purpose of each expression and variable

The code is easy to extend and refactor, and it’s easy to fix bugs in the codebase. This can be achieved if the person making the changes understands the code and also feels confident that the changes introduced in the code do not break any existing functionality.

One could argue that for the code to be easy to change:

- Classes and methods are small and only have single responsibility
- Classes have clear and concise public APIs
- Classes and methods are predictable and work as expected
- The code is easily testable and has unit tests (or it is easy to write the tests)
- Tests are easy to understand and easy to change

Clean code includes:

- **Pronounceable variable and function names** - so instead of temp write out the word temporary or temperature. Insted qtyOH write it out to quantityOnHand.

- **Using constants instead of literals (magic numbers or magic strings)** - constants can help you find their use in the code. If for example you use the number 18 for MINIMUM_AGE, 18 can mean different things in the code vs. MINIMUM_AGE only means that one thing.

- **Descriptive variable and function names** - The less mental mapping that a programmer has to do when reading your code the faster he can fix that bug. Remember that code will be read a lot more after it is created than when it is initially written.

- **Short functions** - short functions help us understand the purpose of the function and also make it less prone to side effects and bugs. They are also easier to read.

- **Functions and classes that do one thing and do it well.** This goes along with the Single Responsibility principle of SOLID. Again there should only one reason for it to change. Less side effects means less bugs and easier maintenance, also better testability.

- **Separating concerns** - When people think of separating concerns they usually speak of the common main concerns, Presentation, Logic and Data Access. However, there are many other different types of responsiblities. For example a reporting system, may require separating all of these concerns to remain more maintainable and extensible.

- **Functions should be verbs** - This goes without saying but this makes the code read more like a story.

- **Variables should be nouns**