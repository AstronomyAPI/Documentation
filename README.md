# Getting Started

Welcome to **Astronomy API**, a web API for retrieving astronomical information.

## Obtaining An Application ID and a Secret

To make API calls, you will first need to create an account. Go to the [Signup](http://astronomyapi.com/auth/signup) page to create your free account.

After creating an account, you must obtain an `Application ID` and an `Application Secret` key by clicking the `"Create Application"` button from your dashboard. You will be directed to the view application page for the application you just created.

The `Application Secret` is visible to you only once during application creation. Write it down somewhere because there's no way to retrieve it back.

You will use the `Application ID` and the `Application Secret` to authenticate the Astronomy API with Basic Authentication.

You can view your `Application ID` later, by clicking the name of the specific application on the [dashboard](http://astronomyapi.com/dashboard).

{% hint style="info" %}
Be sure to set the O`rigin` to the domain of the website when creating an application. If you're planning to use the API on a webpage. The API will respond with a `Access Allow Origin` header with the domain you provide. 
{% endhint %}

## Basic Authentication

When making API calls to endpoints which require authentication, you must use the credentials obtained above to create a hash. The algorithm to create the hash is very simple. Below are implementations on several commonly used languages.

#### JS

```typescript
const hash = btoa(`${applicationId}:${applicationSecret}`);
```

#### PHP

```php
$hash = base64_encode("$applicationId:$applicationSecret");
```

The generated hash must be provided in the API request's `Authorization` header, after the term `Basic` followed by a space.

```text
'Authorization: Basic <hash>'
```

In an event of an authentication failure, a `403 Forbidden` response will be returned to you. Successful requests always respond an HTTP code `200`.

### Sample curl request

```bash
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies' \ --header 'Authorization: Basic <hash>' \\
```

