### Steps - 18/11/23
- mkdir dcrm
- cd dcrm
- python3 -m venv virt
- source virt/bin/activate
- pip install django
- pip install mysql
- pip install mysql-connector-python
- pip install mysql-connector
- django-admin startproject dcrm
- tree -L 3
- cd dcrm
- cd dcrm
- python3 manage.py startapp website
- ls
- cd dcrm
- nvim settings.py
  - Add website to installed apps
    ```
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
  - Make changes to the database section
  ```
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
- Add website to installed apps
