---
title: "Docker and Spring Boot"
author: anantharajuc
categories: [ Spring Boot, Docker ]
layout: post
date: 2021-06-25 17:30
image: /assets/images/spring-boot-docker.jpg
---

This post briefly documents the creation of a [Docker](https://www.docker.com/) image from a [Spring Boot](https://spring.io/projects/spring-boot) based Java (Web Application) project.

---

#### Minimum Software Requirements

- Java
- [Maven](https://maven.apache.org/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Oracle VM VirtualBox](https://www.virtualbox.org/) or any other [hypervisor](https://en.wikipedia.org/wiki/Hypervisor)
- [Postman](https://www.postman.com/downloads/)

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to illustrate the creation and usage of the created docker image.

| *Method*   |    |  *URL*                                 |
|------------|----|----------------------------------------|
| **GET**    |    | **`http://localhost:8080/index.html`** |
| **GET**    |    | **`http://localhost:8080/`**           |
| **PUT**    |    | **`http://localhost:8080/`**           | 
| **POST**   |    | **`http://localhost:8080/`**           | 
| **DELETE** |    | **`http://localhost:8080/`**           |

#### Dependencies

A java project does not necessarily have any library dependency in order to create a docker image of that project.

However, in the plugins section of the **`pom.xml`** dependency management file there must be a plugin to package the project as an executable **jar**/**war** file.

~~~xml
<!-- Package as an executable jar/war. -->
<plugin>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
~~~

In the same **`pom.xml`** file, add the following details as well.

~~~xml
<version>latest</version>
<packaging>jar</packaging>
~~~

#### Basic Usage

Create a file named **`Dockerfile`** in the root of your project with the following details.

~~~txt
# Start with a base image containing Java runtime
FROM openjdk:8-jdk-alpine

# Add Maintainer Info
LABEL maintainer="example@domain.com"

# Add a volume pointing to /tmp
VOLUME /tmp

# Make port 8080 available to the world outside this container
EXPOSE 8080

# The application's jar file
ARG JAR_FILE=target/Spring-Boot-Minimal-Web-App-latest.jar

# Add the application's jar to the container
ADD ${JAR_FILE} Spring-Boot-Minimal-Web-App-latest.jar

# Run the jar file 
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/Spring-Boot-Minimal-Web-App-latest.jar"]
~~~

##### Maven

From the command line, navigate to project directory where the **pom.xml** file is present.

**`mvn clean`** : Clean the project and remove the files from the previous build. 

**`mvn validate`** : Check if all the information necessary for the build (**.jar**) are available.

**`mvn package`** : Runs all the tests and packages/builds the project to a **.jar** file. 

**`mvn package -Dmaven.test.skip=true`** : To skip the tests and package/build the project directly.

The above mentioned **.jar** file is present inside the **/target** directory.

##### Docker

###### Build 

**`docker images`** : Lists the already present container images.

**`docker build -t spring-boot-minimal-web-app .`** : Builds the docker image of the project as per the specifications mentioned in the **Dockerfile** file.

![Docker Build Image]({{ site.baseurl }}/assets/images/spring-boot-docker/1-docker-build.PNG)  

**`docker images`** : Check the docker image is generated from running the previous command.

![List Docker Images]({{ site.baseurl }}/assets/images/spring-boot-docker/2-docker-image-list.PNG)  

###### Run, Stop and Restart

**`docker run -p 8080:8080 --name spring-boot-minimal-web-app spring-boot-minimal-web-app`** : Run the newly created docker image.

![Docker Run]({{ site.baseurl }}/assets/images/spring-boot-docker/3-docker-run.PNG)  

**`docker stop spring-boot-minimal-web-app`** : Stop the container of the image.

![Stop Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/6-stop-running-docker-container.PNG)  

**`docker restart spring-boot-minimal-web-app`** : Restart the stopped container of the image.

![Restart Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/9-docker-container-restart.PNG)  

###### Logs

**`docker logs spring-boot-minimal-web-app`** : Lists container logs.

![Docker Logs]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs.PNG)  

**`docker logs spring-boot-minimal-web-app --tail N`** : Lists container logs. **--tail** flag will show the last **N** lines of logs.

![Docker Logs with tail]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs-tail.PNG)  

**`docker logs spring-boot-minimal-web-app --since YYYY-MM-DD`** : List container logs since a particular date.

![Docker Logs with date]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs-date.PNG) 

###### Clean-up

**`docker rm spring-boot-minimal-web-app`** : Remove the docker container.

![Remove Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/4-remove-docker-container.PNG)  

**`docker image rm spring-boot-minimal-web-app`** : Remove the docker image.

![Remove Docker Image]({{ site.baseurl }}/assets/images/spring-boot-docker/3-remove-docker-image.PNG)  



