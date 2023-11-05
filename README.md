# 🚀 Getting Started

Welcome to **Astronomy API**, a web API for retrieving astronomical information.

## Obtaining an Application ID and a Secret

To make API calls, you will first need to create an account. Go to the [Signup](http://astronomyapi.com/auth/signup) page to create your free account.

After creating an account, you must obtain an `Application ID` and an `Application Secret` key by clicking the `"Create Application"` button from your dashboard. You will be directed to the "View Application" page for the application you just created.

The `Application Secret` is visible to you only once during application creation. Save it somewhere because there's no way to retrieve it back. If you lost your secret create a new application and delete the old application.

You will use the `Application ID` and the `Application Secret` to authenticate with the Astronomy API with Basic Authentication.

You can view your `Application ID` later, by clicking the name of the specific application on the [dashboard](http://astronomyapi.com/dashboard).

{% hint style="info" %}
Be sure to set the `Origin` to the domain of the website when creating an application. If you're planning to use the API on a webpage. The API will respond with a `Access Allow Origin` header with the domain you provide.&#x20;

This is needed if you're calling the API from a web page client since web browsers need CORS setup for remote requests to work.
{% endhint %}

## Basic Authentication

When making API calls to endpoints requiring authentication, you must use the above credentials to create a string that must be used as the authentication string. The algorithm to create the string is very simple. Below are implementations of several commonly used languages.

#### JS

```typescript
const authString = btoa(`applicationId:applicationSecret`);
```

#### PHP

```php
$authString = base64_encode("applicationId:applicationSecret");
```

#### Python

```python
import base64
userpass = "applicationId:applicationSecret"
authString = base64.b64encode(userpass.encode()).decode()
```

The encrypted string must be provided in the API request's `Authorization` header, after the term `Basic` followed by a space.

```markup
"Authorization: Basic YourAuthStringHere"
```

In an event of an authentication failure, a `403 Forbidden` response will be returned, which probably means you encrypted the string incorrectly, or your credentials are wrong.

Successful requests always respond with HTTP code `200`.

### Sample curl request

```bash
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies' 
\ --header 'Authorization: Basic YourAuthStringHere' 
```

For code samples and demos go to [demo.astronomyapi.com](http://demo.astronomyapi.com)

Need help with something? or noticed a bug? [Please create a ticket on Github](https://github.com/AstronomyAPI/Samples/issues)
