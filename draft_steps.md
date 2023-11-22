### Draft steps
- Create mydb.py
  ```
  # Install Mysql on your computer
# https://dev.mysql.com/downloads/installer/
# pip install mysql
# pip install mysql-connector
# pip install mysql-connector-python 

import mysql.connector

dataBase = mysql.connector.connect(
	host = 'localhost',
	user = 'root',
	passwd = 'password123'

	)

# prepare a cursor object
cursorObject = dataBase.cursor()

# Create a database
cursorObject.execute("CREATE DATABASE elderco")

print("All Done!")
```

- python3 mydb.py
- Get OUTPUT 'All Done!`
- Run `python3 manage.py migrate`
- For windows ` winpty python manage.py createsuperuser`
- python3 manage.py createsuperuser
 - name root
 - password toor
- 
-
- make changes to
# settings.py

ALLOWED_HOSTS = ['127.0.0.1', 'localhost', '192.168.1.25']

- python3 manage.py runserver
- python3 manage.py runserver 0.0.0.0:8080
- make changes to dcrm/urls.py
-

- make changes to dcrm/urls.py
- Add include in the `from django.urls import path, include`
- Make change in url path patterns
- Add website.urls 
```
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('website.urls')),
]
```
- Create a new file named urls.py 
- add the following content in the file
```
from django.urls import path
from . import views


urlpatterns = [
    path('', views.home, name='home'),
    #path('login/', views.login_user, name='login'),
    path('logout/', views.logout_user, name='logout'),
    path('register/', views.register_user, name='register'),
    path('record/<int:pk>', views.customer_record, name='record'),
    path('delete_record/<int:pk>', views.delete_record, name='delete_record'),
    path('add_record/', views.add_record, name='add_record'),
    path('update_record/<int:pk>', views.update_record, name='update_record'),

]
```
- Make changes to view.py
```
from django.shortcuts import render, redirect

def home(request):
	return render(request, 'home.html', {})
```
- Create Template folder

- Inside the template folder make a hello.html

- Wirte contents inside that html file

- now restart the server to see the changes are reflecting

- after getting confirmed we will create a base.html with the help of bootstrap

- create base.html and insert the demo bootstrap code containing cdn reference link

- inside the base.html add the following snippet of code for the home.html

```
    <div class="container">
       {% block content %}
       {% endblock %}
    </div>
```

- Create a new navbar.html

- insert code from the bootstrap site

-  change the navbar light to dark - by searching the keyword 

- change the name of the navbar

- {% url 'home' %}

- make changes accordingly to the navbar.html


