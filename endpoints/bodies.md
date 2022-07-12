---
description: >-
  Get Planets, Sun and Moon positions for given latitude, longitude and
  date/time.
---

# Bodies

Bodies API could be used to get information about the planets, the sun and the moon. Most endpoints are GET requests are will require you to submit [observer parameters](../requests-and-response/observer-parameters.md) as query parameters.

See [body properties](../requests-and-response/body-properties.md) for available properties for bodies.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/bodies" method="get" summary="Get available bodies" %}
{% swagger-description %}
Returns a list of bodies available to be queried with.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-response status="200" description="Cake successfully retrieved." %}
```
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/bodies/positions" method="get" summary="Get all bodies positions" %}
{% swagger-description %}
Returns a iterable list of bodies and their properties in tabular format. 
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-parameter in="query" name="latitude" type="string" %}
Latitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="longitude" type="string" %}
Longitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="elevation" type="string" %}
Elevation from the sea in Meters
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from_date" type="string" %}
Starting date as Date. 
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to_date" type="string" %}
Ending date as Date
{% endswagger-parameter %}

{% swagger-parameter in="query" name="time" type="string" %}
Observer's time as Time
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/bodies/positions/:body" method="get" summary="Get body positions" %}
{% swagger-description %}
Returns properties of the given body for the given date range in tabular format.
{% endswagger-description %}

{% swagger-parameter in="path" name="body" type="string" %}
ID of the body
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-parameter in="query" name="latitude" type="string" %}
Latitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="longitude" type="string" %}
Longitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="elevation" type="string" %}
Elevation from the sea in Meters
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from_date" type="string" %}
Starting date as Date.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to_date" type="string" %}
Ending date as Date
{% endswagger-parameter %}

{% swagger-parameter in="query" name="time" type="string" %}
Observer's time as Time
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
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
{% endswagger-response %}
{% endswagger %}
