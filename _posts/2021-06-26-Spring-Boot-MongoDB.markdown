---
title: "Spring Boot and NoSQL Database MongoDB"
author: anantharajuc
categories: [ Spring Boot, MongoDB ]
tags: [ Spring Boot, MongoDB ]
layout: post
date: 2021-06-26 11:10
image: /assets/images/spring-boot-mongodb.jpg
---

This post briefly documents the usage of **MongoDB**, a general purpose, document-based, distributed database with Spring Boot. 

---

#### Minimum Software Requirements

- Java
- [MongoDB](https://docs.mongodb.com/manual/installation/) Community Edition Server
- [Postman](https://www.postman.com/downloads/)

##### MongoDB Installation

On Windows platform, create a folder titled **data** inside another folder named **db**, in **`C:`** drive. (*`C:\data\db`*)

For other platforms, check the installation guide by **MongoDB**.

Start the **mongod** server from the **`\bin`** folder of the MongoDB installation location (*`C:\Program Files\MongoDB\Server\4.0\bin`*). 

![MongoDB Start]({{ site.baseurl }}/assets/images/spring-boot/mongodb/start-mongod-server.PNG)  

#### Sample Project

[Spring Boot MongoDB](https://github.com/AnanthaRajuC/Spring-Boot-MongoDB) is the sample **CRUD** Spring Boot web application i've used to illustrate the usage of MongoDB.

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/spring-boot/mongodb/url.PNG" /></div>

##### ER Diagram

![MongoDB Start]({{ site.baseurl }}/assets/images/spring-boot/mongodb/database-er-diagram.PNG)  

##### Sample Valid JSON Request Body for PUT and POST requests.

```javascript
{
    "name": "John Doe",
    "email": "example@domain.com",
    "department": {
        "departmentName": "computer science",
        "location": "Dystopia"
    },
    "subjects": [
        {
            "subjectName": "Java",
            "marksObtained": 80
        },
        {
            "subjectName": "Chemistry",
            "marksObtained": 90
        }
    ],
    "demographics": {
        "country": "usa",
        "age": 50
    },
    "hobbies": [
        {
            "hobbyName": "music",
            "interestLevel": 4
        },
        {
            "hobbyName": "sports",
            "interestLevel": 3
        }
    ]
}
```

#### Dependencies

This implementation has one dependency, **spring-boot-starter-data-mongodb**. The **maven**/**gradle** dependencies of the same is mentioned below.

##### MongoDB

~~~xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
~~~

or

~~~txt
implementation 'org.springframework.boot:spring-boot-starter-data-mongodb'
~~~

#### Basic Usage

##### Application Configuration

In the **`application.properties`** file configure the following properties. 

*Data Properties*

~~~txt
# Mongo server host. Cannot be set with URI.
spring.data.mongodb.host=localhost
# Mongo server port. Cannot be set with URI.
spring.data.mongodb.port=27017
# Database name.
spring.data.mongodb.database=spring
~~~

##### Application Execution

Build and run the application via an IDE or by issuing the following command:

~~~shell
mvnw spring-boot:run
~~~

---
