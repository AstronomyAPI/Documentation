# Getting Started

Welcome to **Astronomy API**, a web API for retrieving astronomical information.

> This documentation is for the legacy API and will soon be deprecated. Please refer to the v2 api documentation at [https://docs.astronomyapi.com/v2](https://docs.astronomyapi.com/v2)

### Obtaining An Application ID and a Secret

To make API calls, you will first need to create an account. Go to the [Signup](http://astronomyapi.com/auth/signup) page to create your free account.

After creating an account, you must obtain an ID and a secret key by clicking the `"Create New Application"` button from your dashboard. You will be directed to the view application page for the application you just created.

You will use the `Application ID` and the `Application Secret` to authenticate the Astronomy API. You may create upto 10 applications per account.

You can view your `Application ID and the Secret` later, by clicking the `"View Application"` button for the specific application on the [dashboard](http://astronomyapi.com/dashboard).

> If you're using Javascript to make API calls make sure you enter the same domain you use to make requests, in to the `domain` field of the `"Create New Application"` form. Astronomy API responses sends a `Access-Control-Allow-Origin` header with the domain you entered preventing other websites from reusing your JWT.

### Authentication

```text
GET /auth?app_id=<app_id>&app_secret=<app_secret>
```

The Astronomy API is authenticated using a Json Web Token \(JWT\). You may learn more about JWT at [jwt.io](https://jwt.io).

To get your JWT do a `GET` request along with your `app_id` and the `app_secret`.

> You should never reveal the `app_secret` in your public source code. Others might use your application credentials and your daily API quota will exceed without you even knowing.
>
> It is recommended that you use a server side implementation to return the JWT for you. See the sample PHP code below.

_Sample Response_

```text
{
    "data": {
        "token": "some-really-long-string"
    }
}
```

When making API calls to endpoints which require JWT, you must submit the obtained token in your request headers.

Following the JWT specification, the header name must be `Authorization`. The header value will be the word `Bearer`, followed by a space and the `token` you obtained above. Notice the space between the word `Bearer` and the token.

_Sample in PHP_

```text
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
```

In an event of an authentication failure, a `400 Bad Request` will be sent to you. Make sure you check the response HTTP code before reading the JWT. Successful requests always send an HTTP code `200`.

```text
{
    "error": "Access denied",
    "message": "Invalid `app_id` or `app_secret`"
}
```

## Observer Parameters

Observer Parameters include the current observers location and other information.

\|\| **Parameter** \|\| **Required** \|\| **Description** \|\| \|\| lon \|\| Yes \|\| Longitude of the observer's location, as Float \|\| \|\| lat \|\| Yes \|\| Latitude of the observer's location, as Float \|\| \|\| el \|\| No \|\| Elevation from the sea in Meters as Number _\(not implemented\)_ \|\|

## Date Range Parameters

Date Range Parameters include the current date and time in UTC.

\|\| **Parameter** \|\| **Required** \|\| **Description** \|\| \|\| from\_year \|\| Yes \|\| Starting year, as Number \|\| \|\| from\_month \|\| Yes \|\| Starting month, as Number \|\| \|\| from\_day \|\| Yes \|\| Starting day, as Number \|\| \|\| to\_year \|\| Yes \|\| Ending year, as Number \|\| \|\| to\_month \|\| Yes \|\| Ending month, as Number \|\| \|\| to\_day \|\| Yes \|\| Ending day, as Number \|\| \|\| hour \|\| No \|\| Observing hour, as Number \|\| \|\| minute \|\| No \|\| Observing minute, as Number \|\|

`hour` and `minute` are optional. If not supplied will default to `00:00`

Maximum day span that could be requested from the API is seven days.

## Solar System Bodies

The Astronomy API supports the following Solar System bodies by their name. Certain API endpoints might require you to pass one or more of these Solar System bodies.

More will be added soon.

`sun`, `mercury`, `venus`, `moon`, `mars`, `jupiter`, `saturn`, `uranus`, `neptune`, `pluto`

### Body properties

#### distance

Distances to the body from both Sun and Earth are returned on this property, in Kilo Meters `(km)` and Astronomical Units `(au)`.

#### position

Position of the body is returned by the `constellation`, Altitude `alt` / Azimuth `az` pairs and in Right Accession `(ra)` / Declination `(dec)` pairs.

Note that `alt/az` values also contain literal string values and degree values while the `ra/dec` values contain degree and hour values.

## Tabular Responses

Certain API endpoints might return you data in a tabular format, thus making it easier for you to render them in your template files.

You can get the `table` object from response object using `data.table`.

```text
{
    "data": {
        "dates": {
            "from": "2016-12-20T00:00:00",
            "to": "2016-12-22T23:59:59"
        },
        "observer": {
            "geo": {
                "lat": "17.2",
                "lon": "70"
            }
        },
        "table": {
            .... table object
        }
    }
}
```

A typical `table` object response will include a `header` and `rows`. The `header` contains the column names, while the `rows` contains the row data.

Each row object consists of a `cells` array and an `entry` object. The `entry` is the label for current row. While cells are the values for the corresponding columns of the row.

For more information on how to render this type of data refer to the [samples repository](https://github.com/AstronomyAPI/Samples)

```text
{
    "header": [
        "Column 1",
        "Column 2"
    ],
    "rows": [
        {
            "cells": [
                {
                    .. Row 1, Col 1
                },
                {
                    .. Row 1, Col 2
                }
            ],
            "entry": {
                "id": "Row 1"
            }
        },
        {
            "cells": [
                {
                    .. Row 2, Col 1
                },
                {
                    .. Row 2, Col 2
                }
            ],
            "entry": {
                "id": "Row 2"
            }
        },
        {
            "cells": [
                {
                    .. Row 3, Col 1
                },
                {
                    .. Row 3, Col 2
                }
            ],
            "entry": {
                "id": "Row 3"
            }
        }
    ]
}
```

## Endpoints

### `POST` Positions

This endpoint will return the position of Solar System bodies for a given range of dates, for the given Earth coordinates.

```text
GET /positions
```

The following parameters are required to be sent in the request.

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v1/documentation/?id=observer-parameters/README.md)

[Date Range Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v1/documentation/?id=date-range-parameters/README.md)

_Sample Response_

```text
{
    "data": {
        "dates": {
            "from": "2016-12-20T00:00:00",
            "list": [
                "2016-12-20T00:00:00"
            ],
            "to": "2016-12-20T23:59:59"
        },
        "observer": {
            "geo": {
                "lat": "33.775867",
                "lon": "-84.39733"
            }
        },
        "rows": [
            {
                "columns": [
                    {
                        "date": "2016-12-20T00:00:00",
                        "dist": {
                            "earth": {
                                "au": 0.98382376714112019,
                                "km": 147177940.70836419
                            },
                            "sun": {
                                "au": 0,
                                "km": 0
                            }
                        },
                        "id": "sun",
                        "meta": {
                            "elong": 0,
                            "mag": -26.8,
                            "radi": 0.004601224197882966,
                            "sz": 1898.1412353515625
                        },
                        "name": "Sun",
                        "pos": {
                            "altaz": {
                                "alt": {
                                    "deg": -17.676677205653913,
                                    "str": "-17deg 40' 36.0\""
                                },
                                "az": {
                                    "deg": 253.20953205863395,
                                    "str": "253deg 12' 34.3\""
                                }
                            },
                            "const": {
                                "abbr": "Leo",
                                "id": "leo",
                                "name": "Leo"
                            },
                            "radec": {
                                "dec": {
                                    "deg": -23.427243017367854,
                                    "str": "-23deg 25' 38.1\""
                                },
                                "ra": {
                                    "hr": 17.875687472812032,
                                    "str": "17h 52m 32.47s"
                                }
                            }
                        }
                    }
                ],
                "id": "sun",
                "name": "Sun"
            },
            {
                "columns": [
                    {
                        "date": "2016-12-20T00:00:00",
                        "dist": {
                            "earth": {
                                "au": 0.79518336244444721,
                                "km": 118957737.83775564
                            },
                            "sun": {
                                "au": 0.4070223867893219,
                                "km": 60889682.39091436
                            }
                        },
                        "id": "mercury",
                        "meta": {
                            "elong": 0.12851867808223255,
                            "mag": 3.38,
                            "radi": 0.000026483396276688,
                            "sz": 10.925185203552246
                        },
                        "name": "Mercury",
                        "pos": {
                            "altaz": {
                                "alt": {
                                    "deg": -3.3902502011998239,
                                    "str": "-03deg 23' 24.9\""
                                },
                                "az": {
                                    "deg": 244.62816986540426,
                                    "str": "244deg 37' 41.4\""
                                }
                            },
                            "const": {
                                "abbr": "Sex",
                                "id": "sex",
                                "name": "Sextans"
                            },
                            "radec": {
                                "dec": {
                                    "deg": -22.885117161385157,
                                    "str": "-22deg 53' 06.4\""
                                },
                                "ra": {
                                    "hr": 19.077950188242596,
                                    "str": "19h 04m 40.62s"
                                }
                            }
                        }
                    }
                ],
                "id": "mercury",
                "name": "Mercury"
            }

            ...
            ...
            ...
            ...
            ...
            ...
        ]
    }
}
```

