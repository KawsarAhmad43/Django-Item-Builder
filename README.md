# Getting Started with Django: Creating a Simple App

## Step 1: Install Django

```bash
pip install Django
```

## Step 2: Create a Project
```bash
django-admin startproject myproject
cd myproject
```
## Step 3: Create an app
```bash
python manage.py startapp myapp
```
## Step 4: Define model in 'myapp/models.py'
```bash
# myapp/models.py
from django.db import models

class Item(models.Model):
    name = models.CharField(max_length=100)

    def __str__(self):
        return self.name
```
## Step 5: Register App in myproject/settings.py

##### for example:
INSTALLED_APPS = [
    # ... other installed apps ...
    'myapp',
]

## Step 6: Create Migrations and Apply
```bash
python manage.py makemigrations myapp
python manage.py migrate
```

## Step 7: Create Views in myapp/views.py
```bash

from django.shortcuts import render
from .models import Item

def item_list(request):
    items = Item.objects.all()
    return render(request, 'myapp/item_list.html', {'items': items})

```

## Step 8: Create Templates Folder and HTML Template

```bash
<!DOCTYPE html>
<html>
<head>
    <title>Item List</title>
</head>
<body>
    <h1>Item List</h1>
    <ul>
        {% for item in items %}
            <li>{{ item.name }}</li>
        {% endfor %}
    </ul>
</body>
</html>
```
## Step 9: Configure URLs
 * Create myapp/urls.py. and define url patterns.
 * Include the app's URLs in myproject/urls.py.

 ## Step 10: Run the Development Server
 ```bash
 python manage.py runserver
```
* Now you can navigate the project using this URL: [http://127.0.0.1:8000/myapp/items/](http://127.0.0.1:8000/myapp/items/)





