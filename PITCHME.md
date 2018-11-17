## MoMo API Developer Training 

Wifi Network: Tribe Kampala

Wifi Key: FPWFAV


---

### Themes We Shall Explore

- Introduction to the API
- Authorization and Authentication
- API Requests with Curl
- Sample Code Walkthrough
- Best Practices

---

### Introduction

https://momodeveloper.mtn.com

---
### Introduction

First, what is an API?

"a set of functions and procedures that allow the creation of applications which access the features or data of an operating system, application, or other service." - Wikipedia

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

### Using Curl

First we generate a UUID on bash

```bash
$ uuidgen

```

---

### Using Curl

First we generate a UUID with python

```bash
$ curl -v -X POST  -H "X-Reference-Id: your uuid4"  -H  "Ocp-Apim-Subscription-Key: APIKey”
 -H "Content-Type: application/json"  -d '{"providerCallbackHost": "sparkpl.ug"}'   https://ericssonbasicapi2.azure-api.net/v1_0/apiuser

```

This returns your `API Secret`
---

### Using Curl

Basic Auth using Commandline

```bash
$ openssl enc -base64 <<< 'UUID'

```

---

### Using Curl

Basic Auth using Python

```python
>> import base64
>>  base64.b64encode('41187126-ab69-46ed-b7a5-7f3316c7942e:9ad0de137e194567bf310590b9471a63'.encode()) 

```

---

### Swagger URL


https://app.swaggerhub.com/apis-docs/sparkplug/sandbox-user_provisioning/1.0#/default/post-v1_0-apiuser


---
