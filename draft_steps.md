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




- view.py
```
def home(request):
    # Retrieve all records from the Record model
    records = Record.objects.all()

    # Check if the request method is POST (form submission for login)
    if request.method == 'POST':
        # Retrieve username and password from the POST request
        username = request.POST['username']
        password = request.POST['password']

        # Authenticate user using Django's authentication system
        user = authenticate(request, username=username, password=password)

        # Check if the user is authenticated successfully
        if user is not None:
            # Log in the authenticated user
            login(request, user)
            # Display success message upon successful login
            messages.success(request, "You Have Been Logged In!")
            # Redirect to the 'home' page
            return redirect('home')
        else:
            # Display error message if login fails
            messages.success(request, "There Was An Error Logging In, Please Try Again...")
            # Redirect to the 'home' page
            return redirect('home')
    else:
        # If request method is not POST (GET request), render the home page
        return render(request, 'home.html', {'records': records})

# Markdown Explanation:
# 1. **Retrieve Records:** Fetches all records from the `Record` model using `Record.objects.all()`.
# 2. **Check Request Method:** Determines if the incoming request is a POST request (typically from a login form submission).
# 3. **Authenticate User:**
#    - Retrieves the `username` and `password` from the POST data.
#    - Uses Django's built-in `authenticate` function to verify the user's credentials.
#    - If authentication succeeds, logs in the user using `login(request, user)`.
# 4. **Handle Authentication Result:**
#    - If authentication is successful, a success message is added using Django's `messages.success` and redirects the user to the 'home' page.
#    - If authentication fails, an error message is added using `messages.error` and redirects back to the 'home' page.
# 5. **Render Home Page:** If the request method is not POST (GET request), renders the 'home.html' template with the retrieved records.
```

--


