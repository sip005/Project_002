Sure, I'll format the steps and code snippets in a more organized way using proper markdown syntax:

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
