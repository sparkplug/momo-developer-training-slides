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

### Using the Python Wrapper

```bash
$ momoapi
$ providerCallBackHost: https://akabbo.ug
$ Ocp-Apim-Subscription-Key: f83xx8d8xx6749f19a26e2265aeadbcdeg
```

where `providerCallBackHost` is your callback host and `Ocp-Apim-Subscription-Key` is your API key for the specific product to which you are subscribed.

---  

### Using the Python Wrapper

You should get the following response.

```bash
Here is your User Id and API secret : {'apiKey': 'b0431db58a9b41faa8f5860230xxxxxx', 'UserId': '053c6dea-dd68-xxxx-xxxx-c830dac9f401'}

```

---
### Using the Python Wrapper

```python
from momoapi.client import MomoApi
client = MomoApi(APIKEY,USERID,APISECRET)
ref=client.requestToPay("256772123456", "600", "123456789", note="dd", message="dd", currency="EUR", environment="sandbox")
```

Replace `APIKEY`, `USERID`, `APISECRET` with the correct string literals.
 
---





