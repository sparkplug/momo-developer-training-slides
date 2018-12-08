## MoMo API Developer Training 

Wifi Network: Tribe Kampala

Wifi Key: 	LXWX1H


---

### Themes We Shall Explore

- Introduction to the API
- Basic Auth
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

- Using Curl
- Using the [Sparkplug MoMo Python](https://github.com/sparkplug/momoapi-python) library

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
$ curl -v -X POST  -H "X-Reference-Id: UUID"  -H  "Ocp-Apim-Subscription-Key: APIKey"
 -H "Content-Type: application/json"  -d '{"providerCallbackHost": "sparkpl.ug"}'   https://ericssonbasicapi2.azure-api.net/v1_0/apiuser

```

This  creates an API User
---

### Basic Auth

Encode ApiKey:ApiSecret as base64 string. Pass it as a header in your requests using commandline

```bash
$ curl -i -X POST -H "Content-Type:application/json" -H "Ocp-Apim-Subscription-Key: ApiKey"   -d '{}' https://ericssonbasicapi2.azure-api.net/v1_0/apiuser/UserId/ApiKey
```


```bash
$ openssl enc -base64 <<< 'UUID'

```
Where `41187126-ab69-46ed-b7a5-7f3316c7942e` is the ApiKey `9ad0de137e194567bf310590b9471a63` is the API Secret

---

### Basic Auth

Basic Auth using Python

```python
>> import base64
>>  base64.b64encode('41187126-ab69-46ed-b7a5-7f3316c7942e:9ad0de137e194567bf310590b9471a63'.encode()) 

```

---

### Basic Auth 

Lets use basic auth to get an `Auth Token` with curl

```bash 
$ curl -i -X POST -H "Content-Type:application/json"  -H "Authorization: Basic NDExODcxMjYtYWI2OS00NmVkLWI3YTUtN2YzMzE2Yzc5NDJlOjlhZDBkZTEzN2UxOTQ1NjdiZjMxMDU5MGI5NDcxYTYz"  -d {} https://ericssonbasicapi2.azure-api.net/colection/token/ 
```

This returns the token. Lets use this token to do bearer token authentication. This is what we shall use for the rest of the API calls.

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

### Exploring the API

There are two main APIs for payments:

- requestToPay
- transfer

---


### Collections API Product

- This operation is used to request a payment from a consumer (Payer). The payer will be asked to authorize the payment. 
- The transaction will be executed once the payer has authorized the payment. 
- The requesttopay will be in status PENDING until the transaction is authorized or declined by the payer or it is timed out by the system.

---

### Request To Pay

POST /v1_0/requesttopay

https://app.swaggerhub.com/apis-docs/sparkplug/collection/1.0#/default/requesttopay-POST

---

### Request to Pay Using the Python Library

```python
from momoapi.client import MomoApi
client = MomoApi(APIKEY,USERID,APISECRET)
ref=client.requestToPay("256772123456", "600", "123456789", note="dd", message="dd", currency="EUR", environment="sandbox")
```

---

### Request to Pay Using the Python Library

So, what just happened? We create a client on the commandline, and made a requestToPay transaction. 

```python
>>> ref
```

You should see a response similar to this:

```python
>>> ref
{'transaction_ref': '33a9d94b-6828-4879-xxxx-e0ecb946d465'}
```
---

### Request to Pay Using the Python Library

So, what just happened? We create a client on the commandline, and made a requestToPay transaction. 

```python
>>> ref
```

You should see a response similar to this:

```python
>>> ref
{'transaction_ref': '33a9d94b-6828-4879-xxxx-e0ecb946d465'}
```
---

### Request to Pay Using the Python Library

We can then use this `Transaction Reference` to get the status of the Transaction

```python
>>> client.getTransactionStatus(ref['transaction_ref'])
{'financialTransactionId': '1854386795', 'externalId': '123456789', 'amount': '600', 'currency': 'EUR', 'payer': {'partyIdType': 'MSISDN', 'partyId': '256794631873'}, 'payerMessage': 'dd', 'payeeNote': 'dd', 'status': 'SUCCESSFUL'}
```

Voila!

---

### Check Balance

```python
>>> client.getBalance()
```

---

### Swagger URL


https://app.swaggerhub.com/apis-docs/sparkplug/sandbox-user_provisioning/1.0#/default/post-v1_0-apiuser

---

### Important Links

https://github.com/sparkplug/momoapi-python
https://github.com/sparkplug/momoapi-node
https://github.com/sparkplug/momoapi-example-app
https://github.com/sparkplug/momo-developer-training-slides

Send Pull Requests

---

## MoMo API Developer Training 

Feedback form: http://bit.do/apitraining

Community Chat: https://spectrum.chat/momo-api-developers/

Thank you. 




