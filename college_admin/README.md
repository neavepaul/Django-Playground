# Django Admin Site

## Concepts Covered in the Template

### Django Admin Site

A built-in feature of the Django web framework that serves as an interface and allows authorized users to perform various management operations on the data stored in the application’s database.

### Superuser

A user account with administrative privileges that allows superusers to perform administrative tasks and manage the application’s data.

### Admin Class

A class that helps fine-tune the behavior, appearance, and functionality of models within the Django admin site.

### Inline Class

Allows you to include related model instances in the same page/form as the parent model, instead of switching between different forms or screens.

## Step 1: Setup Environment and Install Packages

### Install Required Packages

Run the following commands:

```bash
pip install --upgrade distro-info
pip3 install --upgrade pip==23.2.1
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate
```

### Install Django

Run the following command to install Django:

```bash
pip install Django
```

## Step 2: Perform Migrations

### Generate Migration Scripts

Run the following command to generate migration scripts:

```bash
python3 manage.py makemigrations
```

### Apply Migrations

Run the following command to apply the migrations to your database:

```bash
python3 manage.py migrate
```

## Step 3: Create a Superuser

Run the following command to create a superuser with administrative privileges:

```bash
python3 manage.py createsuperuser
```

## Step 4: Register Models with Admin site

Regiter the models in `adminsite/models.py`

## Step 5: Run
