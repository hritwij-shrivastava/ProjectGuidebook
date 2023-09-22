# Django Project Setup Guide

This README.md file provides step-by-step instructions on setting up a Django project using Visual Studio Code. Follow these steps to create a basic Django project with an app named "home" that includes a contact form.

## Prerequisites

Before you begin, make sure you have the following prerequisites installed:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Python](https://www.python.org/downloads/)
- [Django](https://www.djangoproject.com/download/)

## Step 1: Shift + Right Click

Begin by opening your project folder in Visual Studio Code. You can right-click on the folder and select "Open with Code" to open it in VS Code.

## Step 2: Install Django Extension in VS Code

If you haven't already, install the Django extension for Visual Studio Code. This extension provides useful features for Django development.

## Step 3: Install Python Extension in VS Code

Install the Python extension for Visual Studio Code to enhance your Python development experience.

## Step 4: Create a Django Project

Open the integrated terminal in VS Code and run the following command to create a new Django project:

```bash
django-admin startproject Projectname
```

Replace `Projectname` with the desired name for your Django project.

## Step 5: Start the Development Server

Navigate to your project folder and run the following command to start the Django development server:

```bash
python manage.py runserver
```

## Step 6: Understand Django's MVT Architecture

Django uses the MVT (Model View Template) architecture for building web applications. Familiarize yourself with this architecture by referring to the [Django documentation](https://docs.djangoproject.com/en/3.1/).

## Step 7: Create a Django App

In the integrated terminal, run the following command to create a new Django app named "home":

```bash
python manage.py startapp home
```

## Step 8: Configure URLs

- In the project folder, open the `urls.py` file.
- In the "home" app folder, create a `urls.py` file.
- Configure the URLs by copying the necessary code into these files.

## Step 9: Configure URLs (Project Folder)

In the `urls.py` file located in the project folder, add the following code to configure the URLs:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('home.urls')),
]
```

## Step 10: Configure URLs (Home App Folder)

In the `urls.py` file located in the "home" app folder, add the following code to configure the URLs:

```python
from django.contrib import admin
from django.urls import path
from home import views

urlpatterns = [
    path("", views.index, name='home'),
]
```

## Step 11: Create a View

In the `views.py` file located in the "home" app folder, create a simple view as follows:

```python
from django.shortcuts import render, HttpResponse

def index(request):
    return HttpResponse("This is the homepage")
```

## Step 12: Static Files

Refer to the [Django documentation](https://docs.djangoproject.com/en/3.1/howto/static-files/) on how to configure and manage static files in your project.

## Step 13: Configure Static Files in `settings.py`

In the `settings.py` file of your project, add the following lines of code to configure static files:

```python
STATICFILES_DIRS = [
    BASE_DIR / "static",
    '/var/www/static/',
]

# Also, add the following line inside the TEMPLATES configuration:
'DIRS': [BASE_DIR / "templates"],
```

## Step 14: Create a Template View

In the `views.py` file located in the "home" app folder, create a template view as follows:

```python
def template(request):
    return render(request, 'index.html')
```

## Step 15: Configure URL for Template View

In the `urls.py` file located in the "home" app folder, add the following code to configure the URL for the template view:

```python
path("tmp", views.template, name='hello'),
```

## Step 16: Use Variables in Templates

To use variables in HTML templates, follow these steps:

- Inside HTML files, use `{{ variable }}` to display variables.
- Inside the view function, create a context dictionary to pass variables to templates.

```python
# Inside views function
context = {
    'variable': "This is sent"
}
```

## Step 17: Create a Form

Inside your HTML file (`index.html`), create a form using the `<form>` tag. Set the form's `method` and `action` attributes as needed.

```html
<form method="post" action="/contact">
```

## Step 18: Run Migrations

In the integrated terminal, run the following command to apply database migrations:

```bash
python manage.py migrate
```

## Step 19: Create a Superuser

Create a superuser account to access the Django admin interface:

```bash
python manage.py createsuperuser
```

## Step 20: Define a Model

In the `models.py` file located in the "home" app folder, define a model for a contact form:

```python
from django.db import models

class ContactForm(models.Model):
    name = models.CharField(max_length=122)
    email = models.CharField(max_length=122)
    phone = models.CharField(max_length=122)
    desc = models.TextField()
    date = models.DateField()

    def __str__(self):
        return self.name
```

## Step 21: Register the Model in Admin

In the `admin.py` file located in the "home" app folder, register the `ContactForm` model:

```python
from home.models import ContactForm
admin.site.register(ContactForm)
```

## Step 22: Update `INSTALLED_APPS`

In your project's `settings.py` file, add the app's configuration name to the `INSTALLED_APPS` list:

```python
INSTALLED_APPS = [
    'home.apps.HomeConfig',
    # ...
]
```

## Step 23: Apply Migrations Again

Run migrations again to update the database schema with the new model:

```bash
python manage.py makemigrations
python manage.py migrate
```

## Step 24: Create a Contact View

In the `views.py` file located in the "home" app folder, create a view to handle the contact form submission:

```python
from datetime import datetime
from home.models import ContactForm

def contact(request):
    if request.method == "POST":
        name = request.POST.get('name')
        email = request.POST.get('email')
        phone = request.POST.get('phone')
        desc = request.POST.get('desc')
        contact = ContactForm(name=name, email=email, phone=phone, desc=desc, date=datetime.today())
        contact.save()
```

You have now completed the basic setup of your Django project with a "home" app that includes a contact form. You can continue building your project by adding more views, templates, and functionality as needed.