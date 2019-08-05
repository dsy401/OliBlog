---
layout: post_layout
title: Selenium
date: 2019-06-01 18:31:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

It is a big data era today. We use big data to handle anything like AI, Image Identification and machine learning. But, have you guys known where the data comes from? The data may come from web, newspaper, voice. So, i gonna talk about Selenium to get the data from web.

**What is Selenium?&nbsp; &nbsp;** &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br>Selenium is a complete web application testing system that includes test recording (selenium IDE), writing and running (Selenium Remote Control) and testing parallel processing (Selenium Grid). Selenium's core Selenium Core is based on JsUnit and is written entirely in JavaScript, so it can be used on any browser that supports JavaScript. Selenium can simulate real browsers, automate testing tools, and support multiple browsers. The crawler is mainly used to solve JavaScript rendering problems.

Here to talk about the more important PhantomJS, PhantomJS is a WebKit-based server-side JavaScript API that supports the Web without browser support. It supports various Web standards quickly and natively: Dom processing, CSS selector, JSON, etc. . PhantomJS can be used for page automation, network monitoring, web page capture, and no interface testing

&nbsp;

**Declare browser object**
```python
from selenium import webdriver

browser = webdriver.Chrome()
browser = webdriver.Firefox()
```
```python
from selenium import webdriver

browser = webdriver.Chrome()

browser.get("http://www.baidu.com")
print(browser.page_source)
browser.close() 
```
```python
from selenium import webdriver

browser = webdriver.Chrome()

browser.get("http://www.taobao.com")
input_first = browser.find_element_by_id("q")
input_second = browser.find_element_by_css_selector("#q")
input_third = browser.find_element_by_xpath('//*[@id="q"]')
print(input_first)
print(input_second)
print(input_third)
browser.close()
```
