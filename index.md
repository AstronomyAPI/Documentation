## Getting Started

Welcome to **Astronomy API**, a web API for retreiving astronomical information.

### Obtaining An Application ID and a Secret

To make API calls, you will first need to create an account. Go to the [Signup](/auth/signup) page to create your free account.

After creating an account, you must obtain an ID and a secret key by clicking the `"Create New Application"` button from your dashboard. You will be directed to the view application page for the application you just created. 

You will use the `Application ID` and the `Application Secret` to authenticate the Astronomy API. You may create upto 10 applications per account.

You can view your `Application ID and the Secret` later, by clicking the `"View Application"` button for the specific application on the [dashboard](/dashboard).

### Authentication

    GET /auth?app_id=<app_id>&app_secret=<app_secret>

The Astronomy API is authenticated using a Json Web Token (JWT). You may learn more about JWT at [jwt.io](https://jwt.io).

To get your JWT do a `GET` request along with your `app_id` and the `app_secret`. 

> You should never reveal the `app_secret` in your public source code. Others might use your application credentials and your daily API quota will exceed without you even knowing. 

> It is recommended that you use a server side implementation to return the JWT for you. See the sample PHP code below.

*Sample Response*

    {
        "data": {
            "token": "some-really-long-string"
        }
    }

When making API calls to endpoints which require JWT, you must submit the obtained token in your request headers. 

Following the JWT specification, the header name must be `Authorization`. The header value will be the word `Bearer`, followed by a space and the `token` you obtained above. Notice the space between the word `Bearer` and the token.


*Sample in PHP*


    $app_id = 'some-id';
    $app_secret = 'some-secret';

    $curl = curl_init();

    curl_setopt_array($curl, array(
    CURLOPT_URL => "http://api.astronomyapi.org/auth?app_id=$app_id&app_secret=$app_secret",
    CURLOPT_RETURNTRANSFER => true
    ));

    $response = curl_exec($curl);
    $err = curl_error($curl);

    curl_close($curl);

    if ($err) {
        echo "cURL Error #:" . $err;
    } else {
        $response = json_decode($response);

        print_r($response);
    }

In an event of an authentication failure, a `400 Bad Request` will be sent to you. Make sure you check the response HTTP code before reading the JWT. Successful requests always send an HTTP code `200`.

    {
        "error": "Access denied",
        "message": "Invalid `app_id` or `app_secret`"
    }