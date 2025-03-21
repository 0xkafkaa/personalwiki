# Flask

- All flask applications must create an application instance.
- The web server passes all the requests from the clients to this object for handling, using a protocol called /Web Server Gateway Interface/.
- The application instance is an object of class Flask. It takes the name of the main module or package of the application as the argument.

```python
  from flask import Flask
  app = Flask(__name__)
```

## Route and View functions

- The association between a URL and the function that handles it is called a /route/.

```python
  @app.route('/')
  def index():
      return '<h1>Hello, World!</h1>'
```

- The return value of the function is called the /response/.
- The function index() is called a /view function/.
- Dynamic component in flask

```python
  @app.route('user/<name>')
  def user(name):
      return '<h1>Hello, %s!</h1>' % name
```

- Dynamic component in routes are strings by default but can also be defined with a type. Example: '/user/<int:id>' - would match only URLs that have an integer in the id dynamic segment.
- Flask supports int, float, and path for routes. The path type also represents a string but does not consider slashes as separators and instead considers them part of the dynamic component.

## The Request-Response Cycle

- When Flask receives a request from a client, it needs to make a few objects available to the view function that will handle it. A good example is a request object.
- The obvious way in which Flask could give a view function access to the request object is by sending it as an argument, but that would require every single view function in the application to have an extra argument. Things get more complicated if you consider that the request object is not the only object that the view functions might need to access to fulfill a request.
- Flask uses /contexts/ to temporarily make certain objects globally accessible to avoid cluttering view functions with a bunch of arguments.

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def index():
    return '<p>%s</p>' %request.headers

if __name__ == '__main__':
    app.run(debug=True)
```

- Note how in the above view function request is used as if it was a global variable.
- In reality, request cannot be global variable if you consider that in a multithreaded server the threads are working on different requests from different clients at the same time, so each thread need to see a different object in request.
- Contexts enables Flask to make certain variables globally accessible to a thread without interfering with the other threads.
- A thread is the smallest sequence of instructions that can be managed independently. It is common for a process to have multiple active threads, sometimes sharing resources such as memory or file handles. Multithreaded web servers start a pool of threads and select a thread from the pool to handle each incoming request.
- There are two types of context in Flask: application context and the request context.

| Variable Name | Context | Description                                          |
| ------------- | ------- | ---------------------------------------------------- |
| current app   | App Con | The application instance for the active application  |
| g             | App Con | An object used as temp storage for each request      |
| request       | Req Con | Contents of a HTTP request sent by the client as obj |
| session       | Req Con | Dict, used to store values used between requests     |

## Request Dispatching

- When the application receives a request from the client, it needs to know which view function to be invoked.
- Flask looks up the URL given in the request in the application's URL map, which contains a mapping of URLs to the view function that handle them.

```python
>>> app.url_map
Map([<Rule '/static/<filename>' (GET, HEAD, OPTIONS) -> static>,
 <Rule '/' (GET, HEAD, OPTIONS) -> index>,
 <Rule '/user/<name>' (GET, HEAD, OPTIONS) -> user>,
 <Rule '/user/<userId>' (GET, HEAD, OPTIONS) -> userId>])
```

- Head, Options and Get are the request methods that are handled by the route.

## Request Hooks

- Sometimes it is useful to execute code before or after each request is processed, eg: connection to database.
- Instead of duplicating the code in every view function, flask offers an option to register common functions to be invoked before or after a request is dispatched to a view function.
- Request hooks are implemented as decorators.

| Request Hooks        | Used                                                                                 |
| -------------------- | ------------------------------------------------------------------------------------ |
| before first request | Register a function to run before the first req is handled                           |
| before request       | Register a function to run before each request                                       |
| after request        | Register a function to run after each request, if no unhandled exceptions occurred   |
| teardown request     | Register a function to run after each request, even if unhandled exceptions occurred |

## Responses

- When Flask invokes a view function, it expects its return values to be the response of the request. In most cases, its just a string.
- The HTTP protocol requires more than a string as a response to the request such as a status code.
- By default, 200 is sent by Flask. To add something else pass it as a second return value after the response text.

```python
  @app.route('/')
  def index():
      return '<h1>Bad request</h1>', 400
```

- It can also take a third argument, a dictionary of headers that are added to the HTTP response.
- Instead of returning one, two, or three values as a tuple, Flask view functions have the option of returning a Response object.
- The /make response()/ function takes one, two, or three arguments and returns as a Response object.

```python
  from flask import make_response

  @app.route('/')
  def index():
      response = make_response('<h1>This document carries a cookie!</h1>')
      response.set_cookie('answer', '42')
      return response
```

- There is another special type of response called a redirect for redirecting.

```python
  @app.route('/')
  def index():
      return redirect('https://thekafkaa.online')
```

## Templates

- A template is a file that contains the text of a response, with placeholder variables for the dynamic parts that will be known only in the context of a request. The process that replaces the variables with actual values and returns a final response string is called rendering.
- Flask uses Jinja2 for rendering.

```python
  from flask import Flask, render_template
  app = Flask(__name__)

  @app.route('/')
  def index():
      return render_template('index.html') // templates/index.html

  @add.route('/user/<name>')
  def user(name):
      return render_template('user.html', name = name)
```

- Jinja2 recognizes variables of any type, even complex types such as lists, dictionaries and objects.

```html
<p>A value from a dictionary: {{ mydict['key'] }}.</p>
<p>A value from a list: {{ mylist[3] }}.</p>
<p>A value from a list with a variable index: {{ mylist[myintvar] }}.</p>
<p>A value from an object's method: {{ myobj.somemethod() }}.</p>
```

- Variables can be modified with filters which are added after the variable name with a pipe as separator.

```html
<p>Hello, {{ name|capitalize }}.</p>
```

- Jinja also offers control structures. Following is how conditionals are done.

```html
{% if user %} Hello, {{ user }}! {% else %} Hello, Stranger! {% endif %}
```

- Following is a demonstration of a for loop.

```html
<ul>
  {% for comment in comments %}
  <li>{{ comment }}</li>
  {% endfor %}
</ul>
```

- Jinja also supports macros, which are similar to python code.

```html
{% macros render_comment(comment) %}
<li>{{ comment }}</li>
{% endmacros %}

<ul>
  {% for comment in comments %} {{ render_comment(comment) }} {% endfor %}
</ul>
```

- To make macros more reusable, they can be stored in a standalone file that is then imported from all the templates that need them.

```html
{% import 'macros.html' as macros %}

<ul>
  {% for comment in comments %} {{ macros.render_comment(comment) }} {% endfor
  %}
</ul>
```

- Portions of template code that need to be repeated in several places can be stored in a separate file and included from all the templates to avoid repetition.

```html
{% include 'common.html' %}
```

- Jinja also provides template inheritance for powerful reuse, first a base template is created with the name base.html.

```html
<html>
  <head>
    {% block head %}
    <title>{% block title %}{% endblock %} - My application</title>
    {% endblock %}
  </head>
  <body>
    {% block body %} {% endblock %}
  </body>
</html>
```

```html
{% extends "base.html" %} {% block title %}Index{% endblock %} {% block head %}
{{ super() }} {% endblock %} {% blockbody %}
<h1>Hello, World!</h1>
{% endblock %}
```

## Links

- Any application that has more than one route will invariably need to include links that connect the different pages, such as in a navigation bar.
- Writing the URLs as links directly in the template is trivial for simple routes, but for dynamic routes with variable portions it can get more complicated to build the URLs right in the template.
- To avoid these problems, Flask provides the urlfor() helper function, which generates URLs from the information stored in the application's URL map.

```python
  @app.route('/user/<name>')
  def user():
      print(url_for('user', name=name)
```

- Using static file for a file URL.

```html
{% block head %} {{ super() }}
<link
  rel="shortcut icon"
  href="{{ url_for('static', filename = 'favicon.ico') }}"
  type="image/x-icon"
/>
<link
  rel="icon"
  href="{{ url_for('static', filename = 'favicon.ico') }}"
  type="image/x-icon"
/>
{% endblock %}
```

## Web Forms

- Though forms in Flask can be handled with the help of the request object, it becomes tedious and repetitive to generate HTML code for forms and the validations of the submitted form data. Hence Flask-WTF extension is used.
- Cross Site Request Forgery attack occurs when a malicious website sends requests to a different website on which the victim is logged in. By default, Flask-WTF protects forms against CSRF.
- To implement CSRF, WTF needs the application to configure an encryption key. Flask then uses this key to generate encrypted tokens that are used to verify the authenticity of requests with form data.

```python
  app = Flask(__name__)
  app.config['SECRET_KEY'] = 'hard to guess string'
```

- app.config dictionary is a general-purpose place to store configuration variables used by the framework, extensions, or the application itself.
- When using Flask-WTF, each form is represented by a class that inherits from class Form.

```python
  from flask_wtf import Form
  from wtforms import StringField, SubmitField
  from wtforms.validators import Required

  class GetNameForm(Form):
      name = StringField('What is your name?', validators=[Required()])
      submit = SubmitField('Submit')
```
