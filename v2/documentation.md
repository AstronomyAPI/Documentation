# README

## Getting Started

Welcome to **Astronomy API**, a web API for retrieving astronomical information.

### Obtaining An Application ID and a Secret

To make API calls, you will first need to create an account. Go to the [Signup](http://astronomyapi.com/auth/signup) page to create your free account.

After creating an account, you must obtain an `Application ID` and an `Application Secret` key by clicking the `"Create Application"` button from your dashboard. You will be directed to the view application page for the application you just created.

The `Application Secret` is visible to you only once during application creation. Write it down somewhere because there's no way to retrive it back.

You will use the `Application ID` and the `Application Secret` to authenticate the Astronomy API with Basic Authentication.

You can view your `Application ID` later, by clicking the name of the specific application on the [dashboard](http://astronomyapi.com/dashboard).

> If you're using Javascript to make API calls make sure you enter the same domain you use to make requests, in to the `domain` field of the `"Create New Application"` form. Astronomy API responses sends a `Access-Control-Allow-Origin` header with the domain you entered preventing other websites from reusing your JWT.

### Basic Authentication

When making API calls to endpoints which require authentication, you must use the credentials obtained above to create a hash. The algotithem to create the hash is very simple. Below is the implementation in PHP.

`$hash = base64_encode("$applicationId:$applicationSecret");`

The generated hash must be provided in the API request's `Authorization` header, after the term `Basic` followed by a space.

`'Authorization: Basic <hash>'`

In an event of an authentication failure, a `403 Forbidden` response will be sent to you. Successful requests always respond an HTTP code `200`.

### Sample curl request

`curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies' \ --header 'Authorization: Basic <hash>' \\`

## Observer Parameters

Observer Parameters include the current observers location and other information.

| **Parameter** | **Required** | **Description** |
| :--- | :---: | :--- |
| longitude | Yes | Longitude of the observer's location, as Float |
| latitude | Yes | Latitude of the observer's location, as Float |
| elevation | Yes | Elevation from the sea in Meters as Number |
| from\_date | Yes | Starting date as Date |
| to\_date | Yes | Ending date as Date |
| time | Yes | Observer's time as Time |

Maximum day span that could be requested from the API is 30 days.

### Body properties

| **Section** | **Sub Section** | **Description** |
| :--- | :--- | :--- |
| id |  | Unique identified for the body |
| name |  | User friendly name for the body |
| distance |  | Distance object |
|  | fromEarth | Distance from Earth in Kilometers \(km\) and Astronomical units \(au\) |
| position |  | Position object |
|  | horizonal | Position object in horizonal cordinates. Object will return the values in Altitude and Azimuth \(Alt/Az\) format. Numerical and literal values are returned. |
|  | equatorial | Position object in equatorial cordinates. Object will return the values in Right Ascension and Declination \(RA/Dec\) format. Numerical and literal values are returned. |
| extraInfo |  | Other information relating to the body |
|  | elongation | Angular separation between the Sun and the planet, with Earth as the reference point |
|  | magnitude | Apparent magnitude of the object |

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
            "location": {
                "longitude": -84.39733,
                "latitude": 33.775867,
                "elevation": 1000
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

### GET /api/v2/bodies

Returns a list of bodies available to be queried with.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies' \
--header 'Authorization: Basic xxx'
```

_Sample Response_

```text
{
    "data": {
        "bodies": [
            "sun",
            "moon",
            "mercury",
            "venus",
            "earth",
            "mars",
            "jupiter",
            "saturn",
            "uranus",
            "neptune",
            "pluto"
        ]
    }
}
```

### GET /api/v2/bodies/positions

Returns a iteratable list of bodies and their properties in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

_Sample Response_

[Download sample response as a json file](https://docs.astronomyapi/v2/positions.response.json)

```text
{
    "data": {
        "dates": {
            "from": "2017-12-20T08:00:00.000Z",
            "to": "2017-12-21T08:00:00.000Z"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 33.775867,
                "elevation": 1000
            }
        },
        "table": {
            "header": [
                "2017-12-20T08:00:00.000Z",
                "2017-12-21T08:00:00.000Z"
            ],
            "rows": [
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98389",
                                    "km": "147187925.46926"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-56.53",
                                        "string": "-57&deg; 28' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "81.48",
                                        "string": "81&deg; 28' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.88",
                                        "string": "17h 52m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-23.43",
                                        "string": "-24&deg; 34' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "0.00000",
                                "magnitude": "-26.77747"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98382",
                                    "km": "147177087.08537"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-56.64",
                                        "string": "-57&deg; 21' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "81.40",
                                        "string": "81&deg; 24' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.96",
                                        "string": "17h 57m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-23.44",
                                        "string": "-24&deg; 33' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "0.00000",
                                "magnitude": "-26.77763"
                            }
                        }
                    ],
                    "entry": {
                        "id": "sun",
                        "name": "Sun"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00275",
                                    "km": "412114.48291"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-72.21",
                                        "string": "-73&deg; 47' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "41.29",
                                        "string": "41&deg; 17' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.48",
                                        "string": "19h 28m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-19.93",
                                        "string": "-20&deg; 4' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "22.37099",
                                "magnitude": "-6.07891"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00275",
                                    "km": "410944.40618"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-74.74",
                                        "string": "-75&deg; 15' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "3.44",
                                        "string": "3&deg; 26' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.30",
                                        "string": "20h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-18.71",
                                        "string": "-19&deg; 17' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "33.09721",
                                "magnitude": "-6.97202"
                            }
                        }
                    ],
                    "entry": {
                        "id": "moon",
                        "name": "Moon"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.75157",
                                    "km": "112433078.69683"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-41.52",
                                        "string": "-42&deg; 28' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "86.56",
                                        "string": "86&deg; 33' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.83",
                                        "string": "16h 49m 47s"
                                    },
                                    "declination": {
                                        "degrees": "-19.47",
                                        "string": "-20&deg; 31' 48\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "15.25952",
                                "magnitude": "1.00756"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.77038",
                                    "km": "115247907.67492"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-40.32",
                                        "string": "-41&deg; 40' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "87.31",
                                        "string": "87&deg; 18' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.80",
                                        "string": "16h 48m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-19.41",
                                        "string": "-20&deg; 35' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "16.64391",
                                "magnitude": "0.68517"
                            }
                        }
                    ],
                    "entry": {
                        "id": "mercury",
                        "name": "Mercury"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.70202",
                                    "km": "254618023.28841"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-52.15",
                                        "string": "-53&deg; 51' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "84.91",
                                        "string": "84&deg; 54' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.53",
                                        "string": "17h 31m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-23.30",
                                        "string": "-24&deg; 42' 0\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "4.78113",
                                "magnitude": "-3.94087"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.70284",
                                    "km": "254741984.41192"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-52.51",
                                        "string": "-53&deg; 29' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "84.80",
                                        "string": "84&deg; 48' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.63",
                                        "string": "17h 37m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-23.39",
                                        "string": "-24&deg; 36' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "4.54120",
                                "magnitude": "-3.94309"
                            }
                        }
                    ],
                    "entry": {
                        "id": "venus",
                        "name": "Venus"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6372.56539"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.82",
                                        "string": "-90&deg; 10' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0&deg; 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.29",
                                        "string": "20h 17m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-33.66",
                                        "string": "-34&deg; 20' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6372.56539"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.82",
                                        "string": "-90&deg; 10' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0&deg; 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.36",
                                        "string": "20h 21m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-33.66",
                                        "string": "-34&deg; 20' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        }
                    ],
                    "entry": {
                        "id": "earth",
                        "name": "Earth"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "2.05555",
                                    "km": "307505325.23151"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-6.66",
                                        "string": "-7&deg; 20' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "100.68",
                                        "string": "100&deg; 40' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "14.31",
                                        "string": "14h 18m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-12.81",
                                        "string": "-13&deg; 11' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "51.75344",
                                "magnitude": "1.56828"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "2.04720",
                                    "km": "306257345.70992"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-6.46",
                                        "string": "-7&deg; 32' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "101.06",
                                        "string": "101&deg; 3' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "14.35",
                                        "string": "14h 21m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-13.02",
                                        "string": "-14&deg; 58' 48\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "52.14559",
                                "magnitude": "1.56132"
                            }
                        }
                    ],
                    "entry": {
                        "id": "mars",
                        "name": "Mars"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "6.10221",
                                    "km": "912877259.73281"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-14.44",
                                        "string": "-15&deg; 33' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "98.61",
                                        "string": "98&deg; 36' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "14.83",
                                        "string": "14h 49m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-15.23",
                                        "string": "-16&deg; 46' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "43.76662",
                                "magnitude": "-1.76112"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "6.09074",
                                    "km": "911161947.76374"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-13.80",
                                        "string": "-14&deg; 12' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "99.08",
                                        "string": "99&deg; 4' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "14.84",
                                        "string": "14h 50m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-15.29",
                                        "string": "-16&deg; 42' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "44.59994",
                                "magnitude": "-1.76472"
                            }
                        }
                    ],
                    "entry": {
                        "id": "jupiter",
                        "name": "Jupiter"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "11.04833",
                                    "km": "1652807114.58763"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-57.37",
                                        "string": "-58&deg; 37' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "78.82",
                                        "string": "78&deg; 49' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.98",
                                        "string": "17h 58m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-22.53",
                                        "string": "-23&deg; 28' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "1.66392",
                                "magnitude": "0.31200"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "11.04858",
                                    "km": "1652843517.48672"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-56.66",
                                        "string": "-57&deg; 20' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "79.51",
                                        "string": "79&deg; 30' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.99",
                                        "string": "17h 59m 23s"
                                    },
                                    "declination": {
                                        "degrees": "-22.53",
                                        "string": "-23&deg; 28' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "1.03303",
                                "magnitude": "0.30957"
                            }
                        }
                    ],
                    "entry": {
                        "id": "saturn",
                        "name": "Saturn"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.45055",
                                    "km": "2909760992.86026"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-3.90",
                                        "string": "-4&deg; 6' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "284.00",
                                        "string": "284&deg; 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.52",
                                        "string": "01h 31m 12s"
                                    },
                                    "declination": {
                                        "degrees": "8.92",
                                        "string": "8&deg; 55' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "116.02352",
                                "magnitude": "5.75586"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.46607",
                                    "km": "2912083336.54165"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-4.71",
                                        "string": "-5&deg; 17' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "284.56",
                                        "string": "284&deg; 33' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.52",
                                        "string": "01h 31m 12s"
                                    },
                                    "declination": {
                                        "degrees": "8.92",
                                        "string": "8&deg; 55' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "114.99407",
                                "magnitude": "5.75764"
                            }
                        }
                    ],
                    "entry": {
                        "id": "uranus",
                        "name": "Uranus"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.21454",
                                    "km": "4520031473.15350"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-45.68",
                                        "string": "-46&deg; 19' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "296.81",
                                        "string": "296&deg; 48' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "22.88",
                                        "string": "22h 52m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-8.12",
                                        "string": "-9&deg; 52' 48\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "73.06986",
                                "magnitude": "7.91295"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.23110",
                                    "km": "4522508746.20495"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-46.40",
                                        "string": "-47&deg; 36' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "297.74",
                                        "string": "297&deg; 44' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "22.88",
                                        "string": "22h 52m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-8.11",
                                        "string": "-9&deg; 53' 24\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "72.06740",
                                "magnitude": "7.91414"
                            }
                        }
                    ],
                    "entry": {
                        "id": "neptune",
                        "name": "Neptune"
                    }
                },
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "34.39136",
                                    "km": "5144874671.76098"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-72.06",
                                        "string": "-73&deg; 56' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "51.14",
                                        "string": "51&deg; 8' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.31",
                                        "string": "19h 18m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-21.74",
                                        "string": "-22&deg; 15' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "19.77312",
                                "magnitude": "14.32829"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "34.39774",
                                    "km": "5145828126.09192"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-71.43",
                                        "string": "-72&deg; 34' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "53.14",
                                        "string": "53&deg; 8' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.31",
                                        "string": "19h 18m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-21.74",
                                        "string": "-22&deg; 15' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "18.78735",
                                "magnitude": "14.32764"
                            }
                        }
                    ],
                    "entry": {
                        "id": "pluto",
                        "name": "Pluto"
                    }
                }
            ]
        }
    }
}
```

### GET /api/v2/bodies/positions/sun

Returns properties of the sun for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/sun?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

_Sample Response_

```text
{
    "data": {
        "dates": {
            "from": "2017-12-20T08:00:00.000Z",
            "to": "2017-12-21T08:00:00.000Z"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 33.775867,
                "elevation": 1000
            }
        },
        "table": {
            "header": [
                "2017-12-20T08:00:00.000Z",
                "2017-12-21T08:00:00.000Z"
            ],
            "rows": [
                {
                    "cells": [
                        {
                            "date": "2017-12-20T08:00:00.000Z",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98389",
                                    "km": "147187925.46926"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-56.53",
                                        "string": "-57&deg; 28' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "81.48",
                                        "string": "81&deg; 28' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.88",
                                        "string": "17h 52m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-23.43",
                                        "string": "-24&deg; 34' 12\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "0.00000",
                                "magnitude": "-26.77747"
                            }
                        },
                        {
                            "date": "2017-12-21T08:00:00.000Z",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98382",
                                    "km": "147177087.08537"
                                }
                            },
                            "position": {
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-56.64",
                                        "string": "-57&deg; 21' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "81.40",
                                        "string": "81&deg; 24' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.96",
                                        "string": "17h 57m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-23.44",
                                        "string": "-24&deg; 33' 36\""
                                    }
                                }
                            },
                            "extraInfo": {
                                "elongation": "0.00000",
                                "magnitude": "-26.77763"
                            }
                        }
                    ],
                    "entry": {
                        "id": "sun",
                        "name": "Sun"
                    }
                }
            ]
        }
    }
}
```

### GET /api/v2/bodies/positions/moon

Returns properties of the Moon for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/moon?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/mercury

Returns properties of Mercury for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/mercury?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/venus

Returns properties of Venus for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/venus?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/mars

Returns properties of Mars for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/mars?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/jupiter

Returns properties of Jupiter for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/jupiter?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/saturn

Returns properties of Saturn for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/saturn?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/uranus

Returns properties of Uranus for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/uranus?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/neptune

Returns properties of Neptune for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters.

_Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/neptune?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

### GET /api/v2/bodies/positions/pluto

Returns properties of Pluto for the given date range in tabular format.

_Query Params_

[Observer Parameters](https://github.com/AstronomyAPI/Documentation/tree/735adb1fd6df1a243a83750ee1f39c36de64d3a0/v2/documentation/?id=observer-parameters/README.md) must be passed as query parameters. _Sample Request_

```text
curl --location --request GET 'https://api.astronomyapi.com/api/v2/bodies/positions/pluto?latitude=33.775867&longitude=-84.39733&elevation=1000&from_date=2017-12-20&to_date=2017-12-21&time=08:00:00' \
--header 'Authorization: Basic xxx'
```

