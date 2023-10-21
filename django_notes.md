# DJANGO WEB FRAMEWORK

Can connect to a dedicated frontend like react through use of an API. On the back-end features like email-notifications, data analysis tools, admin dashboards and development tools for online marketplaces and booking system are available. 

Django can be used to make AI/ML available through APIs, RPCs and WebSockets.

Django is also often used for scalable web applications like Instagram. It is also well suited for cloud storage applications because it supports asynchronous views (allows to run multiple services simultaneously). 

# Projects and Apps

## Project
Represents the entire web application

`django-admin startproject my_site .`

``` bash
my_site/
	manage.py
	my_site/
		__init__.py
		settings.py
		urls.py
		wsgi.py
	...
```

## Apps

App is a submodule of a project. Typically used to implement functionality for a specific purpose. Apps can be selfcontained, meaning they do not rely on other apps to function. Can be used and releused in different projects. 

`python manage.py startapp feed`
`python manage.py startapp comments`
`python manage.py startapp profile`

``` bash
my_site/
	manage.py
	feed/
	comments/
	profile/
	my_site/
```

In order for apps to work with a project they have to be added to the *INSTALLED_APPS* setting in my_site/my_site/settings.py.

Django Applications usually contain **Models, Views, Templates, Template Tags, Static Files, URLs and Middleware**.

## Administration

Django manages database operations with the ORM technique. Migration refers to generating a database table that matches the model declared in apps. Whenever a new model is declared the following should be run.

`python manage.py makemigrations`

The *migrate* command synchronizes the currently declared models with the database state. 

`python manage.py migrate`

The *runserver* command starts a **development server** on the local machine with IP 127.0.0.1 and port 8000.

`python manage.py runserver`

If some quick interactive operations need to be performed an interactive Python shell can be started using the *shell* command.

`python manage.py shell`

To create a new project there are two possible ways. To create a new folder with the manage.py and the main project app inside the following can be used.

`django-admin startproject project_name`

If the parent folder is not needed and you want the manage.py and the project main app should be in the current directory the following can be done.

`django-admin startproject project_name .`

The inner folder with the name *project_name* is a Python package. For a folder to be considered a package it **must have** a file called **__init__.py**

To create an app inside a project the following command is used.

`python manage.py startapp app_name`

``` bash
demoproject/
	db.sqlite3
	manage.py
	demoapp/
		admin.py
		apps.py
		models.py
		tests.py
		views.py
		__init__.py
		migrations/
			__init__.py
	demoproject/
		asgi.py
		settings.py
		urls.py
		wsgi.py
		__init__.py
```

## Views

A view in django is a function that is called when Django's URL dispatcher identifies the client's request URL and matches it with a URL pattern defined in the *urls.py* file.

## Three-tier architecture

* Presentation tier - User interface usually React/Angular. Communticates through API with backend
* Application tier - Ties Presentation and Data tier together.
* Data tier - Usually Database

## MVT - Model, View, Template pattern

Most web frameworks use the MVC (Model, View, Controller) pattern. A pattern where the controller intercepts requests and coorinates a response with the model and view. The model is handling all business logig and the view handles representation. 

In **MVT** the Model also coordinates data representation. The view is what does the logic processing. The template is the representation. In the *urls.py* file, urls are mapped to views. When a request arrives the dispatcher tries to find the corresponding view.


The process of mapping a URL to a view function is called **routing**.

A mapping can be createn in a *url.py* file.

The first parameter to the path is a url pattern. The second one specifies the view function that shall be called for this url.

``` python
from django.urls import path
from . import views

urlpatterns = [
	path('', views.home)
]
```

When a new request arrives the *urls.py* file at the project level is checked first. To delegate the routing to the *urls.py* file inside an app (at app level) the *include()* function has to be utilized. 

``` python
from django.urls import path, include

urlpatters = [
	path('admin/', admin.site.urls),
	path('', include('myapp.urls'))
] 
```

### Class based vs Function based views

**Function based**

``` python
from django.shortcuts import render

def myview(request):
	if request.method == 'GET':
		val = request.GET['key']
		# Anything GET request related
		
	if request.method == 'POST':
		val = request.POST['key']
		# Anything post request related
	
	return render(request, 'mytemplate.html')
```

**Class based**

``` python
from django.views import View

class MyView(View):
	def get(self, request):
		# Logic to process GET request
		return HttpResponse('response to GET request')
	
	def post(self, request):
		# Logic to process POST request
		return HttpResponse('response to POST request')
		
```

There are several view classes that provide typical functionality. They can be used from *django.views.generic*. Some of them are *TemplateView, CreateView, ListView, DetailView and UpdateView*. They can be subclassed and their *model* and *template_name* properties have to be set. 

## HTTP

### HTTP Request

Consists of *method, path, version and headers*. The method describes the type of action the client wants to perform. The headers contain mor information about the request and the client making the request. 

In django a **HttpRequest** object is passed as the first parameter to a view function. *request.method* gives a string representaion of the method used. *request.GET and request.POST* returns a dictionary-like object containing all the GET or POST parametes. *request.COOKIES* is a dictionary of string keys and values too. If the user uploads a file with a multipart form it is available through *request.FILES*. With *request.user* information about the current user can be obtained. It is an instance of the *django.contrib.auth.models.User* class. If the user is not authorized/logged in yet it returns *AnonymousUser*. To check if a POST or GET request's parameter dictionary contains a certain value *request.has_key()* can be used. 

### HTTP Response

Format similar to request. Following header response optionally contains a body that contains the response content. (i.e. html document, image file). Status code in the header gives information if was successful.

**HttpResponse** objects also have attributes. *status_code*

## URLS

### Scheme

A URL begins with a Scheme/Protocol. This is the *http:// or https://* part of the url.

### Subdomain

The subdomain is located before the domain. The most common subdomain is *www*.

### domain

There are second-level and top-level domain. The second levele domain for little lemon is *littlelemon* as in *https://www.littlelemon.com*. The top level domain is used to reference a country or category of the organization. Examples for top level domains are *.com, .de, .org* and so on. 

### Query String

Begins with the questionmark '?' symbol and is placed after the url path. Contains paramters in key value pairs and can contain multiple parameters separated by the apersand '&' symbol.

`https://www.littlelemon.com/menu/?year=2022&menu=summer`

## Path parameters

Path parameters can be mapped in django. If the url is *http://localhost:8000/getuser/John/1/* the view function shall retrieve the user *John* and the id *1*.

This can be done with the following path to view mapping. The parameter names in the *path()* function **have to** match the parameters in the view function.

``` python
path('getuser/<name>/<id>/', views.pathview, name='pathview')

def pathview(request, name, id):
	return HttpResponse("Name: {} UserID: {}".format(name, id))
```

By default the parametes from the url will be cast to string. In this example both *\<name>* and *\<id>* will be cast to string. If need be it can also be cast to int for example. This could be done like so: *\<int:id>*.

The same could also be achieved with query strings like so.

`http://localhost:8000/getuser/?name=John&id=1`
The key-value pairs in query strings like *?name=John&id=1* will be added to the request.GET property. So they can be retrieved with *request.GET['name']* and *request.GET['id']*

Html forms send their data in it's action attribute using the POST method. Sending data with POST is more secure because the data is not visible in the URL. Post requests need a **{% csrf_token %}**. This prevents cross-site forgery attacks. 

* [Django Writing Views](https://docs.djangoproject.com/en/4.1/topics/http/views/)
* [Django Class Based Views](https://docs.djangoproject.com/en/4.1/topics/class-based-views/)
* [Django render() function](https://docs.djangoproject.com/en/4.1/topics/http/shortcuts/#render)
* [Getting Query Parameters](https://docs.djangoproject.com/en/4.1/topics/http/urls/#path-converters)