Flask is a lightweight [[Python]] web development framework used to create simple applications. Flask uses a similar approach to [[React#JSX|JSX]] where strings are used to return HTML. This is handled through decorators which handle application routing and requests. Apps are created with the flask command.
```python
from flask import Flask
app = Flask(__name__)
```
This creates a Flask object which is bound to the name in the brackets. This name is usually specified as the file's name.

# Routing
Routing is handled through the route decorator. This decorator specifies what function will be ran when a page's URL is called. This follows the structure:
```python
@app.route('/')
def page():
	return "<div>Hello World</div>"
```
Routes can have variable sections within the URL by placing a `<var>` into the route. This enables a unique route which depends on a variable. A **converter** can be used within the route to specify a type. This variable routing uses:
```python
@app.route('/<int:user>')
def userPage(user):
	return f"<div>escape(user)</div>"
```

## URL Building
URL building allows for a URL to a function to be gotten without the need to specific an exact relative position. This allows URLs to be retrieved anywhere within the document. This is done by using the name of the function as a string argument within the `url_for('...')` function.

# HTML Escaping
HTML escaping is the process of leaving the HTML syntax when returning a value. This is done as to avoid injection attacks where HTML syntax is used as an input and results in a potentially dangerous output. To stop this flask provides the `escape()` function which can be used together will a formatted string to display text from Python variables.
