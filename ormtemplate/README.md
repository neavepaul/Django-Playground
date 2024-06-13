# Standalone Django ORM App

## Prerequisite

### Set the password in `settings.py`

Example:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_database_name',
        'USER': 'your_database_user',
        'PASSWORD': 'your_generated_password',
        'HOST': 'localhost',
        'PORT': '5050',
    }
}
```

## Step 1: Define a Simple Test Model

Open the `orm/models.py` file and copy and paste the following code snippet to define a simple Test model:

```python
from django.db import models

# Test model
class Test(models.Model):
    name = models.CharField(max_length=30)
```

## Step 2: Generate the Test Table

Next, we can ask the `ormtemplate` app to generate the Test table by running migration command-lines.

### Change Directory to `ormtemplate`

```sh
cd ormtemplate
```

Your current Theia folder should now be `/home/project/ormtemplate` as shown in the terminal.

### Set Up a Virtual Environment

```sh
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate
```

### Install Required Packages

```sh
pip install django psycopg2-binary
```

### Generate Migration Scripts for the Standalone App

```sh
python3 manage.py makemigrations standalone
```

You should see migration scripts generated for your Test model:

```
Migrations for 'standalone':
  standalone/migrations/0001_initial.py - Create model Test
```

**Note:** If you see errors like:

```
django.db.utils.OperationalError: FATAL: password authentication failed for user "postgres"
```

Please re-run `start_postgres` to reset the PostgreSQL server and use the new password in `settings.py`.

### Run Migration

```sh
python3 manage.py migrate
```

## Step 3: Write Testing Code

Next, you can write some Python testing code in a Python script file to test your model.

### Create a New Test File

Click the `ormtemplate` folder and create a new file called `test.py`.

### Add the Following Code Snippet to `test.py`

```python
# Django specific settings
import inspect
import os
os.environ.setdefault("DJANGO_SETTINGS_MODULE", "settings")
from django.db import connection

# Ensure settings are read
from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()

# Your application specific imports
from standalone.models import Test

# Delete all data
def clean_data():
    Test.objects.all().delete()

# Test Django Model Setup
def test_setup():
    try:
        clean_data()
        test = Test(name="name")
        test.save()  # Check test table is not empty
        assert Test.objects.count() > 0
        print("Django Model setup completed.")
    except AssertionError as exception:
        print("Django Model setup failed with error: ")
        raise(exception)
    except:
        print("Unexpected error")

test_setup()
```

The above code snippet first cleans the database and then inserts a test object. Then it checks if the test object was inserted correctly.

### Run the Test Script

In the terminal, run the `test.py`:

```sh
python3 test.py
```

You should see:

```
Django Model setup completed.
```
