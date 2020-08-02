# ELCA

I participated in this internship in the second summer of college, which lasted 3 months.

During this internship, I learned about fundamental knowledges, Java, Spring Framework, Angular, and had to do an exercise to create a tool to manage the progress of projects with the knowledge I learned and then gave presentations to the trainer.

I was the youngest in that internship

# ZaloPay

This is a fresher program organized by VNG company

I work 3 months part-time and 6 months almost full-time

During that time, I learned about Golang, Linux, Nginx, basic knowledge about Microservices and Docker

I was assigned to develop ZaloPay integrated documentation page for 3rd parties, and also provide technical support to 3rd parties if required.

In the project, I have to modify the user interface according to the design and ensure the user interface will be responsive on different screen sizes. 

In addition, I have to write sample code for integration methods in different programming languages and create some demo applications using HTML / CSS / JS and Golang.

You can access that document at docs.zalopay.vn

The document page was developed based on a static site generator called Slate

# Zalo

I worked in Zalo for a year

Overall, I work on two main projects.

The first is a human resource management project called ZAHub

The second is the project called ZOAdmin. In this project I work in 3 modules including:

- A SSO server
- A tool to manage SSH access, upload / download files, and view logs on Zalo's servers
- A tool to manage activities that Zalo programmers perform on servers and on internal tools

## SSO Server

- This is the generic login method for all modules of the team
- Each module is a tool, such as the rights management tool that I work with is also a module
- Based on Zalo Login API
- When the user accesses a module, they will be redirected to the SSO server to log in. This time the SSO server will proceed with the login flow using the Zalo Login API. After successfully logging in through the Zalo Login API, the SSO server will create a session and redirect the callback url that the module previously registered with 2 JWT tokens, the first is an accesstoken containing the user's id and is used to query information of the user, the second is a refreshtoken used to create new accesstoken
- Technical Stack: Java, JWT

## Permission management

This project consists of three parts:
- a data storage server written in Java and using in-house Zalo's NoSQL and Elasticsearch to store data
- an API server written in Zalo's framework which is based on Java Servlet and communicates with data storage server through Apache Thrift
- a user interface written in React

Others:
- I work on both front-end and back-end
- Before this tool, all rights management operations such as adding, editing, and deleting were done manually, because of that, it was difficult to manage how many rights a user had.
- In this project I receive and store information about SSH access from agents installed on the server. This information is stored in Zalo's NoSQL and ElasticSearch in-house.

- Technical Stack: Java, React, Thrift, Message Queue (in-house)

## Activity management

This project consists of 3 parts
- a data storage server: receives and stores activity information from in-house Zalo's message queue called event bus.
- an API server written in Zalo's framework which is based on Java Servlet and communicates with data storage server through Apache Thrift
- a user interface written in React

This is a copy of Kibana's Discover feature which includes features such as:
- Filter data by conditions
- Query and highlight data according to ElasticSearch's query string syntax
- Draw a chart showing the number of activities according to the timeline

Others:
- This is actually a clone of Kibana's Discover feature
- I also work on both back-end and front-end
- The number of activities per day ranges from five hundred thousand to one million

- Technical Stack: Java, React, Thrift, Message Queue (in-house)

# Problems / Solutions

**Problems:** Save the storage space on ElasticSearch of Activity Management Tool.

**Solutions:**
- Research and apply Hot-warm-cold architect on a cluster of 5 nodes including: 1 master node, 2 data node on Hot server which have SSD disk and 2 data node on Warm server which have large HHD disk
- Hot-warm-cold architect consist of 3 phases: Hot, warm, and cold
- In hot phase, data is stored on 2 Hot servers that have SSD disks
- We switch to the Warm phase when the data capacity reaches the threshold of 50GB, this time the data will be transferred to storage on 2 Warm servers and the data is converted to read-only mode to reduce the capacity.
- In cold phase, data will be compressed when their lifetime is over 180 days

# Achivements