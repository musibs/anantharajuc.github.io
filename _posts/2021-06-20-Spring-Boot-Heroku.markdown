---
title: "Spring Boot Web Application Deployment on Heroku (PaaS)"
author: anantharajuc
categories: [ Cloud, Heroku, Spring Boot, Java ]
tags: [ Cloud, Heroku, Spring Boot, Java ]
layout: post
date: 2021-06-20 19:35
image: /assets/images/spring-boot-heroku.jpg
---

This post documents the necessary steps needed to deploy a simple web application packaged as a jar file and developed using Java Spring Boot framework on Heroku, using the Heroku Git deployment method.

---

#### Software Requirements

- [Git](https://git-scm.com/downloads)
- [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install)

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to deploy on the Heroku platform. 

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>

#### Heroku Deployment steps

- In this step we assume that the project repository (source code files) is tracked through git, the code is committed and is ready for deployment.

- Login to the [Heroku Web Portal](https://id.heroku.com/login), create a new web app. Name the web app and choose a region (United States/Europe).

![Heroku Web Portal Project Creation]({{ site.baseurl }}/assets/images/spring-boot/heroku/heroku-web-portal-project-creation.PNG)  

- In your local machine, from the command line tool, navigate to the project directory.

- Login to the Heroku platform via command line. This can be done in two ways.

	- *Method 1* : **`heroku login`** You’ll be prompted to enter any key to go to your web browser to complete login. The CLI will then log you in automatically.
	
	- *Method 2* : **`heroku login -i`** In this method, you will complete the login by entering your credentials from the command line itself.  
	
	![Heroku Login]({{ site.baseurl }}/assets/images/spring-boot/heroku/heroku-login.PNG)  
	
- Add Heroku's remote repository to the project. The command to do so has the following structure. **`heroku git:remote -a [APP_NAME]`**

	- In case of the above mentioned project, the command to do so is **`heroku git:remote -a spring-boot-minimal-web-app`**  
	
	![Add Remote Repository]({{ site.baseurl }}/assets/images/spring-boot/heroku/add-remote-repository.PNG)  
	
	- **`git remote -v`** command can be used to see the remote URL added to the project.  
	
	![List Remote URL]({{ site.baseurl }}/assets/images/spring-boot/heroku/list-remote-url.PNG)  

- Finally, push the project to Heroku's remote repository added in the previous step. **`git push heroku main`**

	![Build Log - Beginning]({{ site.baseurl }}/assets/images/spring-boot/heroku/git-push-heroku-main-start.PNG)    

	![Build Log - End]({{ site.baseurl }}/assets/images/spring-boot/heroku/git-push-heroku-main-end.PNG)   

	- The Build log can also be viewed in the Heroku console under the project's **Activity** tab.

	![Build Log - Heroku]({{ site.baseurl }}/assets/images/spring-boot/heroku/build-log-heroku.PNG)  
	
#### Accessing the deployed application	

- Access the deployed web application from the URL **[APP_NAME].herokuapp.com**. In case of the above mentioned project the URL will be **spring-boot-minimal-web-app.herokuapp.com**

![App URL]({{ site.baseurl }}/assets/images/spring-boot/heroku/app-url.PNG)  

#### Cleanup

- In order to delete the project, navigate to the bottom of the **Settings** tab and click on the **Delete** button.

![Delete Project]({{ site.baseurl }}/assets/images/spring-boot/heroku/delete-project.PNG)  

--- 