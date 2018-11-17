## MoMo API Developer Training 

Hello and welcome.


---

### Themes We Shall Explore

- Introduction to the API
- Authorization and Authentication
- API Requests with Curl
- Sample Code Walkthrough
- Best Practices

---

### Introduction

First, what is an API?

"a set of functions and procedures that allow the creation of applications which access the features or data of an operating system, application, or other service." - Wikipedia

---

### Introduction

https://momodeveloper.mtn.com

---

### To Start

- Sign Up
- Subscribe to a Product
- Generate API User and API Key

---

### Sign Up

Head over the to domain below

https://momodeveloper.mtn.com/signup

---

### Subscribe to Product

After creating an account, head on over to the products page. The list of products:

- Collections
- Disbursements
- Remittance 
- Collection Widget

---

### Subscribe to Collections

Click on `Collections` and hit the `Subscribe` button. This generates your `API Key`. The API is unique to the product and you will need an `API Key` for each product you use.

---

### Generate API User & API Secret

Currently, there are two ways to create these:

- Using the Sparkplug MoMo Python library
- Using Curl

---

### Using the Python Wrapper

https://github.com/sparkplug/momoapi-python

Follow the README

---

### Using the Python Wrapper

git clone https://github.com/sparkplug/momoapi-python

--- 

### Using the Python Wrapper

Creation of virtualenv:

```bash
$ virtualenv -p python3 <desired-path>
```

Activate the virtualenv:

```bash
$ source <desired-path>/bin/activate
```

Next, we install from source:

```bash
$ python setup.py install
```

--- 






