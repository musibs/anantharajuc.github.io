---
layout: post
title: "Gitflow Workflow"
author: anantharajuc
categories: [ Git, CLI ]
tags: [ Git, CLI ]
date: 2020-10-13 13:30
image: /assets/images/Git.png
---

Gitflow Workflow is a Git strategy that helps with continuous software development and implementing DevOps practices. It was first published and made popular by Vincent Driessen at nvie. The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects.  

##### STEP 1/6: clone a remote git repository
				
*	**`git clone <remote-repository-url>`**  
clone a remote git repository to a local system.  
example: **`git clone https://github.com/username/repository.git`**

---

##### STEP 2/6: create **DEVELOP** branch - This is the main code-line

1. **`git checkout -b develop`**  
create and switch to a branch called **develop**

2. **`git push -u origin develop`**  
links local **develop** branch with remote corresponding **develop** branch  
push local branch to remote repository for the first time (first time only)

---

##### STEP 3/6: create/checkout **FEATURE** branch 

1. **`git checkout -b featureBranch`**  
create and switch to a branch called featureBranch

	1.1 **`git add .`**  
	add or modify files  

	1.2 **`git commit -m "ADD/MODIFY File/s"`**  
	commit changes

2. **`git push -u origin featureBranch`**  
links local branchName with remote corresponding branch

---

##### STEP 4/6: integrate featureBranch branch with the main code-line i.e., the **DEVELOP** branch
 
1. **`git checkout develop`**

2. **`git pull`**

3. **`git merge featureBranch`**

4. **`git push`**

---

##### STEP 5/6: release code from **develop** branch (Normally code is released from a dedicated **release** branch taken from **develop**). In this case assume develop contains valid releaseable code.

1. **`git checkout main`**

2. **`git pull`**

3. **`git merge develop`**

4. **`git push`**

---

##### STEP 6/6: create a tag representing the release

A **tag** is a special branch which can be setup to read only, giving us the certainity to always have a branch we can go back to in-order to reproduce releaseable code

1. **`git tag "1.0.0.RELEASE" -m "Releasing version 1.0.0"`**

2. **`git push --tags`**

---