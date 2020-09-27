# Python Docker

Docker is a containerization tool used for spinning up isolated, reproducible application environments. It is a popular development tool for Python developers.

When you develop an application, you need to provide your code along with all possible dependencies like libraries, the web server, databases, etc. You may end up in a situation when the application is working on your computer, but won’t even start on the staging server, or the dev or QA’s machine.

This challenge can be addressed by isolating the app to make it independent of the system.

### Docker VS Virtualization

Traditionally, virtual machines were used to avoid this unexpected behavior. The main problem with VM is that an “extra OS” on top of the host operating system adds gigabytes of space to the project. Most of the time your server will host several VMs that will take up even more space. And by the way, at the moment, most cloud-based server providers will charge you for that extra space. Another significant drawback of VM is a slow boot.

Docker eliminates all the above by simply sharing the OS kernel across all the containers running as separate processes of the host OS.


### Why do we need Docker?

The short list of benefits includes:

* Faster development process
* Handy application encapsulation
* The same behaviour on local machine / dev / staging / production servers
* Easy and clear monitoring
* Easy to scale



# Library Website and API

Django REST Framework works alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework; it always must be added to a project after Django itself has been installed and configured. The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

Django and DRF( Django Rest Framework ) are different in the way they are being used. If you want to create a web application django will be helpful for that and if you want to create APIs only then DRF can be useful.


The Django REST framework is distributed as a standard Python package. So to get started you need to install the Django REST framework with the command: pip install djangorestframework.

Once you install the Django REST framework package, add it to the INSTALLED_APPS list variable in your Django project's settings.py file with the name rest_framework. Once this is done, you can start working with the Django REST framework. 


#### Serializers and views

Serializers are one of the main building blocks of the Django REST framework used to define the representation of data records, which are generally based on Django models. Python records can have ambiguous data representations (e.g. a record with a datetime value can be represented as DD/MM/YYYY, DD-MM-YYYY or MM-YYYY) and a serializer removes any uncertainty about how to represent a record. Listing 12-3 illustrates a Django REST framework serializer using one its serializers package.









