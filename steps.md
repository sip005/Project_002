### Steps - 18/11/23

1. Create a directory and navigate into it:
    ```bash
    mkdir dcrm
    cd dcrm
    ```

2. Set up a Python virtual environment and activate it:
    ```bash
    python3 -m venv virt
    source virt/bin/activate
    ```

3. Install Django and necessary MySQL-related packages:
    ```bash
    pip install django
    pip install mysql-connector-python
    pip install mysql-connector
    ```

4. Create a Django project named "dcrm":
    ```bash
    django-admin startproject dcrm
    ```

5. View the directory structure using the `tree` command:
    ```bash
    tree -L 3
    ```

6. Navigate into the Django project directory and create a new app named "website":
    ```bash
    cd dcrm
    cd dcrm
    python3 manage.py startapp website
    ```

7. Open the `settings.py` file using a text editor (e.g., `nvim`) within the inner 'dcrm' folder:
    ```bash
    cd dcrm
    nvim settings.py
    ```

8. Inside the `settings.py` file, add 'website' to the `INSTALLED_APPS` list:
    ```python
    # Application definition

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'website',
    ]
    ```

9. Update the database configuration in the `settings.py` file to use MySQL:
    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'elderco',
            'USER': 'root',
            'PASSWORD': '1234',
            'HOST': 'localhost',
            'PORT': '3306',
        }
    }
    ```

Please make sure to replace `'1234'` with the actual password for your MySQL setup, and adjust other configurations as needed for your specific environment.

### Steps - 22/11/23

##### Database Setup

1. Create `mydb.py`:
    ```python
    # Install MySQL on your computer
    # https://dev.mysql.com/downloads/installer/
    # pip install mysql-connector

    import mysql.connector

    dataBase = mysql.connector.connect(
        host='localhost',
        user='root',
        passwd='password123'
    )

    cursorObject = dataBase.cursor()

    # Create a database
    cursorObject.execute("CREATE DATABASE elderco")

    print("All Done!")
    ```

2. Run `python3 mydb.py` and verify the output 'All Done!'

#### Django Setup
3. Run `python3 manage.py migrate` in your Django project directory.

4. For Windows, use `winpty python manage.py createsuperuser`, or on other systems, run `python3 manage.py createsuperuser`.
   - Enter username as 'root' and password as 'toor'.

5. Update `settings.py`:
   ```python
   ALLOWED_HOSTS = ['127.0.0.1', 'localhost', '192.168.1.25']
   ```

6. Ensure Django server runs locally:
   - Run `python3 manage.py runserver` or specify a different port with `python3 manage.py runserver 0.0.0.0:8080`.

7. Modify `dcrm/urls.py`:
   ```python
   from django.urls import path, include
   
   urlpatterns = [
       path('admin/', admin.site.urls),
       path('', include('website.urls')),
   ]
   ```

8. Create a new file named `urls.py` within `website/` and add URL patterns.

9. Modify `views.py` to set up basic views:
   ```python
   from django.shortcuts import render

   def home(request):
       return render(request, 'home.html', {})
   ```

10. Create a 'Templates' folder:
    - Inside, create `hello.html` and add content.

11. Restart the server to confirm changes.

12. Create `base.html` with Bootstrap:
    - Include Bootstrap CDN references and create a base layout with `{% block content %}` in the body.

13. Create `navbar.html`:
    - Use Bootstrap code for a navbar.
    - Change style to dark and modify navbar details.

14. Integrate `navbar.html` in `base.html` using `{% include 'navbar.html' %}`.
   - Use `{% url 'home' %}` for home link in the navbar.

15. Update content in `home.html` to extend `base.html`:
    ```html
    {% extends 'base.html' %}

    {% block content %}
        <!-- Your content here -->
    {% endblock %}
    ```

16. Restart the server and check for reflected changes.

These steps will guide you through setting up a basic Django application with necessary database configuration, URL routing, views, and templates using Bootstrap for styling. Adjust the specifics as needed for your project requirements.

### Steps - 
