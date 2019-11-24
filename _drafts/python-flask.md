---
layout: post_layout
title: Python Flask
date: 2019-11-20 22:20:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### First, the environment configuration

My current development environment is Miniconda3+PyCharm. The development environment doesn't really matter, you can use Python3+Nodepad yourself. Install the Flask library:

```python
pip install Flask
```

```python
# 导入Flask类
from flask import Flask
# 实例化，可视为固定格式
app = Flask(__name__)

# route()方法用于设定路由；类似spring路由配置
@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    # app.run(host, port, debug, options)
    # 默认值：host=127.0.0.1, port=5000, debug=false
    app.run()
```


```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>get请求示例</title>
</head>
<body>
    <form action="/deal_request" method="get">
        <input type="text" name="q" />
        <input type="submit" value="搜索" />
    </form>
</body>
</html>
```

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>post请求示例</title>
</head>
<body>
    <form action="/deal_request" method="post">
        <input type="text" name="q" />
        <input type="submit" value="搜索" />
    </form>
</body>
</html>
```


```html
<h1>{{ result }}</h1>
```

```python
# 导入Flask类
from flask import Flask
from flask import render_template
from flask import request
# 实例化，可视为固定格式
app = Flask(__name__)

# route()方法用于设定路由；类似spring路由配置
#等价于在方法后写：app.add_url_rule('/', 'helloworld', hello_world)
@app.route('/helloworld')
def hello_world():
    return 'Hello, World!'

# 配置路由，当请求get.html时交由get_html()处理
@app.route('/get.html')
def get_html():
    # 使用render_template()方法重定向到templates文件夹下查找get.html文件
    return render_template('get.html')

# 配置路由，当请求post.html时交由post_html()处理
@app.route('/post.html')
def post_html():
    # 使用render_template()方法重定向到templates文件夹下查找post.html文件
    return render_template('post.html')

# 配置路由，当请求deal_request时交由deal_request()处理
# 默认处理get请求，我们通过methods参数指明也处理post请求
# 当然还可以直接指定methods = ['POST']只处理post请求, 这样下面就不需要if了
@app.route('/deal_request', methods = ['GET', 'POST'])
def deal_request():
    if request.method == "GET":
        # get通过request.args.get("param_name","")形式获取参数值
        get_q = request.args.get("q","")
        return render_template("result.html", result=get_q)
    elif request.method == "POST":
        # post通过request.form["param_name"]形式获取参数值
        post_q = request.form["q"]
        return render_template("result.html", result=post_q)

if __name__ == '__main__':
    # app.run(host, port, debug, options)
    # 默认值：host=127.0.0.1, port=5000, debug=false
    app.run()
```
