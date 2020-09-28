# DRF Permissions

In DRF We can use the permissions to implement RBAC (Role-Based Access Control). Role-Based Access Control is an approach that restricts access to users based on their role. You can use Django’s authentication and authorization features to configure Role-Based Access Control.

Django user authentication has built-in models like User, Group, and Permission.

* User: The heart of authentication
* Group: Way of categorizing User
* Permission: Granular access control

## Permissions

Permissions are used for different classes of users and for different parts of the API. DRF always check permissions before running any code in views.

Permissions in DRF represent a list of classes that must be checked before any code executes. There are 7 pre-built permission classes in DRF:

* AllowAny
* IsAuthenticated
* IsAdminUser
* IsAuthenticatedOrReadOnly
* DjangoModelPermissions
* DjangoModelPermissionsOrAnonReadOnly
* DjangoObjectPermissions

You can either build custom classes by yourself.

Permissions in Django REST Framework may be set in 3 different ways:

* Globally to all API endpoints
* Into the views or viewsets
* On an object level

## Setting permissions globally

Setting permissions globally is the easiest way to implement user access to your API. You can do it by adding a string to your Django project's settings.py file:

    REST_FRAMEWORK = {
        'DEFAULT_PERMISSION_CLASSES': [
            'rest_framework.permissions.IsAuthenticated',
        ]
    }

Now we can't access our API endpoints without authentication:

Setting permissions in views
The second way to set permissions in our Django project is to specify it in the views(or in the viewsets).

We have 3 viewsets in views.py:


    from django.shortcuts import render
    from django.contrib.auth.models import User, Group
    from rest_framework import viewsets
    from starter.app.serializers import UserSerializer, GroupSerializer
    from .models import Task
    from .serializers import TaskSerializer

    class UserViewSet(viewsets.ModelViewSet):
    
        queryset = User.objects.all().order_by('-date_joined')
        serializer_class = UserSerializer

    class GroupViewSet(viewsets.ModelViewSet):
    
        queryset = Group.objects.all()
        serializer_class = GroupSerializer

    class TaskViewSet(viewsets.ModelViewSet):

        queryset = Task.objects.all()
        serializer_class = TaskSerializer





