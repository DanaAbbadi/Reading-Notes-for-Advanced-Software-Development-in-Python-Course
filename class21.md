# Django Models

A Django model is the built-in feature that Django uses to create tables, their fields, and various constraints. In short, Django Models is the SQL of Database one uses with Django. SQL (Structured Query Language) is complex and involves a lot of different queries for creating, deleting, updating or any other stuff related to database. Django models simplify the tasks and organize tables into models. Generally, each model maps to a single database table.

we can use admin panel of Django to create, update, delete or retrieve fields of a model and various similar operations. Django models provide simplicity, consistency, version control and advanced metadata handling. Basics of a model include –

* Each model is a Python class that subclasses ```django.db.models.Model```.
* Each attribute of the model represents a database field.
* With all of this, Django gives you an automatically-generated database-access API.


In Django, the model is the object mapped to the database. When you create a model, Django executes SQL to create a corresponding table in the database without you having to write a single line of SQL. Django prefixes the table name with the name of your Django application. The model also links related information in the database.

![db](https://djangobook.com/wp-content/uploads/model_table1_600.png)

## Designing the LocalLibrary models

When designing your models it makes sense to have separate models for every "object" (a group of related information).

Once we've decided on our models and field, we need to think about the relationships. Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).


### Creating a Model

Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata.

``` python
from django.db import models

class MyModelName(models.Model):
    """A typical class defining a model, derived from the Model class."""

    # Fields
    my_field_name = models.CharField(max_length=20, help_text='Enter field documentation')
    ...

    # Metadata
    class Meta: 
        ordering = ['-my_field_name']

    # Methods
    def get_absolute_url(self):
        """Returns the url to access a particular instance of MyModelName."""
        return reverse('model-detail-view', args=[str(self.id)])
    
    def __str__(self):
        """String for representing the MyModelName object (in Admin site etc.)."""
        return self.my_field_name
```

### Metadata

You can declare model-level metadata for your Model by declaring class Meta, as shown.

``` python
class Meta:
    ordering = ['-my_field_name']

```
