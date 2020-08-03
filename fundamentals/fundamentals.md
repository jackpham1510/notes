# Network

**HTTP**

Hyper text transfer protocol. At it’s most basic, it allows for the communication between different systems

Http versions:

- HTTP
  - Seperate connection
- HTTP 1.1
  - Persistent connections, Request queuing
  - Pipelining, Response queuing, head-of-line blocking
- HTTP 2.0
  - Multiplexing over single connection

**HTTPS**

HTTPS uses an encryption protocol to encrypt communications. 

The protocol is called Transport Layer Security (TLS), although formerly it was known as Secure Sockets Layer (SSL). 

This protocol secures communications by using what’s known as an asymmetric public key infrastructure. 

This type of security system uses two different keys to encrypt communications between two parties:

1. The private key - this key is controlled by the owner of a website and it’s kept, as the reader may have speculated, private. This key lives on a web server and is used to decrypt information encrypted by the public key.
2. The public key - this key is available to everyone who wants to interact with the server in a way that’s secure. Information that’s encrypted by the public key can only be decrypted by the private key.

**Headers**

**OSI Model**

- **Application layer:** Human-computer interaction layer, where applications can access the network services
  - End user layer
  - HTTP, FTP, SSH, DNS, IRC
  - Datas
- **Presentation layer:** Ensures that data is usable format and is where data encryption occurs
  - Syntax layer
  - SSL, SSH, IMAP, FTP, MPEG, JPEG
  - Datas
- **Session layer:** Maintains connections and is responsible for controlling ports and sessions
  - Sync & send to port
  - API's, Sockets, WinSock
  - Datas
- **Transport layer:** Transmits data using transmission protocols including TCP and UDP
  - End to end connections
  - TCP, UDP
  - Segments
- **Network layer:** Decides which physical path the data will take
  - IP, ICMP, IPSec, IGMP
  - Packets
- **Datalink layer:** Defines the format of data on the network
  - Ethernet, PPP, Switch, Bridge
  - MAC and LLC
  - Frames
- **Physical layer:** Transmits raw bit stream over the physical medium
  - Wireless, Hubs, Repeaters
  - Bits

**TCP/IP Model**

- **Application layer:** 
  - OSI Model: Application, Presentation and Session Layer
  - HTTP, FTTP, Telnet, NTP, DHCP, PING
- **Transport layer:**
  - OSI Model: Transport
  - TCP
  - UDP
- **Internet layer / Network layer:**
  - OSI Model: Network
  - IP, ARP, ICMP, IGMP
- **Network access layer:**
  - OSI Model: Data Link, Physical

**TCP**

- Transmission Control Protocol
- It is known to provide reliable and error-free communication between end systems. 
- It performs sequencing and segmentation of data. 
- It also has acknowledgment feature and controls the flow of the data through flow control mechanism. 
- It is a very effective protocol but has a lot of overhead due to such features. Increased overhead leads to increased cost.

**UDP**

- User Datagram Protocol
- On the other hand does not provide any such features. 
- It is the go-to protocol if your application does not require reliable transport as it is very cost-effective. 
- Unlike TCP, which is connection-oriented protocol, UDP is connectionless.

**FTP**

- File Transfer Protocol is a standard network protocol used for the transfer of computer files between a client and server on a computer network.

**SSH**

- Providing secure access for users and automated processes
- Interactive and automated file transfers
- Issuing remote commands
- Managing network infrastructure and other mission-critical system components.

**Polling / SSE / Websocket**

- **Short polling:** is an AJAX-based timer that calls at fixed delays
- **Long polling:** is based on Comet (i.e server will send data to the client when the server event happens with no delay)
  - Request with long or without timeout
  - Server hold request and repsonse when event happens
- **Websocket:** persistent connection between the client and server. This is a communications protocol providing full-duplex communication channels over a single TCP connection.
  - Frame-based not stream-based
  - Upgrade header
- **SSE:** is a mechanism that allows the server to asynchronously push the data to the client once the client-server connection is established. The server can then decide to send data whenever a new “chunk” of data is available. It can be considered as a one-way publish-subscribe model.
  - EventSource (HTML5)
  - The main benefits we get from this approach are:
    - Simpler implementation and Data efficiency
    - It is automatically multiplexed over HTTP/2 out of the box
    - Limits the number of connections for data on the client to one

**GET / POST**

GET | POST
----|-----
Values are visible in the URL | Values are not visible in the URL
GET has a limitation on the length of the values, generally 255 characters. | POST has no limitation on the length of the values since they are submitted via the body of HTTP.
GET performs are better compared to POST because of the simple nature of appending the values in the URL. | It has lower performance as compared to GET method because of time spent in including POST values in the HTTP body.
This method supports only string data types. | This method supports different data types, such as string, numeric, binary, etc.
GET results can be bookmarked. | 	POST results cannot be bookmarked.
GET request is often cacheable. | The POST request is hardly cacheable.
GET Parameters remain in web browser history. | Parameters are not saved in web browser history.

**Session-cookie**

- Session:
  - stored on server
  - usually is a map of data
- Cookie
  - stored on browser
  - http only (access only by server, javascript can't access http-only cookie)
  - secure (only send through https)
  - expired or persitent until close browser

**User agent**

- User agent is a string that contains application, operating system, platform, vendor and version informations of request

# Crypto

## Hash function

- Can't revert to plain data
- Only compare hash
- Some hash function:
  - MD5
  - Bcrypt
  - HMAC
    - SHA1
    - SHA2
    - SHA256
    - SHA512

## Encrypt function

- Synchronous: using one password
- Asynchronous: public key, private key
  - public key: share to every sender
  - private key: only the receiver
- Some encrypt function:
  - RSA: async
  - AES: sync

## Encode function

- No need key to encode
- Can revert to plain data by the same algorithm
- Some encode function:
  - Base64
  - URI

# Security

**XSS**

- Cross-site scripting
- The attacker aims to execute malicious scripts in a web browser of the victim by including malicious code in a legitimate web page or web application
- Prevent solution:
  - Don't trust user input
  - Avoid render plain HTML from user input data
  - Strip / Escaping HTML tag before render

**SQL Injection**

- The attacker aims to execute malicious SQL statements
- Attackers can use SQL Injection vulnerabilities to bypass application security measures.
- They can also use SQL Injection to add, modify, and delete records in the database.
- Prevent solution:
  - Don't trust user input
  - Using lastest SQL prepare statement library

# ElasticSearch

**How it work**

**Cluser / node**

**Analyzer / tokenizer**

**Query / aggregation**

# Database

**B-tree**

Method | Time complexity
-------|----------------
Search | O(logN)
Insert | O(logN)
Delete | O(logN)

Properties:

1. All leaves are at the same level.
2. A B-Tree is defined by the term minimum degree ‘t’. The value of 't' depends upon disk block size.
3. Every node except root must contain at least t-1 keys. The root may contain minimum 1 key.
4. All nodes (including root) may contain at most 2t – 1 keys.
5. Number of children of a node is equal to the number of keys in it plus 1.
6. All keys of a node are sorted in increasing order. The child between two keys k1 and k2 contains all keys in the range from k1 and k2.

![B-tree](./images/btree.png)

**Spatial/dense index b-tree and hash**

**Transaction**

- A transaction is a way of representing a state change. Transactions ideally have four properties, commonly known as **ACID:**
  - **Atomicity** (if the change is committed, it happens in one fell swoop; you can never see "half a change")
    - Change all or nothing change, there is no half a change
  - **Consistency** (the change can only happen if the new state of the system will be valid; any attempt to commit an invalid change will fail, leaving the system in its previous valid state)
  - **Isolation** (no-one else sees any part of the transaction until it's committed)
  - **Durability** (once the change has happened - if the system says the transaction has been committed, the client doesn't need to worry about "flushing" the system to make the change "stick")

**Transaction Isolation Level**

Phenomena:

1. **Dirty read:** Read the rollback data
2. **Non repeatable read:** Get different results with the same query
3. **Phantom read:** Get different result sets with the same query

Isolation levels:

1. **Serializable:** Implements read and writes locks until the transaction is finished. Also implements range locks.
2. **Repeatable Reads:** Implements read and write locks until the transaction is completed. Doesn’t manage range locks.
3. **Read Committed:** Implements write locks until the transaction is completed but releases read locks when a SELECT operation is performed.
4. **Read Uncommitted:** One transaction can see the uncommitted changes made by the other transaction

**Relationships**

- One to one
- One to many
- Many to many

**Normalization / Denormalization**

- **Normalization:** is the process of removing redundant data from the database by splitting the table in a well-defined manner in order to maintain data integrity. This process saves much of the storage space.
  - **First Normal Form (1NF):** A relation is said to be in 1NF only when all the entities of the table contain unique or atomic values.
  - **Second Normal Form (2NF):** A relation is said to be in 2NF only if it is in 1NF and all the non-key attribute of the table is fully dependent on the primary key.
  - **Third Normal Form (3NF):** A relation is said to be in 3NF only if it is in 2NF and every non-key attribute of the table is not transitively dependent on the primary key.

- **De-normalization:** is the process of adding up redundant data on the table in order to speed up the complex queries and thus achieve better performance.

**Why procedure execute faster than plain SQL**

- Stored procedures are precompiled and cached so the performance is much better.
- Query takes time to parse, validate, and compile

**How many SQL statements are used**

- **Data Definition Language (DDL)** commands are used to define the structure that holds the data. These commands are auto-committed.
  - CREATE, ALTER, TRUNCATE, DROP, RENAME
- **Data Manipulation Language (DML)** commands are used to manipulate the data of the database. These commands are not auto-committed and can be rolled back.
  - INSERT, UPDATE, DELETE, MERGE
- **Data Control Language (DCL)** commands are used to control the visibility of the data in the database like revoke access permission for using data in the database.
  - COMMIT, ROLLBACK

# System

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

### Compressing

- RLE: Run-length encoding
- Huffman encoding

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

**State**

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

**Request dispatcher**

# Principle

**OOP (Object Oriented Programming)**


Encapsulation
  - is a process of wrapping code and data together into a single unit.
  - control read, write permission -> make read-only, write-only classes
  - Data hiding
  - Control data by providing setter logic, restrict only valid data

Inheritance
  - is a mechanism in which one object acquires all the states and behaviors of a parent object.
  - Using Inheritance, In derived classes we can reuse the code of existing super classes.

Polymorphism
  - Polymorphism is the ability of an object to take on many forms.
  - Polymorphism in OOP occurs when a super class references a sub class object.
  - **Method overloading:** If a class has multiple methods that have same name but different parameters, this is known as method overloading.
  - **Method overriding:** If a subclass has the same method as declared in the super class, this is known as method overriding.

Abstraction
  - Abstraction is a process of hiding the implementation details and showing only functionality to the user.
  -  Abstract means a concept or an Idea which is not associated with any particular instance.
  -  Using abstract class/Interface we express the intent of the class rather than the actual implementation.
  -  In a way, one class should not know the inner details of another in order to use it, just knowing the interfaces should be good enough.

Interface
  - An interface is a blueprint of a class.
  - An interface is 100% abstract. No constructors are allowed here
  - By default, interface variables are public, static and final.
  - Interface have default, static methods
  - Multiple inheritance in Java

Abstract class
  - Abstract classes can’t be instantiated (can’t create objects of abstract classes). 
  - Have constructors, static methods, and final methods.
  - We can have an abstract class with no abstract methods.
  - The first concrete sub class of an abstract class must provide implementation to all abstract methods.
  - If this doesn't happen, then the sub class also should be marked as abstract.

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