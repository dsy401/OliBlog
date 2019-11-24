---
layout: post_layout
title: Python Flask
date: 2019-11-20 22:20:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### **1\. The environment configuration**

My current development environment is Miniconda3+PyCharm. The development environment doesn't really matter, you can use Python3+Nodepad yourself. Install the Flask library:

~~~python
pip install Flask
~~~

### **2\. The first application Save the following as helloworld.py:**

~~~python
# import Flask class
from flask import Flask
# Initialise，can be consider as fixed format
app = Flask(__name__)

# route() is used for setting route like spring route
@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    # app.run(host, port, debug, options)
    # default：host=127.0.0.1, port=5000, debug=false
    app.run()
~~~

Run the file directly and go to: http://127.0.0.1:5000/helloworld. The results are as follows:

![](/uploads/screen-shot-2019-11-25-at-10-28-17-am.png){: width="590" height="130"}

### **3\. Get and Post implementation**

3\.1 Create the template file used By default, Flask looks for the template file in the templates directory, and creates the templates folder in the same directory as the htlloworld.py directory above. Create get.html under the templates folder and write the following:

~~~html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>get request demo</title>
</head>
<body>
    <form action="/deal_request" method="get">
        <input type="text" name="q" />
        <input type="submit" value="search" />
    </form>
</body>
</html>
~~~

Create post.html in the templates folder and write the following:

~~~html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>post request demo</title>
</head>
<body>
    <form action="/deal_request" method="post">
        <input type="text" name="q" />
        <input type="submit" value="search" />
    </form>
</body>
</html>
~~~

Finally create a result.html in the templates folder, write the following:

~~~html
{% raw %}<h1>{{ result }}</h1>{% endraw %}
~~~

3\.2 Writing related processing methods Add get\_html(), post\_html(), and deal\_request() methods to helloworld.py. See the comments for more details. The current helloworld.py content is as follows:

~~~python
# import Flask class
from flask import Flask
from flask import render_template
from flask import request
# Initialize
app = Flask(__name__)

#be equal to：app.add_url_rule('/', 'helloworld', hello_world)
@app.route('/helloworld')
def hello_world():
    return 'Hello, World!'

@app.route('/get.html')
def get_html():
    return render_template('get.html')

@app.route('/post.html')
def post_html():
    return render_template('post.html')

@app.route('/deal_request', methods = ['GET', 'POST'])
def deal_request():
    if request.method == "GET":
        get_q = request.args.get("q","")
        return render_template("result.html", result=get_q)
    elif request.method == "POST":
        post_q = request.form["q"]
        return render_template("result.html", result=post_q)

if __name__ == '__main__':
    # app.run(host, port, debug, options)
    app.run()
~~~