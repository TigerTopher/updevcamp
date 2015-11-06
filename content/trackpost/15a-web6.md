# flash-flask: get started with flask

```
date = "2015-02-10T02:11:02+08:00"
title = "Learn Flask"
authors = ["toph", "carl"]
```

In this guide, we’ll cover installing Flask and using it for the first time. Flask is a back-end framework that we will be using alongside HTML and CSS. Contrary to to the front end, which is basically what the client sees, the back end consists of the internal mechanisms of a website, which handles stuff like input from the client.

After completing this tutorial, you will be able to:
* Set-up Flask in your machines
* Create a backend for your web app
* Implement CRUD operations in Flask

This guide is based directly from the awesome and concise guides provided by [Flask Documentation](http://flask.pocoo.org/docs/0.10/) and [Miguel Grinberg](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). These guides have been merged and modified for UP CSI Devcamp 2015.

```
Guide Outline:
Foreword
I. Installing Flask
  A. Linux Guide
  B. Windows Guide  
II. Hello World in Flask
III. Templates
  A. Control Statements in Templates
  B. Loops in Templates
  C. Template Inheritance
```

## Foreword: Why Flask?
Why flask? Why study a microframework if I could just study real `frameworks` such as Django? Why should I waste my time learning Flask?

A short, simple answer is that many developers use frameworks such as RoR and Django to develop sites whose functionalities doesn't really need to use such sophisticated, complicated frameworks. Why not simplify things o'rayt? Also, the learning curve for complete frameworks are way-way steeper than microframeworks. Surely, Flask is a suitable stepping stone for first-time non-framework developers.

Please read this 2-minute article before starting with Flask. [Check out this link.](http://flask.pocoo.org/docs/0.10/foreword/#what-does-micro-mean):


## I. Installing Flask

To install Flask, we would be needing to 3 things:
1. Python 3 - a widely used general-purpose, high-level programming language.

2. pip - a tool that's used to manage packages written in Python

3. Virtual Environment (Virtualenv)- allows us to create Python environments that are isolated from one another. We will now create our own virtual environment for a simple web app and install Flask in it.

To learn more about one of the best programming language, check out [Python's Website](https://www.python.org/).

For a  thorough beginner-level explanation for pip and Virtualenv, you could check out this awesome [article](http://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/).

For Unix-based Operating Systems
---
On Ubuntu, Linux Mint, or other distributions that have `apt-get`, run the command:
```
sudo apt-get install python3.4-venv
```
This will allow us to create Python environments that are isolated from one another.

Type these on the command line in order to make the virtual environment:
```
mkdir microblog
cd microblog
python3 -m venv flask
```
(note: the name microblog can be substituted with anything)

To install Flask and other stuff, copy this to the command line:
```
flask/bin/pip install flask
```

** THIS IS FOLLOWING IS JUST OPTIONAL IN THE CURRENT SCOPE OF THIS TUTORIAL**
```
flask/bin/pip install flask-login
flask/bin/pip install flask-openid
flask/bin/pip install flask-mail
flask/bin/pip install flask-sqlalchemy
flask/bin/pip install sqlalchemy-migrate
flask/bin/pip install flask-whooshalchemy
flask/bin/pip install flask-wtf
flask/bin/pip install flask-babel
flask/bin/pip install guess_language
flask/bin/pip install flipflop
flask/bin/pip install coverage
```

And we're done! Let's proceed to our First Web App in Flask!

For Windows
===
One main difference between Windows from Unix-based OS is that you need to edit your system environment variables in order to run python in the command prompt.

Luckily, both the (1) system environment variables can already be updated and (2) pip can already be installed during the Python 3.4 installation. In order to accomplish that, you can do the following:

1.) Quick-Guide: Python 3.4 Installation
    For a thorough guide, you can click this [link](google.com).

  a. Download python 3.4 [here](https://www.python.org/downloads/).

  b. Run (as administator) the downloaded exe file.

  c. Select `Customize Installation`

  d. In Optional Feature, tick the checkbox `pip`. Click `next`.

  e. In Advanced Options, tick the checkbox `Add Python to environment variables`. Click `Install`

2.) Pip Installation

  If you did Step 1, then you don't need to do this.

  Else if you have installed Python before but didn't decide to install pip, then do the following:

  Enter the following in our command line:
```
python -m easy_install pip
```
  The command above makes use of easy_install, a primitive package manager (same as pip) that is installed automatically when you install python.

  **Note: If you renamed 'python' to 'python3' in your 'Python3' folder in order to accommodate to versions of Python, then you must rename all the commands with the keyword 'python' to 'python3'. Example: `python3 -m easy install pip`**

3.) Installing Virtualenv

  In your command line, enter:
```
python -m pip install virtualenv
```

4.) Setup application folder

  Type these on the command line in order to make the virtual environment:
```
mkdir microblog
cd microblog
virtualenv venv
```
  (note: the name microblog can be substituted with anything)

  Now, whenever you want to work on a project, you only have to activate the corresponding environment.
```
$ venv\scripts\activate
```
  Either way, you should now be using your virtualenv (notice how the prompt of your shell has changed to show the active environment).
  Now you can just enter the following command to get Flask activated in your virtualenv:
```
(venv) C:\Users\Cheverloo\my_app> pip install Flask
```

  **THE FOLLOWING IS JUST OPTIONAL IN THE CURRENT SCOPE OF THIS TUTORIAL**  

Next, do this...
```
(venv) C:\Users\Cheverloo\my_app> pip install flask-login
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-openid
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-mail
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-sqlalchemy
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install sqlalchemy-migrate
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-whooshalchemy
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-wtf
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flask-babel
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install guess_language
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install flipflop
(venv) C:\Users\Cheverloo\my_app> $ venv\Scripts\pip install coverage
```

If you are having error message `Fatal error in launcher: Unable to create process using '"' `, try this:
```
(venv) C:\Users\Cheverloo\my_app> python -m pip install Flask
```

Next, do this...
```
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-login
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-openid
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-mail
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-sqlalchemy
(venv) C:\Users\Cheverloo\my_app> python -m pip install sqlalchemy-migrate
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-whooshalchemy
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-wtf
(venv) C:\Users\Cheverloo\my_app> python -m pip install flask-babel
(venv) C:\Users\Cheverloo\my_app> python -m pip install guess_language
(venv) C:\Users\Cheverloo\my_app> python -m pip install flipflop
(venv) C:\Users\Cheverloo\my_app> python -m pip install coverage
```


These commands will download and install all the packages that we will use for our application.

And we're done! Let's proceed to our First Web App in Flask!

## II. "Hello World" in Flask!

We now have a venv sub-folder inside your microblog folder that is populated with a Python interpreter and the Flask framework and extensions that we will use for this application.

`cd` to the `microblog` folder. We will create the basic folder structure for our application:

```
$ mkdir app
$ mkdir app/static
$ mkdir app/templates
$ mkdir tmp
```

**WHAT ARE THESE FOLDERS**

The `app` folder will be where we will put our application package.
The `static` sub-folder is where we will store static files like images, javascripts, and cascading style sheets.
The `templates` sub-folder is obviously where our templates will go.

Let's start by creating a simple init script for our `app` package (`file app/__init__.py`):

```
from flask import Flask

app = Flask(__name__)
from app import views
```

The script above simply creates the application object (of class Flask) and then imports the `views` module, which we haven't written yet. Do not confuse `app` the variable (which gets assigned the `Flask` instance) with `app` the package (from which we import the `views` module).

If you are wondering why the import statement is at the end and not at the beginning of the script as it is always done, the reason is to avoid circular references, because you are going to see that the views module needs to import the app variable defined in this script. Putting the import at the end avoids the circular import error.

**WHAT ARE VIEWS?**

The views are the handlers that respond to requests from web browsers or other clients. In Flask handlers are written as Python functions. Each view function is mapped to one or more request URLs.

Now let's write our first view function (file `app/views.py`):

```
from app import app

@app.route('/')
@app.route('/index')
def index():
    return "Hello, World!"
```

This `view` is actually pretty simple, it just returns a string, to be displayed on the client's web browser. The two `route` decorators above the function create the mappings from URLs `/` and `/index` to this function.

You might want to check out this [site to learn more about Python Decorators](https://realpython.com/blog/python/primer-on-python-decorators/)

The final step to have a fully working web application is to create a script that starts up the development web server with our application. Let's call this script `run.py`, and put it in the root folder:

```
#!flask/bin/python
from app import app
app.run(debug=True)
```

The script simply imports the app variable from our app package and invokes its run method to start the server. Remember that the app variable holds the Flask instance that we created it above.

Before we start the app, let's verify if our directory is correct. It must look like this (except instead of my_app it would be microblog):

![Directory Image](https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-xlf1/v/t34.0-12/12177706_1213462125337486_431659876_n.jpg?oh=b28483a4a964e826dd2043a24ae9ccec&oe=562F6F82&__gda__=1446031431_1b570c98a7ae22341ffe082c80def9c0)


**Mistake in the picture: That must be `templates` not template :)**

**Starting the App**

To start the app you just run this script. On OS X, Linux and Cygwin you have to indicate that this is an executable file before you can run it:

```
$ chmod a+x run.py
```


Then the script can simply be executed as follows:
```
./run.py
```

On Windows the process is a bit different. There is no need to indicate the file is executable. Instead you have to run the script as an argument to the Python interpreter from the virtual environment:

```
$ venv\Scripts\python run.py
```

After the server initializes it will listen on port 5000 waiting for connections. Now open up your web browser and enter the following URL in the address field:

```
http://localhost:5000
```

Alternatively you can use the following URL:

```
http://localhost:5000/index
```

Do you see the route mappings in action? The first URL maps to /, while the second maps to /index. Both routes are associated with our view function, so they produce the same result. If you enter any other URL you will get an error, since only these two have been defined.

When you are done playing with the server you can just hit Ctrl-C to stop it.

## III. Templates

We have made our webApp running. Now let's try to expand it!

Let's try to combine what we've learned in our previous DevCamp session/s: HTML and Python.

Copy the following in your `views.py` file:
```

from app import app

@app.route('/')
@app.route('/index')
def index():
    user = {'nickname': 'Toph'}
    return '''
<html>
    <head>
        <title>Home Page</title>
    </head>
    <body>
        <h1>Hello, ''' + user['nickname'] + '''! Why you so pogi?<h1>
    </body>
</html>
'''

```
So what's happening?
First, look at the line `user = {'nickname': 'Toph'}`. Here we are creating a variable `user` which is a data structure in Python called a dictionary. Using the key `nickname`, we can access the value `Toph`. We can clearly see that in this line:

`<h1>Hello, ''' + user['nickname'] + '''! Why you so pogi?<h1>`

So what are the `'''`s for? Well, it's an opening and closing tag for our string (this is in Python). So what's happening is that we are returning an html code represented in the concatenation of the three strings.

You should see something like this:
![SomethinLikeThis](https://scontent-hkg3-1.xx.fbcdn.net/hphotos-xpa1/v/t34.0-12/12179844_1214551965228502_1186999711_n.jpg?oh=1a8ea1c91c74a332edd886450dce86da&oe=56331D34)

But. But. But. This is HIDEOUS! It works but this is just fugly. Imagine if you have a more complex HTML code. Just... NO!

Consider how complex the code will become if you have to return a large and complex HTML page with lots of dynamic content. And what if you need to change the layout of your web site in a large app that has dozens of views, each returning HTML directly? This is clearly not a scalable option. - Grinberg

**TEMPLATES TO THE RESCUE SWOOOOOOSH**


To solve this, let's try to separate the logic of our application from its layout. This separation is actually common among frameworks. (If you have time, you might want to read about the design pattern [Model-View-Controller](http://c2.com/cgi/wiki?ModelViewController). This is widely implemented in the industry) Templates help implement this separation.

Let's create our first template (file: app/templates/index.html):
```
<html>
  <head>
    <title>{{ title }} - microblog</title>
  </head>
  <body>
      <h1>Hello, {{ user.nickname }}!</h1>
  </body>
</html>
```

As you see above, we just wrote a mostly standard HTML page, with the only difference that there are some placeholders for the dynamic content enclosed in {{ ... }} sections.

Now let's see how we use this template from our view function (file app/views.py):

```
from flask import render_template
from app import app

@app.route('/')
@app.route('/index')
def index():
    user = {'nickname': 'Toph'}  # Awesome Guy
    return render_template('index.html',
                           title='Home',
                           user=user)
```

Try the application at this point to see how the template works. Once you have the rendered page in your browser you may want to view the source HTML and compare it against the original template.

To render the template we had to import a new function from the Flask framework called `render_template`. This function takes a template filename and a variable list of template arguments and returns the rendered template, with all the arguments replaced.

Under the covers, the `render_template` function invokes the Jinja2 templating engine that is part of the Flask framework. Jinja2 substitutes `{{...}}` blocks with the corresponding values provided as template arguments.

You might want to check out [Jinja](http://jinja.pocoo.org/), a full featured template engine for Python.

### Control Statements in Templates

Remember control structures? Let's try to apply those `if`s and `else`s!
The Jinja2 templates support control statements, given inside {%...%} blocks. Let's add an if statement to our template (file app/templates/index.html):

```
<html>
  <head>
    {% if title %}
    <title>{{ title }} - microblog</title>
    {% else %}
    <title>Welcome to microblog</title>
    {% endif %}
  </head>
  <body>
      <h1>Hello, {{ user.nickname }}!</h1>
  </body>
</html>
```

Here our template is a little smarter. If the variable title has been defined (there's an assigned value), then we print it. If not, we just display `Welcome to microblog`. Try to remove the title argument in the render_template call of our view function to see how the conditional statement works.


### Loops in Templates

We can also have loops in our template. Let's make an array of "messages" in `views.py` and then using a for loop in our template to show them one by one.


(file app/views.py)

```
from flask import render_template
from app import app

@app.route('/')
@app.route('/index')
def index():
    user = {'nickname': 'Carl'}
    posts = [
                {
                    'author': {'nickname': 'John'},
                    'body': 'Lorem ipsum dolor sit amet'
                },
                {
                    'author': {'nickname': 'Carl'},
                    'body': 'insert random message here'
                },
                {
                    'author': {'nickname': 'Person1'},
                    'body': 'I like turtles'
                },
                {
                    'author': {'nickname': 'John'},
                    'body': 'lksadjflknldkjetojeaisldklfbsbnllaksj'
                }
            ]
    return render_template('index.html', title='', user=user, posts=posts)
```

(file app/templates/index.html)

```
<html>
  <head>
    {% if title %}
      <title>{{ title }} - microblog</title>
    {% else %}
      <title>Welcome to microblog</title>
    {% endif %}
  </head>
  <body>
    <h1>Hello, {{ user.nickname }}</h1>

    {% for post in posts %}
    <div>
      <p>{{ post.author.nickname }} says: <b>{{ post.body }}</b></p>
    </div>
    {% endfor %}
  </body>
</html>
```


This is pretty similar to for loops in python, but keep in mind the `{% endfor %}`.


### Template Inheritance

As we add more and more templates to our web app, there will be some parts of the page layout that are common to all files. Instead of copy-pasting them to every html file, let's use Jinja2's template inheritance feature to make a base template that will be added to all our html files. (file app/templates/base.html)

```
<html>
  <head>
    {% if title %}
    <title>{{ title }} - microblog</title>
    {% else %}
    <title>Welcome to microblog</title>
    {% endif %}
  </head>
  <body>
    <div>Microblog: <a href="/index">Home</a></div>
    <hr>
    {% block content %}{% endblock %}
  </body>
</html>
```

Note the new syntax. We will change `index.html` so that it will "inherit" the html code from `base.html`. (file app/templates/index.html)

```
{% extends "base.html" %}
{% block content %}
    <h1>Hi, {{ user.nickname }}!</h1>
    {% for post in posts %}
    <div><p>{{ post.author.nickname }} says: <b>{{ post.body }}</b></p></div>
    {% endfor %}
{% endblock %}
```

So far, we've learned templates and how they interact with Flask. Also, we can now use variables, control statements and loops in html files. Next, we will make a form so users can login to our web app.



## Web Forms

We will be using the extension Flask-WTF to handle web forms. Before we can use it, we'll have to make a configuration file in the root folder (file config.py):

```
WTF_CSRF_ENABLED = True
SECRET_KEY = 'you-will-never-guess'
```

Now we need the app to read and use the config file, by adding one line within app/__init__.py:

```
from flask import Flask

app = Flask(__name__)
app.config.from_object('config')

from app import views
```

### User Login Form

To create a form, we will make a class LoginForm which will contain the input fields (username and password). Here is the code for the form (file app/forms.py):

```
from flask.ext.wtf import Form
from wtforms import StringField, PasswordField, validators

class LoginForm(Form):
    username = StringField(u'Username', [validators.required(), validators.length(max=32, min=6)])
    password = PasswordField(u'Password', [validators.required(), validators.length(max=32, min=6)])
```

Notice that `username` is a `StringField` but `password` is a `PasswordField` since we want the password to be displayed as black circles while it's being typed.

### Form template

We will now create a standard-looking template which will have a username, password, and submit field. (file app/templates/login.html)

```
{% extends "base.html" %}
{% block content %}
    <h1>Sign In</h1>
    <form action="" method="post" name="login">
        {{ form.hidden_tag() }}
        <p>
            Username<br>
            {{ form.username(size=32) }}<br>
            {% for error in form.username.errors %}
                <span style="color: red;">[{{ error }}]</span>
            {% endfor %}<br>
        </p>
        <p>
            Password<br>
            {{ form.password(size=32) }}<br>
            {% for error in form.password.errors %}
                <span style="color: red;">[{{ error }}]</span>
            {% endfor %}<br>
        </p>
        <p><input type="submit" value="Sign In"></p>
    </form>
{% endblock %}
```

Note that we can also catch and print input errors using a for loop.


### Form Views

(insert description here) (file app/views.py)

```
from flask import render_template, flash, redirect
from app import app
from .forms import LoginForm

@app.route('/')
@app.route('/index')
def index():
    user = {'nickname': 'Juan Dela Cruz'}
    posts = [
                {
                    'author': {'nickname': 'John'},
                    'body': 'Lorem ipsum dolor sit amet'
                },
            ]
    return render_template('index.html', title='', user=user, posts=posts)

@app.route('/login', methods=['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        return redirect('/index')
    return render_template('login.html', title='Sign In', form=form)
```
(insert description here)


Now try running the web server then going to `localhost:5000/login`. Notice that if we enter a username or password that is less than 6 characters or more than 32 characters long, the form outputs an error. Else, it redirects to index, which means the output was valid.



## References
All thanks to Miguel Grinberg's [Mega-Tutorial Site](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world).
