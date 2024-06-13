# Django CRUD Template

## Step 1: Setup Virtual Environment and Install Packages

### Run the Following Commands

1. Upgrade `distro-info`:

    ```bash
    pip install --upgrade distro-info
    ```

2. Upgrade `pip`:

    ```bash
    pip3 install --upgrade pip==23.2.1
    ```

3. Install `virtualenv`:

    ```bash
    pip install virtualenv
    ```

4. Create a virtual environment named `djangoenv`:

    ```bash
    virtualenv djangoenv
    ```

5. Activate the virtual environment:

    ```bash
    source djangoenv/bin/activate
    ```

6. Install Django and `psycopg2-binary`:
    ```bash
    pip install Django psycopg2-binary
    ```

## Step 2: Configure Database Settings

### Update `settings.py`

Open `settings.py` and locate the `DATABASES` section. Replace the value of the `PASSWORD` key with the generated PostgreSQL password.

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

## Step 3: Generate and Run Migrations

### Generate Migration Scripts

Run the following command to generate migration scripts based on your models:

```bash
python3 manage.py makemigrations crud
```

### Apply Migrations

Run the following command to apply the migrations to your database:

```bash
python3 manage.py migrate
```
