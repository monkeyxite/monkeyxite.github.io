<!--
.. title: test nicola with markdown
.. slug: test-nicola-with-markdown
.. date: 2018-10-14 00:07:27 UTC+08:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
-->

# Ch1
Probably all of you learn Flask studies via [The Flask Mega-Tutorial](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). Even though I believe it's typical that starting a tutorial for beginners to start learn by standlone env, a Paas version would be suiable for beginers who are aiming for using Paas as Infrustruction as Paas is "next big thing" and it's popular all over the word even in China. That's enough talk, let's get the work done.

List of tutorials:

1. [getting started and basic configurations in SAE](.)
2. []


SAE Basic Configuration
========================
Even though sae team claimed that flask only support 0.7 or some other version, I tried latest 0.10.1 in config file it works fine so far.

##SVN
Create first version and you would have a init version. detailed useage you could refer [SVN Doc for SAE](http://sae.sina.com.cn/?m=devcenter&catId=211).
After checkout, you would have a basic folder name 1 which could be used as a repo for your useage. 

##Initialize the MySQL
As sooner or later we would adopt MySQL, so we need intiallize it from the control panel.

##Local env (optional)
Please refer to [SAE python user guide](http://python.sinaapp.com/doc/index.html) for more details 


"Hello World" from Flask in SAE
===============================

##application folder structure
A recommandated project structure would be like this for now:


	1/
	    config.yaml
	    index.wsgi
	    main.py
	    app/
	        views.py
	        __init__.py
	        static/
	    tmp/



##flask modification in SAE

index.wsgi would be frontgate for all request, need a instance to hanle http requests:

```python
import sae

from main import app

application = sae.create_wsgi_app(app)
```

main.py would be like this: 

```python
from app import app
from flask import g, request
import MySQLdb

app.debug = True

from sae.const import (MYSQL_HOST, MYSQL_HOST_S,
	MYSQL_PORT, MYSQL_USER, MYSQL_PASS, MYSQL_DB
)

@app.before_request
def before_request():
	g.db = MySQLdb.connect(MYSQL_HOST, MYSQL_USER, MYSQL_PASS,
							MYSQL_DB, port=int(MYSQL_PORT))

@app.teardown_request
def teardown_request(exception):
	if hasattr(g, 'db'): g.db.close()
```


Ready to go
===========
SVN update and visit your application ID, or here to see what is [expected](http://1.flasktutorial.sinaapp.com/).

# Ch2
Probably all of you learn Flask studies via [The Flask Mega-Tutorial](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). Even though I believe it's typical that starting a tutorial for beginners to start learn by standlone env, a Paas version would be suiable for beginers who are aiming for using Paas as Infrustruction as Paas is "next big thing" and it's popular all over the word even in China. That's enough talk, let's get the work done.

List of tutorials:

1. [getting started and basic configurations in SAE](.)
2. [template]

Recap
=======
What we already have now is:



Why we need template?
========================



"Hello World" from Flask in SAE
===============================

## First impression of template engine in Flask
###add index template
create a templates folder in app, the content is 
```html
<html>
  <head>
    <title>{{title}} - microblog</title>
  </head>
  <body>
      <h1>Hello, {{user.nickname}}!</h1>
  </body>
</html>
```

###modify view to render from template

view will change into:

```python
from flask import render_template
from app import app

@app.route('/')
@app.route('/index')
def index():
    user = { 'nickname': 'Miguel' } # fake user
    return render_template("index.html",
        title = 'Home',
        user = user)
```

Then you will find you pass the user name into the template. Jinja2 take care of ...

## Higher level templated skills
Let move on for more details

### Control

*The Jinja2 templates also support control statements, given inside {%...%} blocks*.
update index template like this:

```html
<html>
  <head>
    {% if title %}
    <title>{{title}} - microblog</title>
    {% else %}
    <title>Welcome to microblog</title>
    {% endif %}
  </head>
  <body>
      <h1>Hello, {{user.nickname}}!</h1>
  </body>
</html>
```
Then, feel free to remove the `title` argue in view.py, you will find that logic in index.html will handle missing title situation.

### Loop
First of all, you need provide contents(like `posts` as argue here) in view to show in templates. update `view.py` as the following:
```python
from app import app
from flask import render_template

@app.route('/')
@app.route('/index')
def index():
    user = {'nickname': "SAE User"} #fake
    posts = [ # fake array of posts
        { 
            'author': { 'nickname': 'John' }, 
            'body': 'Beautiful day in Portland!' 
        },
        { 
            'author': { 'nickname': 'Susan' }, 
            'body': 'The Avengers movie was so cool!' 
        }
    ]
    return render_template("index.html",
        title = 'Home',
        user = user,
        posts = posts)
```
Then, let us take a look at how `for` loop works in `index.html`jinja2:
```html
<html>
  <head>
    {% if title %}
    <title>{{title}} - microblog</title>
    {% else %}
    <title>microblog</title>
    {% endif %}
  </head>
  <body>
    <h1>Hi, {{user.nickname}}!</h1>
    {% for post in posts %}
    <p>{{post.author.nickname}} says: <b>{{post.body}}</b></p>
    {% endfor %}
  </body>
</html>
```

###Tempalte Inheritance
I could imagine how boring it is to repeat `head` stuff in htmls everytime when you create tempaltes, while thanks to inheritance of Jinja2, we could make our life easier by creating `base.html`, in this file we store all the repeating stuff for other siblings of our apps.
```html
<html>
  <head>
    {% if title %}
    <title>{{title}} - microblog</title>
    {% else %}
    <title>microblog</title>
    {% endif %}
  </head>
  <body>
    <div>Microblog: <a href="/index">Home</a></div>
    <hr>
    {% block content %}{% endblock %}
  </body>
</html>
```
Then, other templates could reuse the generic stuff and do it own specific logic, like `index.html`:
```html
{% extends "base.html" %}
{% block content %}
<h1>Hi, {{user.nickname}}!</h1>
{% for post in posts %}
<div><p>{{post.author.nickname}} says: <b>{{post.body}}</b></p></div>
{% endfor %}
{% endblock %}
```

Ready to go
===========
SVN update and visit your application ID in this version to enjoy what you've done already!
You could always refer [here](http://2.flasktutorial.sinaapp.com/) to see what is expected.


# Ch3 
Probably all of you learn Flask studies via [The Flask Mega-Tutorial](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). Even though I believe it's typical that starting a tutorial for beginners to start learn by standlone env, a Paas version would be suiable for beginers who are aiming for using Paas as Infrustruction as Paas is "next big thing" and it's popular all over the word even in China. That's enough talk, let's get the work done.

List of tutorials:

1. [getting started and basic configurations in SAE](.)
2. [template]
3. [Webform]

Recap
=======
What we already have now is seting up a basic Flask in SAE, and using the template engine in flask. While, web form is always one of the most important way to interact with users. What are we waiting for?



WTF in Flask
========================

##about WTF in Flask
In Flask WTF is most widely used form extension for form handling. more details you could get from :

- [WTForm](http://wtforms.readthedocs.org/en/latest/)
- [WTForm Course](http://wtforms.readthedocs.org/en/latest/crash_course.html)
- [flask-wtf](https://flask-wtf.readthedocs.org/en/latest/)

##config external packages in SAE

There are several ways to install the packages in SAE:

* put in the version folder, import them directly
* use remote API install related packages
* use virtualenv, then use SAE remote API to install related packages

As there are so many external packages to be installed in SAE, so we preferred 2 or 3 solution in this case. details refer to [link](https://windrocblog.sinaapp.com/?p=935) or [link2](http://cloudbbs.org/forum.php?mod=viewthread&tid=12860), or [offical doc](http://python.sinaapp.com/doc/tools.html#saecloud).

Anyway, after you installed the nessary package, in our case flask-wtf, you could modify the `index.wsgi` like this:
```python
import os
import sys
root = os.path.dirname(__file__)
# 两者取其一
sys.path.insert(0, os.path.join(root, 'site-packages')) #if you do not zip the packages
sys.path.insert(0, os.path.join(root, 'site-packages.zip')) # preferred for zipped packages
``` 

Then, you could import the packages in your project.

## Config flask with the WTF extention
Many extensions require some amount of configuration, fow now we could config our web app with `config.py` in version 3.
```python
CSRF_ENABLED = True
SECRET_KEY = 'you-will-never-guess'
```
This is accuary required by WTF, `CSRF_ENABLED` activates the [cross-site request forgery](http://en.wikipedia.org/wiki/Cross-site_request_forgery) prevention. In most cases you want to have this option enabled as it makes your app more secure.

And `SECRET_KEY` setting is noly needed when `CSRF` is enable, and is used to create a cryptographic token that is used to validate a form. WHen you write your own apps, please make sure to set the key into something others nerver to guess.


##load config in your flask app
Well, this config file need to imported by our app to use it. Modify the file `app/__init__.py` as the following:
```python
app.config.from_object('config')
```

Start using form in Flask
===============================

## First impression of forms in Flask
Web froms are represented in Flask-WTF as objects, subclassed from class *Form*. A form subclass simply defines the fields of the form as class variables.

A login form will be created by using OpenID. We don't have to validate passwords.

The OpenID login only requires one string, called OpenID. We will also put a 'remember me' checkbox in the form.

The form would be like this `app/form.py`:
```python
from flask.ext.wtf import Form
from wtforms import TextField, BooleanField
from wtforms.validators import Required

class LoginForm(Form):
    openid = TextField('openid', validators = [Required()])
    remember_me = BooleanField('remember_me', default = False)
```

in the file, we imported the *Form* class, as twoo field classes we needed: `TextField` and `BooleanField`.
Onething to be highlighted here is the validator in openid field: `Required` validator simply checks that the field is not submitted empty. 

## templates for Form
create a templates named `login.html` for the login form as representative in `app/tempaltes`, the content is 
```html
<!-- extend from base layout -->
{% extends "base.html" %}

{% block content %}
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID:<br>
        {{form.openid(size=80)}}<br>
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
as previous templates intro, inherited from 'base.html' we creat the tempalte for form. While there are several differences which are worth to highlight:

The template expects a form object instantiated from the form class we just defined stored in a template argument named form. We will take care of sending this template argument to the template next, when we write the view function that renders this template.

The `form.hidden_tag()` template argument will get replaced with a hidden field that implements the CSRF prevention that we enabled in the configuration. This field needs to be in all your forms if you have CSRF enabled.

The actual fields of our form are also rendered by the form object, you just have to refer to a {{form.field_name}} template argument in the place where the field should be inserted. Some fields can take arguments. In our case, we are asking the form to generate our openid field with a width of 80 characters.

Since we have not defined the submit button in the form class we have to define it as a regular field. The submit field does not carry any data so it doesn't need to be defined in the form class.


###modify view to render from template

The last step to complete a form is to code a view funtion to handle the specific URL requestion and pass throught the parameteres and render it in the tempaltes.

add contends for form in the `app/views.py` as following:

```python
from flask import render_template, flash, redirect
from app import app
from forms import LoginForm

#index view function suppressed for brevity

@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    return render_template('login.html', 
        title = 'Sign In',
        form = form)
```
So, we imported the `LoginForm` Class in view, and sent it to the template.
Add in the route decorator, we defined the `methods` arguments. It tells the flask this view fuction accepts not only GET request, but also POST request..

Not you can see the form in your browser

## Receiving data from form submission

How did you handle the data from form? Again, in the view func:

```python
@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        flash('Login requested for OpenID="' + form.openid.data + '", remember_me=' + str(form.remember_me.data))
        return redirect('/index')
    return render_template('login.html', 
        title = 'Sign In',
        form = form)
``` 
The `validate_on_submit` method does all the form processing work. When the form just being presented to the user, then it will return `False`, which means Flask will just render the template.

If `validate_on_submit` is called as part of a form submission request, then it will gather all data, run any validators attached to fields, and if everything is  all right and it will return `True`, indicating that the data is valid to proceed next step.

* if validatio pass through, two more steps are processing after that. `flash` function is a quick way to show a message on the next page presented to the user. By now, we just show the submitted data to user. of course, we need update the template to show these flash messages. This time we will update in the `app/templates/base.html` as these flashese would be used as a generic functionalities:
```html
<html>
  <head>
    {% if title %}
    <title>{{title}} - microblog</title>
    {% else %}
    <title>microblog</title>
    {% endif %}
  </head>
  <body>
    <div>Microblog: <a href="/index">Home</a></div>
    <hr>
    {% with messages = get_flashed_messages() %}
    {% if messages %}
    <ul>
    {% for message in messages %}
        <li>{{ message }} </li>
    {% endfor %}
    </ul>
    {% endif %}
    {% endwith %}
    {% block content %}{% endblock %}
  </body>
</html>
```
Jiajia `with` will xxxxxxxxxx. the other step is using `redirect` to tells the client web browser to navigate to a different page(index in this case).
noted that the flashed messages will display even if a view function ends in a redirect.

* if validation teturn `Flase`, we would see later how to show an error message when vlalidation fails.

This is a great time to start the app and test how the form works. Make sure you try submitting the form with the openid field empty, to see how the Required validator halts the submit process.


##improve the field validation

Currently, if validation fails, the page will not submit. While a hint to user which part is missing is helpful to imporvement the usibility. Luckily, Flask-WTF also makes this an easy task.

update `app/templates/login.html` template like this:

```html
<!-- extend base layout -->
{% extends "base.html" %}

{% block content %}
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID:<br>
        {{form.openid(size=80)}}<br>
        {% for error in form.errors.openid %}
        <span style="color: red;">[{{error}}]</span>
        {% endfor %}<br>
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
The only change we've made is to add a for loop that renders any messages added by the validators below the openid field. *As a general rule, any fields that have validators attached will have errors added under `form.errors.field_name`*. In our case we use `form.errors.openid`. We display these messages in a red style to call the user's attention.

## Dealing with OpenID

If you have an account with Google, you have an OpenID with them. Likewise with Yahoo, AOL, Flickr and many other providers.

While we need define which services are supported in our app, so you need update config file(file `config.py`) like this

```python
CSRF_ENABLED = True
SECRET_KEY = 'you-will-never-guess'

OPENID_PROVIDERS = [
    { 'name': 'Google', 'url': 'https://www.google.com/accounts/o8/id' },
    { 'name': 'Yahoo', 'url': 'https://me.yahoo.com' },
    { 'name': 'AOL', 'url': 'http://openid.aol.com/<username>' },
    { 'name': 'Flickr', 'url': 'http://www.flickr.com/<username>' },
    { 'name': 'MyOpenID', 'url': 'https://www.myopenid.com' }]
```

Then, let us take a look at how we need update view to handle OpenID:
```python
@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        flash('Login requested for OpenID="' + form.openid.data + '", remember_me=' + str(form.remember_me.data))
        return redirect('/index')
    return render_template('login.html', 
        title = 'Sign In',
        form = form,
        providers = app.config['OPENID_PROVIDERS'])
```
It just pass through the 'OPENID_PROVIDERS' to tempate.

Now, some modicidations are needed to handle the pass-through `OPENID_OROVIDERS`, update the `app/templates/login.html`:
```html
<!-- extend base layout -->
{% extends "base.html" %}

{% block content %}
<script type="text/javascript">
function set_openid(openid, pr)
{
    u = openid.search('<username>')
    if (u != -1) {
        // openid requires username
        user = prompt('Enter your ' + pr + ' username:')
        openid = openid.substr(0, u) + user
    }
    form = document.forms['login'];
    form.elements['openid'].value = openid
}
</script>
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID, or select one of the providers below:<br>
        {{form.openid(size=80)}}
        {% for error in form.errors.openid %}
        <span style="color: red;">[{{error}}]</span>
        {% endfor %}<br>
        |{% for pr in providers %}
        <a href="javascript:set_openid('{{pr.url}}', '{{pr.name}}');">{{pr.name}}</a> |
        {% endfor %}
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
Some OpenIDs include the user's username, so for those we have to have a bit of javascript magic that prompts the user for its username and then composes the OpenID. When the user clicks on an OpenID provider link and (optionally) enters the username, the OpenID for that provider is inserted in the text field.


Ready to go
===========
SVN update and visit your application ID in this version to enjoy what you've done already!
You could always refer [here](http://3.flasktutorial.sinaapp.com/) to see what is expected.

For now we just finish basic progress regarding forms, there are lots of things to be fixed till we actually do something, such as database setup in next artical.

# Ch4
Probably all of you learn Flask studies via [The Flask Mega-Tutorial](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world). Even though I believe it's typical that starting a tutorial for beginners to start learn by standlone env, a Paas version would be suiable for beginers who are aiming for using Paas as Infrustruction as Paas is "next big thing" and it's popular all over the word even in China. That's enough talk, let's get the work done.

List of tutorials:

1. [getting started and basic configurations in SAE](.)
2. [template]
3. [Webform]
4. [Database]

Recap
=======
What we already have now is seting up a basic Flask in SAE without anyn database configuration. And as you may already known, database is essential part for web developing and we will start config it in SAE on this artical.



WTF in Flask
========================

##about db migration in SAE
There are 3 ways for now I thouht out to migrate db in SAE
- Using local db, then update date into remote sae sever.
- [WTForm Course](http://wtforms.readthedocs.org/en/latest/crash_course.html)
- [flask-wtf](https://flask-wtf.readthedocs.org/en/latest/)

##config external packages in SAE

There are several ways to install the packages in SAE:

* put in the version folder, import them directly
* use remote API install related packages
* use virtualenv, then use SAE remote API to install related packages

As there are so many external packages to be installed in SAE, so we preferred 2 or 3 solution in this case. details refer to [link](https://windrocblog.sinaapp.com/?p=935) or [link2](http://cloudbbs.org/forum.php?mod=viewthread&tid=12860), or [offical doc](http://python.sinaapp.com/doc/tools.html#saecloud).

Anyway, after you installed the nessary package, in our case flask-wtf, you could modify the `index.wsgi` like this:
```python
import os
import sys
root = os.path.dirname(__file__)
#sys.path.insert(0, os.path.join(root, 'site-packages')) #if you do not zip the packages
sys.path.insert(0, os.path.join(root, 'site-packages.zip')) # preferred for zipped packages
``` 

Then, you could import the packages in your project.

## Config flask with the WTF extention
Many extensions require some amount of configuration, fow now we could config our web app with `config.py` in version 3.
```python
CSRF_ENABLED = True
SECRET_KEY = 'you-will-never-guess'
```
This is accuary required by WTF, `CSRF_ENABLED` activates the [cross-site request forgery](http://en.wikipedia.org/wiki/Cross-site_request_forgery) prevention. In most cases you want to have this option enabled as it makes your app more secure.

And `SECRET_KEY` setting is noly needed when `CSRF` is enable, and is used to create a cryptographic token that is used to validate a form. WHen you write your own apps, please make sure to set the key into something others nerver to guess.


##load config in your flask app
Well, this config file need to imported by our app to use it. Modify the file `app/__init__.py` as the following:
```python
app.config.from_object('config')
```

Start using form in Flask
===============================

## First impression of forms in Flask
Web froms are represented in Flask-WTF as objects, subclassed from class *Form*. A form subclass simply defines the fields of the form as class variables.

A login form will be created by using OpenID. We don't have to validate passwords.

The OpenID login only requires one string, called OpenID. We will also put a 'remember me' checkbox in the form.

The form would be like this `app/form.py`:
```python
from flask.ext.wtf import Form
from wtforms import TextField, BooleanField
from wtforms.validators import Required

class LoginForm(Form):
    openid = TextField('openid', validators = [Required()])
    remember_me = BooleanField('remember_me', default = False)
```

in the file, we imported the *Form* class, as twoo field classes we needed: `TextField` and `BooleanField`.
Onething to be highlighted here is the validator in openid field: `Required` validator simply checks that the field is not submitted empty. 

## templates for Form
create a templates named `login.html` for the login form as representative in `app/tempaltes`, the content is 
```html
<!-- extend from base layout -->
{% extends "base.html" %}

{% block content %}
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID:<br>
        {{form.openid(size=80)}}<br>
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
as previous templates intro, inherited from 'base.html' we creat the tempalte for form. While there are several differences which are worth to highlight:

The template expects a form object instantiated from the form class we just defined stored in a template argument named form. We will take care of sending this template argument to the template next, when we write the view function that renders this template.

The `form.hidden_tag()` template argument will get replaced with a hidden field that implements the CSRF prevention that we enabled in the configuration. This field needs to be in all your forms if you have CSRF enabled.

The actual fields of our form are also rendered by the form object, you just have to refer to a {{form.field_name}} template argument in the place where the field should be inserted. Some fields can take arguments. In our case, we are asking the form to generate our openid field with a width of 80 characters.

Since we have not defined the submit button in the form class we have to define it as a regular field. The submit field does not carry any data so it doesn't need to be defined in the form class.


###modify view to render from template

The last step to complete a form is to code a view funtion to handle the specific URL requestion and pass throught the parameteres and render it in the tempaltes.

add contends for form in the `app/views.py` as following:

```python
from flask import render_template, flash, redirect
from app import app
from forms import LoginForm

#index view function suppressed for brevity

@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    return render_template('login.html', 
        title = 'Sign In',
        form = form)
```
So, we imported the `LoginForm` Class in view, and sent it to the template.
Add in the route decorator, we defined the `methods` arguments. It tells the flask this view fuction accepts not only GET request, but also POST request..

Not you can see the form in your browser

## Receiving data from form submission

How did you handle the data from form? Again, in the view func:

```python
@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        flash('Login requested for OpenID="' + form.openid.data + '", remember_me=' + str(form.remember_me.data))
        return redirect('/index')
    return render_template('login.html', 
        title = 'Sign In',
        form = form)
``` 
The `validate_on_submit` method does all the form processing work. When the form just being presented to the user, then it will return `False`, which means Flask will just render the template.

If `validate_on_submit` is called as part of a form submission request, then it will gather all data, run any validators attached to fields, and if everything is  all right and it will return `True`, indicating that the data is valid to proceed next step.

* if validatio pass through, two more steps are processing after that. `flash` function is a quick way to show a message on the next page presented to the user. By now, we just show the submitted data to user. of course, we need update the template to show these flash messages. This time we will update in the `app/templates/base.html` as these flashese would be used as a generic functionalities:
```html
<html>
  <head>
    {% if title %}
    <title>{{title}} - microblog</title>
    {% else %}
    <title>microblog</title>
    {% endif %}
  </head>
  <body>
    <div>Microblog: <a href="/index">Home</a></div>
    <hr>
    {% with messages = get_flashed_messages() %}
    {% if messages %}
    <ul>
    {% for message in messages %}
        <li>{{ message }} </li>
    {% endfor %}
    </ul>
    {% endif %}
    {% endwith %}
    {% block content %}{% endblock %}
  </body>
</html>
```
Jiajia `with` will xxxxxxxxxx. the other step is using `redirect` to tells the client web browser to navigate to a different page(index in this case).
noted that the flashed messages will display even if a view function ends in a redirect.

* if validation teturn `Flase`, we would see later how to show an error message when vlalidation fails.

This is a great time to start the app and test how the form works. Make sure you try submitting the form with the openid field empty, to see how the Required validator halts the submit process.


##improve the field validation

Currently, if validation fails, the page will not submit. While a hint to user which part is missing is helpful to imporvement the usibility. Luckily, Flask-WTF also makes this an easy task.

update `app/templates/login.html` template like this:

```html
<!-- extend base layout -->
{% extends "base.html" %}

{% block content %}
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID:<br>
        {{form.openid(size=80)}}<br>
        {% for error in form.errors.openid %}
        <span style="color: red;">[{{error}}]</span>
        {% endfor %}<br>
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
The only change we've made is to add a for loop that renders any messages added by the validators below the openid field. *As a general rule, any fields that have validators attached will have errors added under `form.errors.field_name`*. In our case we use `form.errors.openid`. We display these messages in a red style to call the user's attention.

## Dealing with OpenID

If you have an account with Google, you have an OpenID with them. Likewise with Yahoo, AOL, Flickr and many other providers.

While we need define which services are supported in our app, so you need update config file(file `config.py`) like this

```python
CSRF_ENABLED = True
SECRET_KEY = 'you-will-never-guess'

OPENID_PROVIDERS = [
    { 'name': 'Google', 'url': 'https://www.google.com/accounts/o8/id' },
    { 'name': 'Yahoo', 'url': 'https://me.yahoo.com' },
    { 'name': 'AOL', 'url': 'http://openid.aol.com/<username>' },
    { 'name': 'Flickr', 'url': 'http://www.flickr.com/<username>' },
    { 'name': 'MyOpenID', 'url': 'https://www.myopenid.com' }]
```

Then, let us take a look at how we need update view to handle OpenID:
```python
@app.route('/login', methods = ['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        flash('Login requested for OpenID="' + form.openid.data + '", remember_me=' + str(form.remember_me.data))
        return redirect('/index')
    return render_template('login.html', 
        title = 'Sign In',
        form = form,
        providers = app.config['OPENID_PROVIDERS'])
```
It just pass through the 'OPENID_PROVIDERS' to tempate.

Now, some modicidations are needed to handle the pass-through `OPENID_OROVIDERS`, update the `app/templates/login.html`:
```html
<!-- extend base layout -->
{% extends "base.html" %}

{% block content %}
<script type="text/javascript">
function set_openid(openid, pr)
{
    u = openid.search('<username>')
    if (u != -1) {
        // openid requires username
        user = prompt('Enter your ' + pr + ' username:')
        openid = openid.substr(0, u) + user
    }
    form = document.forms['login'];
    form.elements['openid'].value = openid
}
</script>
<h1>Sign In</h1>
<form action="" method="post" name="login">
    {{form.hidden_tag()}}
    <p>
        Please enter your OpenID, or select one of the providers below:<br>
        {{form.openid(size=80)}}
        {% for error in form.errors.openid %}
        <span style="color: red;">[{{error}}]</span>
        {% endfor %}<br>
        |{% for pr in providers %}
        <a href="javascript:set_openid('{{pr.url}}', '{{pr.name}}');">{{pr.name}}</a> |
        {% endfor %}
    </p>
    <p>{{form.remember_me}} Remember Me</p>
    <p><input type="submit" value="Sign In"></p>
</form>
{% endblock %}
```
Some OpenIDs include the user's username, so for those we have to have a bit of javascript magic that prompts the user for its username and then composes the OpenID. When the user clicks on an OpenID provider link and (optionally) enters the username, the OpenID for that provider is inserted in the text field.


Ready to go
===========
SVN update and visit your application ID in this version to enjoy what you've done already!
You could always refer [here](http://3.flasktutorial.sinaapp.com/) to see what is expected.

For now we just finish basic progress regarding forms, there are lots of things to be fixed till we actually do something, such as database setup in next artical.
