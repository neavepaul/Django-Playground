# Django App Template Setup Guide

## Concepts Covered in the Template

### Django Project

Defines the structure of your application and configuration files.

### Django App

A Django application that includes models, views, templates, URLs, and other resources like static files.

### View

A function that determines what to do with incoming requests, and how to generate the corresponding response.

### URL or `urls.py`

Serves as the central URL configuration for your application, mapping incoming URL patterns to corresponding view functions or class-based views.

### Template

A file that defines the structure and presentation of the output to be rendered and displayed in a web browser.

## Step 1: Setup Environment and Install Packages

### Install Required Packages

Run the following commands:

```bash
pip install --upgrade distro-info
pip3 install --upgrade pip==23.2.1
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate
```

### Install Django

Run the following command to install Django:

```bash
pip install Django
```

## Step 2: Create a Django Project

### Create a New Django Project

Run the following command to create your first Django project:

```bash
django-admin startproject firstproject
```

A folder called `firstproject` will be created, which is a container wrapping up settings and configurations for a Django project.

## Step 3: Create a Django App

### Create a New Django App

Run the following command to create a Django app called `firstapp` within the project:

```bash
python3 manage.py startapp firstapp
```

Django created a project scaffold for you containing your first `firstapp` app.

#### Project-related Files:

-   `manage.py`: A command-line interface used to interact with the Django project to perform tasks such as starting the server, migrating models, and so on.
-   `firstproject/settings.py`: Contains the settings and configurations information.
-   `firstproject/urls.py`: Contains the URL and route definitions of your Django apps within the project.

#### App-related Files:

-   `firstapp/admin.py`: For building an admin site.
-   `firstapp/models.py`: Contains model classes.
-   `firstapp/views.py`: Contains view functions/classes.
-   `firstapp/urls.py`: Contains URL declarations and routing for the app.
-   `firstapp/apps.py`: Contains configuration metadata for the app.
-   `firstapp/migrations/`: Model migration scripts folder.

## Step 4: Perform Migrations

### Generate Migration Scripts

Run the following command to generate migration scripts:

```bash
python3 manage.py makemigrations
```

### Apply Migrations

Run the following command to apply the migrations to your database:

```bash
python3 manage.py migrate
```

## Step 5: Start the Development Server

Run the following command to start a development server hosting apps in `firstproject`:

```bash
python3 manage.py runserver
```

Stop the Django server by pressing `Control + C` or `Ctrl + C` in the terminal.

## Step 6: Include Your App in the Project

### Add Your App to `INSTALLED_APPS`

Open `firstproject/settings.py` and find the `INSTALLED_APPS` section. Add a new app entry:

```python
'firstapp.apps.FirstappConfig',
```

### Add the App URLs to the Project URLs

Create an empty `urls.py` under the `firstapp` folder:

```bash
cd firstapp
touch urls.py
```

Open `firstproject/urls.py`, and add the `include` method from `django.urls` package:

```python
from django.urls import include, path
```

Then add a new path entry:

```python
path('firstapp/', include('firstapp.urls')),
```

## Step 7: Create Your First View

### Define the View

Open `firstapp/views.py` and write your first view:

```python
from django.http import HttpResponse

def index(request):
    template = "<html>This is your first view</html>"
    return HttpResponse(content=template)
```

### Configure the URL for the View

Open `firstapp/urls.py` and add the following code:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

## Step 8: Test Your First View

### Run the Django Server

Run the Django server if it is not already started:

```bash
cd ..
python3 manage.py runserver
```

Django will map any HTTP requests starting with `/firstapp` to `firstapp` and search for matches in `firstapp/urls.py`.
