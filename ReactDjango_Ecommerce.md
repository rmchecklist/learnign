# Prerequisite:

1. Visual Studio code
    Extensions:
      Prettier
      Auto Reanme tag
      Bracket pair colorizer
      ES7
      
      
2. Create React app - FrontEnd

```
npx create-react-app frontend
```

3. Start the app

```
cd frontend
npm start
```

Shortcuts

rafce - Create ES6 functional compoonents 
imp -> import module from 'module
imd -> destructuring import 


# CSS 
    - React bootstrap [https://react-bootstrap.github.io/]
    - Bootwatch free themes [https://bootswatch.com/]
    
# Install bootstarp

```
npm install react-bootstrap
```

# Install react router and react router bootstrap

```
npm install react-router-dom react-router-bootstrap
```

# Serving and fetching data from Django
      
1. Create a vitural env
```
virtualenv myenv [On Command prompt]
```

2. Activate myenv

```
myenv\scripts\activate
```

3.Find all installed lib under myenv -> pip list

4. Install Django

```
pip install Django
```

5. Create django admin project

```
django-admin startproject backend
```

6. Start server

```
python manage.py runserver
```

7. Create App

```
python manage.py startapp base
```

under base app:

views.py - view logic
models.py - model logic

Register our apps 

 - add entry into settings.py INSTALLED_APPS

In order to use urls, we need to create a urls.py under base apps

Install django rest framework [https://www.django-rest-framework.org/]

```
pip install djangorestframework
```
Add these imports into views.py to use django rest framework

from rest_framework.decorators import api_view
from rest_framework.response import Response


# Install axios on React app

```
npm install axios
```

# Install django cors to avoid error when accessing api [https://pypi.org/project/django-cors-headers/]


# React frontend 

 - Add proxy on packages.json

```
"proxy": "http://localhost:8000",
```

Database model design [drawsql.app]

python apply migration/all pending changes

```
python manage.py migrate

```

create admin user

```
python manage.py createsuperuser


```

Register models and make migrations (to create a script under migrations folder), in order to migrate this changes to DB then we should run migrate command

```
python manage.py makemigrations

python manage.py migrate
```

In order to view these changes in admin panel, then we should register them in admin.py

```
from .models import Product

admin.site.register(Product)
```

# DB model

![image](https://user-images.githubusercontent.com/5713791/122660073-24cbfc80-d14c-11eb-9abb-6172f964a659.png)


Using ImageField, we need to install pillow

```
pip install pillow
```


