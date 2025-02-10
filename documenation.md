"# Python Backend Stack Documentation

## 📌 Table of Contents:
1. [Environment Setup](#environment-setup)
2. [Using Docker and Docker-Compose](#using-docker-and-docker-compose)
3. [Technology Stack](#technology-stack)
4. [Linting Standards](#linting-standards)
5. [Dependency Management](#dependency-management)
6. [Latest Technologies](#latest-technologies)
7. [FastAPI](#fastapi)

---

## Environment Setup
(Details about installing dependencies and setting up the development environment) 
To set up an environment for building a Python backend, the typical stack might include frameworks like **Flask** or **Django** for the web server, and databases like **PostgreSQL** or **SQLite**. Here’s a step-by-step guide to help you get started:

### 1. **Install Python** 
   - Download and install the latest version of Python from [python.org](https://www.python.org/downloads/).
   - **Make sure to check the box** to add Python to the system PATH during installation.

### 2. **Create a Virtual Environment**
   It’s best to use a virtual environment to isolate dependencies for your project.

   - Open your terminal (or command prompt) and navigate to your project folder.
   - Run the following command to create a virtual environment:

     ```bash
     python -m venv backend_env
     ```

   - **Activate the virtual environment**:
     - **Windows**:
       ```bash
       backend_env\Scripts\activate
       ```
     - **Mac/Linux**:
       ```bash
       source backend_env/bin/activate
       ```

   - When activated, you should see `(backend_env)` before the prompt.

### 3. **Install Required Python Packages**
   Depending on the framework you want to use, you can install the following packages.

   #### Flask (for lightweight backend API)
   - Install **Flask**:
     ```bash
     pip install flask
     ```

   #### Django (for full-fledged backend)
   - Install **Django**:
     ```bash
     pip install django
     ```

   #### For Database Support:
   - **PostgreSQL**: You might need to install a package for connecting to PostgreSQL databases.
     ```bash
     pip install psycopg2
     ```
   - **SQLite**: SQLite is built into Python, so you don’t need to install anything extra.

   #### For API Documentation (Swagger or OpenAPI)
   - For **Flask**, you can use **Flasgger** to create API documentation.
     ```bash
     pip install flasgger
     ```
   - For **Django**, you can use **drf-yasg** to generate Swagger documentation for your Django REST APIs.
     ```bash
     pip install drf-yasg
     ```

### 4. **Setup Database (Optional)**
   - If you're using **PostgreSQL**, you need to have it installed locally. You can install it from [here](https://www.postgresql.org/download/).
   - **SQLite** is a lightweight option and doesn’t require installation; it’s built into Python.

   To connect to the database, you’ll set up your backend framework’s database connection (for Flask/Django). 

### 5. **Setup API Documentation (Optional)**
   If you want to generate automatic documentation for your APIs:

   #### **Flask** with Flasgger (for Swagger UI):
   - Add the following to your Flask app:
     ```python
     from flask import Flask
     from flasgger import Swagger

     app = Flask(__name__)
     swagger = Swagger(app)

     @app.route('/api', methods=['GET'])
     def api():
         """
         A simple API endpoint.
         ---
         responses:
           200:
             description: Returns 'Hello, World!'
         """
         return 'Hello, World!'

     if __name__ == '__main__':
         app.run(debug=True)
     ```

     When you visit `http://localhost:5000/apidocs/`, you'll get a Swagger UI with your API documentation.

   #### **Django** with DRF-YASG (for Swagger UI):
   - First, install Django REST Framework:
     ```bash
     pip install djangorestframework
     ```
   - Install `drf-yasg` for automatic Swagger UI:
     ```bash
     pip install drf-yasg
     ```
   - Then, configure it in your Django project’s `urls.py`:
     ```python
     from rest_framework import routers
     from drf_yasg.views import get_schema_view
     from drf_yasg import openapi
     
     schema_view = get_schema_view(
         openapi.Info(
             title="My API",
             default_version='v1',
             description="Test description",
             terms_of_service="https://www.google.com/policies/terms/",
             contact=openapi.Contact(email="contact@myapi.local"),
             license=openapi.License(name="BSD License"),
         ),
         public=True,
     )

     urlpatterns = [
         # Your API endpoints here
         path('swagger/', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui'),
     ]
     ```

     When you visit `http://localhost:8000/swagger/`, you’ll get your API documentation.

### 6. **Git for Version Control (Optional)**
   - Initialize Git for version control:
     ```bash
     git init
     ```
   - Create a `.gitignore` file to exclude unnecessary files (like virtual environment files) from version control.
     Example `.gitignore` for Python:
     ```
     __pycache__/
     *.pyc
     *.pyo
     *.pyd
     backend_env/
     ```

   - Commit your changes and push them to a repository (e.g., GitHub or GitLab):
     ```bash
     git add .
     git commit -m "Initial commit"
     git remote add origin <your-repository-url>
     git push -u origin master
     ```

### 7. **Run Your Application**
   - For **Flask**:
     ```bash
     python app.py
     ```
     This will run your Flask application, typically accessible at `http://localhost:5000`.

   - For **Django**:
     ```bash
     python manage.py runserver
     ```
     This will run your Django application, typically accessible at `http://localhost:8000`.

---

### Example Flask API with Documentation:

```python
from flask import Flask
from flasgger import Swagger

app = Flask(__name__)
swagger = Swagger(app)

@app.route('/hello', methods=['GET'])
def hello_world():
    """
    A simple API endpoint that returns a greeting.
    ---
    responses:
      200:
        description: A greeting message
        examples:
          message: 'Hello, World!'
    """
    return "Hello, World!"

if __name__ == "__main__":
    app.run(debug=True)

## Using Docker and Docker-Compose
(How to run the project using Docker and Docker-Compose)

## Technology Stack
(Overview of the tools and technologies used)

## Linting Standards
(Details about code formatting and linting tools like Flake8 and Black)

## Dependency Management
(How to handle libraries and manage dependencies)

## Latest Technologies
(Updates on new technologies and how they are utilized)

## FastAPI
(Details on using FastAPI for the project)Python Backend" 
