# Django Introduction

![django](https://miro.medium.com/max/1000/1*lV8QK54M8fVOza03A77daw.jpeg)

Django is a Web framework written in Python. A Web framework is a software that supports the development of dynamic Web sites, applications, and services. It provides a set of tools and functionalities that solves many common problems associated with Web development, such as security features, database access, sessions, template processing, URL routing, internationalization, localization, and much more.

The main goal of the Django framework is to allow developers to focus on components of the application that are new instead of spending time on already developed components. Django is fully featured than many other frameworks on the market. It takes care of a lot of hassles involved in web development; enables users to focus on developing components needed for their application.

Security is also a high priority for Django. It has one of the best out-of-the-box security systems out there, and it helps developers avoid common security issues, including
* clickjacking,
* cross-site scripting
* SQL injection.

Among the biggest Web sites using Django we have: Instagram, Disqus, Mozilla, Bitbucket, Lastfm, National Geographic.

## The Structure of a Django Website

A Django website consists of a single project that is split into separate apps. The idea is that each app handles a self-contained function that the site needs to perform.


The Django project holds some configurations that apply to the project as a whole, such as project settings, URLs, shared templates and static files. Each application can have its own database and has its own functions to control how the data is displayed to the user in HTML templates.

Each application also has its own URLs as well as its own HTML templates and static files, such as JavaScript and CSS.

Django apps supports the Model-View-Controller Pattern, which is the architecture on which most web frameworks are built, where the basic principle is that in each application there are three separate files that handle the three main pieces of logic separately:

* **Model** defines the data structure. This is usually a database and is the base layer to an application.
* **View** displays some or all of the data to the user with HTML and CSS.
* **Controller** handles how the database and the view interact.

However, Django handles the controller part itself. There’s no need to define how the database and views interact. It’s all done for you!

The pattern Django utilizes is called the Model-View-Template (MVT) pattern. The view and template in the MVT pattern make up the view in the MVC pattern. All you need to do is add some URL configurations to map the views to, and Django handles the rest!

![mvt](https://www.tutorialspoint.com/django/images/django_mvc_mvt_pattern.jpg)


Django web applications typically group the code that handles each of these steps into separate files:

![dj](https://mdn.mozillademos.org/files/13931/basic-django.png)

### **URLs**:

A URL mapper is used to redirect HTTP requests to the appropriate view based on the request URL. The URL mapper can also match particular patterns of strings or digits that appear in a URL and pass these to a view function as data.

### **View**:
  
A view is a request handler function, which receives HTTP requests and returns HTTP responses. Views access the data needed to satisfy requests via models, and delegate the formatting of the response to templates.

### **Models**:
Models are Python objects that define the structure of an application's data, and provide mechanisms to manage (add, modify, delete) and query records in the database. 
  
### **Templates**:
A template is a text file defining the structure or layout of a file (such as an HTML page), with placeholders used to represent actual content. A view can dynamically create an HTML page using an HTML template, populating it with data from a model. A template can be used to define the structure of any type of file; it doesn't have to be HTML!



