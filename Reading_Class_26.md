# Reading: Class 26

> [Back to the main](./README.md)

---

## Before starting 

### Django Framework
Django is a huge framework that allows us to build and configure web servers and applications. Django provides us with a lot of built-in helpful tools so we don't have to build the project from scratch. These tools are like the admin page manager and the authentication configurations. Providing us with these tools allows us to focus more on building the real application.

### Project's structure
Django project: it consists of multiple apps where each one has its purpose in the project. After creating the project, we can create apps as many as we need to implement the big project.
Django app: it is a part of the project that has a major job on it
Django URL: it is a part of the main URL of the website that will call a view to being applied
Django view: it is a function that handles an HTTP request or response
Django template: it is a holder to call HTML pages

### Installation

    pip install pipenv

### Preparing VSCode
if your terminal on SCode couldn't run the server effectively, you need to use the integrated terminal 
go to (View > Command Palette) then type (python interpreter) and hit enter
run the following command on the project's root directory to get the path of the virtual environment:
which python
copy-paste the path on the palette 
now we can run the server on the VSCode terminal  

---

## Creating a new project

Create a new directory (myProject)

    mkdir myProject
    cd myProject

Install the Django virtual environment

    pipenv install django 

the location for the virtual env will be provided by the terminal after the phrase (Virtual location) 

Enter the virtual environment
    
    pipenv shell

Create a new Django project 
create a project named (myProject), we have to add the dot at the end to create the project in the current directory instead of creating it twice (but you have to use the same name for both the project and the root directory we created at the begging)
    
    django-admin startproject myProject .

Migrate databases 
We use this command whenever starting a new project to migrate Django databases to our project 
python manage.py migrate

Create an admin account
Run the following command then fill the required info 
    
    python manage.py createsuperuser

Change some required settings
Go to (myProject/settings.py) and make these changes in the TEMPLATES list:
'DIRS': [BASE_DIR / "templates"],

Run the server
by default, the following command will start the server at the port 8000, a URL will be provided to go to our website: http://127.0.0.1:8000
python manage.py runserver
if we want to run it on a custom port:
    
    python manage.py runserver 3030


Go to the provided URL, if you see a page similar to the previous picture, then the project has been created successfully.
You can close the server by pressing (Ctrl+c) in the opened terminal 

Visit the admin page
Enter the URL of the server followed by (/admin) and enter the super user account's info you have created 
http://127.0.0.1:8000/admin

---

## Creating a new app

Create a new Django app 
create an app named (myApp) by going to the project's root directory and run the following:
    
    python manage.py startapp myApp

Add the app to the settings 
go to the file (myProject/settings.py) and inside the list (INSTALLED_APPS), add the name of the newly created app ("myApp") as another item on the list
IMPORTANT: you have to add the name of any new app you create to the settings file 


Project's structure

After creating the project and an app inside it, you will have a lot of files and folders inside the project's root directory:  

project's main dir: the main folder that has the name of the project (myProject)
> setting.py: a file that will have all the configurations of the project 
> urls.py: a file that will have all our URLs 

project's app: the folder that has the name of the app we created (myApp)
> admin.py: a file for managing the website 
> apps.py: a file for managing the apps
> models.py: a file for configuring models 
> tests.py: a file for implementing our unit tests
> views.py: a file where we define the view functions that handle HTTP requests and responses 

manage.py: a file that is used to run the server 
pipfile: a file that holds names of requirements and dependencies of the project 

---

## Views

In Django, a view is a function that handles HTTP requests and responses. 

Required imports
Make sure that all these imports are existed in the views.py file 

    from django.shortcut import render
    from django.http import HttpResponse 

Create a view
the view can provide any functionality like displaying data, requesting APIs, ...etc. 
IMPORTANT: for each view you create, you have to map it with a URL so it can be reached (we do that inside the app url file not the one in the main directory)

    def say_hello(request):
        return HttpResponse("Hello World !")

---

## URLs  

We need a file to hold all endpoints for this particular app. 

Define some views and templates
define views inside the (myProject/myApp/views.py) file to call them  
    
    from django.views.generic import TemplateView

    class HomeView(TemplateView):
        template_name = 'home.html'

    class AboutView(TemplateView):
        template_name = 'about.html'

define corresponding HTML files inside the (myProject/myApp/templates) folder to map them with the views (their names must bue the same as defined in the views)
myProject/myApp/templates/home.html
myProject/myApp/templates/about.html

Create the URL file
Create a file named (urls.py) inside the app 
    
    myProject/myApp/urls.py

Required imports
Make sure that all these imports are existed in the (myProject/myApp/urls.py) file 

    from django.urls import path
    from .views import HomeView, AboutView   # import the views  

Define the configuration
Every app should have its own URL configuration, so define the following inside the (myProject/myApp/urls.py):
    
    urlpatters = []

Map the endpoints with views 
Every view should be mapped with a custom unique URL so we can reach that view by entering its URL. So in the (myProject/myApp/urls.py): 

    urlpatters = [
        path('', HomeView.as_view(), name="home"),

        path('about/', AboutView.as_view(), name="about"),
    ]

Now go to the (myProject/urls.py) file that is located in the main directory and add the route of the new app (myApp) to the list (urlpatterns) with including its URL file (myProject/myApp/urls.py)
from django.urls import include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', include("myApp.urls")), 
    ]

IMPORTANT: for each app we create, we have to add its route to the main (myProject/urls.py) file


## Templates   

We need a folder to hold all templates for this particular app. 

Create the folder
Make sure to create a folder named (templates) inside each app 
myProject/myApp/templates

Create a template 
create an HTML file inside the (templates) directory for this app and name it (hello.html), then write some HTML code inside it
myProject/myApp/templates/hello.html

Map the template with a view 
in the (myProject/myApp/views) file, adjust the (say_hello) view to return the new HTML page we have created

    def say_hello(request):
        return render(request, "hello.html")

--- 

## Models   

Create a model
Go to the (myProject/myApp/models.py) file in the app and create a class (it should be named in a singular form). Add some widgets like the text fields.

    from django.db import models

    class Thing(models.Model):
        name = models.CharField(max_length=255)
        description = models.TextField()
        price = models.IntegerField()
        is_cool = models.BooleanField()

        def __str__(self):
            return self.name  # representation on the DB

Reflect model on the DB
We have to run these commands after creating any model to reflect the new data on the database

    python manage.py makemigrations
    python manage.py migrate

Add the model to the admin
Go to (myProject/myApp/admin.py) and add an admin class for the model  

    from django.contrib import admin
    from .models import Thing

    @admin.register(Thing)
    class AdminThing(admin.ModelAdmin):
        pass

