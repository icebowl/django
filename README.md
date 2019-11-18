# django notes:
https://linux4one.com/how-to-install-django-web-framework-on-debian-10/

Prerequisites

Before you start to install Django on Debian 10. You must have the non-root user account on your system with sudo privileges.

Install tree command to use it in the further tutorial for better understanding.

sudo apt install tree

Confirm Python Installation and Install venv

Python 3.5 is by default installed on Debian 10. Confirm the Python installation and check the Python version by typing the following command.

python3 -V

The output should be as give below. The note version number may vary.

Output:
Python 3.5.2

By using venv module we can create virtual environments in Python 3.6. To get venv module we need to install a python3-venv package to do so enter the following command.

sudo apt install python3-venv

Now we can create Virtual Environment for Django Applications.
Create Virtual Environment

Create a new directory for your Django application and go inside the directory.

mkdir new_django_app && cd new_django_app

Now create virtual Environment by running following command. It will create a directory named venv which includes supporting files, Standard python library, Python binaries, Pip package manager.

python3 -m venv venv

To start using the virtual environment we need to activate it. To activate the virtual environment run following command.

source venv/bin/activate

Now your path will change and it will show the name of your virtual environment (venv)
Install Django

Now install Django by using Pip (Python Package Manager).

pip install Django

Confirm the installation and Check the version typing following command.

python -m django --version

The output should be as given below. NOTE: you can get a slightly different output.

Output:
2.1.4

Creating a Django Project

Create a Django project by using django-admin utility named newdjangoapp. Enter the following command to create new Django project.

django-admin startproject newdjangoapp

Now the newdjangoappdirectory will be created. Check the directory structure by using the following command. This directory has manage.py file used to manage the project and other Django specific files about database configuration settings, routes, and settings

tree  newdjangoapp/

Output should be

newdjangoapp/
|-- manage.py
`-- mydjangoapp
    |-- __init__.py
    |-- settings.py
    |-- urls.py
    `-- wsgi.py

Now go inside newdjangoapp directory.

cd newdjangoapp

Now we need to migrate the database.

python manage.py migrate

The output should be:

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK

Create administrative user running following command.

python manage.py createsuperuser

NOTE: The above command can prompt you for Username, Password and Email Address for your user.
Testing the development server

Run development server using the following command.

python manage.py runserver

The output should be:

Performing system checks...

System check identified no issues (0 silenced).
December 28, 2018 - 17:00:23
Django version 2.1.4, using settings 'mydjangoapp.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.

NOTE: If you are using the virtual machine then you need to add your server IP address inside settings.py file.

Go to http://127.0.0.1:8000/ in your browser you will get the following page.
