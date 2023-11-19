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
