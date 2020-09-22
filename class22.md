# Django CRUD and Forms

CRUD stands for Create, Read, Update & Delete. These are the four basic operations which are executed on Database Models.

![crud](https://media.geeksforgeeks.org/wp-content/uploads/20200114185631/Untitled-Diagram-316-1024x630.jpg)

* **Create** – create or add new entries in a table in the database.
* **Retrieve** – read, retrieve, search, or view existing entries as a list(List View) or retrieve a * particular entry in detail (Detail View)
* **Update** – update or edit existing entries in a table in the database
* **Delete** – delete, deactivate, or remove existing entries in a table in the database

## Django forms

Handling forms is a complex business. Consider Django’s admin, where numerous items of data of several different types may need to be prepared for display in a form, rendered as HTML, edited using a convenient interface, returned to the server, validated and cleaned up, and then saved or passed on for further processing.

Django’s form functionality can simplify and automate vast portions of this work, and can also do it more securely than most programmers would be able to do in code they wrote themselves.

Django handles three distinct parts of the work involved in forms:

* Preparing and restructuring data to make it ready for rendering
* Creating HTML forms for the data
* Receiving and processing submitted forms and data from the client

It is possible to write code that does all of this manually, but Django can take care of it all for you.

### Building a Django Form

To build a Django form, we will use **Form Class**. First, create a file named forms.py.

We already know what we want our HTML form to look like. Our starting point for it in Django is this:

``` python
from django import forms

class NameForm(forms.Form):
    your_name = forms.CharField(label='Your name', max_length=100)
```

A Form instance has an **is_valid()** method, which runs validation routines for all its fields. When this method is called, if all fields contain valid data, it will:

* return True
* place the form’s data in its cleaned_data attribute.

### The view

Form data sent back to a Django website is processed by a view, generally the same view which published the form. This allows us to reuse some of the same logic.

To handle the form we need to instantiate it in the view for the URL where we want it to be published:

```python
from django.http import HttpResponseRedirect
from django.shortcuts import render

from .forms import NameForm

def get_name(request):
    # if this is a POST request we need to process the form data
    if request.method == 'POST':
        # create a form instance and populate it with data from the request:
        form = NameForm(request.POST)
        # check whether it's valid:
        if form.is_valid():
            # process the data in form.cleaned_data as required
            # ...
            # redirect to a new URL:
            return HttpResponseRedirect('/thanks/')

    # if a GET (or any other method) we'll create a blank form
    else:
        form = NameForm()

    return render(request, 'name.html', {'form': form})
```

If we arrive at this view with a GET request, it will create an empty form instance and place it in the template context to be rendered. This is what we can expect to happen the first time we visit the URL.

If the form is submitted using a POST request, the view will once again create a form instance and populate it with data from the request: form = NameForm(request.POST) This is called “binding data to the form” 

We call the form’s is_valid() method; if it’s not True, we go back to the template with the form. This time the form is no longer empty (unbound) so the HTML form will be populated with the data previously submitted, where it can be edited and corrected as required.

If is_valid() is True, we’ll now be able to find all the validated form data in its cleaned_data attribute. We can use this data to update the database or do other processing before sending an HTTP redirect to the browser telling it where to go next.


### The template

We don’t need to do much in our name.html template:

``` html
<form action="/your-name/" method="post">
    {% csrf_token %}
    {{ form }}
    <input type="submit" value="Submit">
</form>
```

All the form’s fields and their attributes will be unpacked into HTML markup from that {{ form }} by Django’s template language.

