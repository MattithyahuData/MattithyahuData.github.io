---
layout: post
title:  "Project: 💻User Registration System"
date:   2021-12-04 16:30:58 +0100
categories: jekyll update
---
# Project Overview 
* Integrating mySQL databases and PHP scripts 
* Inserting values into database or reading values from them
* Mimicking platforms that use User registration and applying logic in PHP to ensure certain parameters 

## Table of Contents 
*   [Resources](#resources)<br>
*   [Database Creation](#Datacreate)<br>
*   [Page Creation](#Pagecreate)<br>
*   [Final View](#Finalview)<br>
*   [Project Management (Agile/Scrum/Kanban)](#Prjmanage)<br>
*   [Project Evaluation](#PrjEval)<br>
*   [Looking Ahead](#Lookahead)<br>
*   [Questions & Contact me](#Questions)<br

<a name="resources"></a> 

## Resources Used
**PHP, mySQL, Apache, XAMPP** 

<a name="Datacreate"></a> 

## Database creation 
Using localhost/phpmyadmin/ I created a new database and a new table with the fields that PHP scripts will point to

*   Fields:
    *   ID
    *   Username
    *   Email
    *   Password

<a name="Pagecreate"></a> 

## Page creation
After creating the table, I needed to create the different registration and login pages for the user. I made the following changes and created the following pages:

*   [registration.php](https://github.com/MattithyahuData/P9-User-Registration-System/blob/master/registration.php)
    *   4 inputs required for registration; Username, Email, Password, and confirm password
    *   All fields were requeired so required tag was added which would prevent fields from being submitted as null
    *   Login page referenced if User already had registered
*   [login.php](https://github.com/MattithyahuData/P9-User-Registration-System/blob/master/login.php)
    *   2 inputs required for login; Username and password 
    *   All fields were requeired so required tag was added which would prevent fields from being submitted as null
    *   Registration page referenced if User already had registered.
*   [server.php](https://github.com/MattithyahuData/P9-User-Registration-System/blob/master/server.php) 
    *   Connection to the database  
    *   Importing values enetered at registration
    *   Passwords were enrypted on database side so Database Administrator would not be able to view passwords
    *   Validation:
        *    if statements for validation e.g if Password and confirm password are not equal throw an error
        *    Not allowing existing usernames or emails from new users 
*   [index.php](https://github.com/MattithyahuData/P9-User-Registration-System/blob/master/index.php)
*   [errors.php](https://github.com/MattithyahuData/P9-User-Registration-System/blob/master/errors.php) 


<a name="Finalview"></a>

## Final View
Login page

<img src="/images/P9/LoginView.png" />


<a name="Prjmanage"></a> 

## [Project Management (Agile/Scrum/Kanban)](https://www.atlassian.com/software/jira)
* Resources used
    * Jira
    * Confluence
    * Trello 

<a name="PrjEval"></a> 

## [Project Evaluation]() 
*   WWW
    *   Front end and Back end engineering
*   EBI 
    *   Could this project be deployed? 
    

<a name="Lookahead"></a> 

## Looking Ahead
*  Can ML be used with a backend database such as this ?? Yes! 

<a name="Questions"></a> 

## Questions & Contact me 
For questions, feedback, and contribution requests contact me
* ### [Click here to email me](mailto:contactmattithyahu@gmail.com) 
* ### [See more projects here](https://mattithyahudata.github.io/)


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
