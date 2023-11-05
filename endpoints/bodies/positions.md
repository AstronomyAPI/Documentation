---
description: Celestial body positions API
---

# 🌐 Positions

Positions API can return position for a single body or all available bodies. This is useful if you don't want to make multiple requests for each body, and don't want to get throttled by the API request limitations.&#x20;

See [Body Properties](../../requests-and-response/body-properties.md) for the available properties of bodies.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/bodies/positions" method="get" summary="Get all bodies positions" %}
{% swagger-description %}
Returns an iterable list of bodies and their properties in tabular format.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic
{% endswagger-parameter %}

{% swagger-parameter in="query" name="latitude" type="string" required="true" %}
Latitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="longitude" type="string" required="true" %}
Longitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="elevation" type="string" required="true" %}
Elevation from the sea in Meters
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from_date" type="string" required="true" %}
Starting date as Date. The maximum number of days you can query is 366 days.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to_date" type="string" required="true" %}
Ending date as Date. The maximum number of days you can query is 366 days.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="time" type="string" required="true" %}
Observer's time as Time
{% endswagger-parameter %}

{% swagger-parameter in="query" name="output" type="string" required="false" %}
Output format.

`rows`

or

`table`

. Default is

`table`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "data": {
        "dates": {
            "from": "2020-12-20T09:00:00.000-05:00",
            "to": "2020-12-23T09:00:00.000-05:00"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 38.775867,
                "elevation": 0
            }
        },
        "table": {
            "header": [
                "2020-12-20T09:00:00.000-05:00",
                "2020-12-21T09:00:00.000-05:00",
                "2020-12-22T09:00:00.000-05:00",
                "2020-12-23T09:00:00.000-05:00"
            ],
            "rows": [
                {
                    "entry": {
                        "id": "sun",
                        "name": "Sun"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98378",
                                    "km": "147171382.76144"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "10.04",
                                        "string": "10° 2' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.21",
                                        "string": "131° 12' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "10.04",
                                        "string": "10° 2' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.21",
                                        "string": "131° 12' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.92",
                                        "string": "17h 55m 12s"
                                    },
                                    "declination": {
                                        "degrees": "-23.43",
                                        "string": "-24° 34' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 0,
                                "magnitude": -26.77762
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98371",
                                    "km": "147160312.87067"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "9.96",
                                        "string": "9° 57' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.13",
                                        "string": "131° 7' 48\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "9.96",
                                        "string": "9° 57' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.13",
                                        "string": "131° 7' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.99",
                                        "string": "17h 59m 23s"
                                    },
                                    "declination": {
                                        "degrees": "-23.44",
                                        "string": "-24° 33' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 0,
                                "magnitude": -26.77778
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98364",
                                    "km": "147149972.87077"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "9.90",
                                        "string": "9° 54' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.03",
                                        "string": "131° 1' 48\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "9.90",
                                        "string": "9° 54' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.03",
                                        "string": "131° 1' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "18.07",
                                        "string": "18h 04m 12s"
                                    },
                                    "declination": {
                                        "degrees": "-23.44",
                                        "string": "-24° 33' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 0,
                                "magnitude": -26.77794
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "sun",
                            "name": "Sun",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.98357",
                                    "km": "147140401.77424"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "9.83",
                                        "string": "9° 49' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "130.94",
                                        "string": "130° 56' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "9.83",
                                        "string": "9° 49' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "130.94",
                                        "string": "130° 56' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "18.14",
                                        "string": "18h 08m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-23.42",
                                        "string": "-24° 34' 48\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 0,
                                "magnitude": -26.77808
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "moon",
                        "name": "Moon"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00267",
                                    "km": "398770.33841"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-39.40",
                                        "string": "-40° 36' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "70.99",
                                        "string": "70° 59' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-39.40",
                                        "string": "-40° 36' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "70.99",
                                        "string": "70° 59' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.13",
                                        "string": "23h 07m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-11.96",
                                        "string": "-12° 2' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 74.27557,
                                "magnitude": -9.45722,
                                "phase": {
                                    "angel": "74.2018",
                                    "fraction": "0.042",
                                    "string": "Waxing Crescent"
                                }
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00270",
                                    "km": "403433.20005"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-43.26",
                                        "string": "-44° 44' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "56.79",
                                        "string": "56° 47' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-43.26",
                                        "string": "-44° 44' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "56.79",
                                        "string": "56° 47' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.89",
                                        "string": "23h 53m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-7.15",
                                        "string": "-8° 51' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 85.52956,
                                "magnitude": -9.90583,
                                "phase": {
                                    "angel": "85.5048",
                                    "fraction": "0.036",
                                    "string": "Waxing Crescent"
                                }
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00272",
                                    "km": "406803.88243"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-45.10",
                                        "string": "-46° 54' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "41.52",
                                        "string": "41° 31' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-45.10",
                                        "string": "-46° 54' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "41.52",
                                        "string": "41° 31' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "0.61",
                                        "string": "00h 36m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-2.20",
                                        "string": "-3° 48' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "cet",
                                    "short": "Cet",
                                    "name": "Cetus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 96.54755,
                                "magnitude": -10.29789,
                                "phase": {
                                    "angel": "96.5672",
                                    "fraction": "0.030",
                                    "string": "Waxing Gibbous"
                                }
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "moon",
                            "name": "Moon",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00273",
                                    "km": "408768.63964"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-44.84",
                                        "string": "-45° 9' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "26.04",
                                        "string": "26° 2' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-44.84",
                                        "string": "-45° 9' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "26.04",
                                        "string": "26° 2' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.32",
                                        "string": "01h 19m 12s"
                                    },
                                    "declination": {
                                        "degrees": "2.74",
                                        "string": "2° 44' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "psc",
                                    "short": "Psc",
                                    "name": "Pisces"
                                }
                            },
                            "extraInfo": {
                                "elongation": 107.41558,
                                "magnitude": -10.65118,
                                "phase": {
                                    "angel": "107.4676",
                                    "fraction": "0.023",
                                    "string": "Waxing Gibbous"
                                }
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "mercury",
                        "name": "Mercury"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.44663",
                                    "km": "216412357.18070"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "8.75",
                                        "string": "8° 45' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.99",
                                        "string": "131° 59' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "8.75",
                                        "string": "8° 45' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.99",
                                        "string": "131° 59' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "17.93",
                                        "string": "17h 55m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-24.92",
                                        "string": "-25° 4' 48\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 1.50745,
                                "magnitude": -1.31155
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.44477",
                                    "km": "216134837.46619"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "8.26",
                                        "string": "8° 15' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.50",
                                        "string": "131° 30' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "8.26",
                                        "string": "8° 15' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.50",
                                        "string": "131° 30' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "18.05",
                                        "string": "18h 03m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-25.00",
                                        "string": "-25° 0' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 1.76363,
                                "magnitude": -1.29482
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.44234",
                                    "km": "215771107.43777"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "7.78",
                                        "string": "7° 46' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.00",
                                        "string": "131° 0' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "7.78",
                                        "string": "7° 46' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "131.00",
                                        "string": "131° 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "18.17",
                                        "string": "18h 10m 12s"
                                    },
                                    "declination": {
                                        "degrees": "-25.06",
                                        "string": "-26° 56' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 2.14413,
                                "magnitude": -1.26822
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "mercury",
                            "name": "Mercury",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.43933",
                                    "km": "215320384.16055"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "7.30",
                                        "string": "7° 18' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "130.49",
                                        "string": "130° 29' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "7.30",
                                        "string": "7° 18' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "130.49",
                                        "string": "130° 29' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "18.29",
                                        "string": "18h 17m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-25.09",
                                        "string": "-26° 54' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 2.59661,
                                "magnitude": -1.23712
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "venus",
                        "name": "Venus"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.51668",
                                    "km": "226892479.91564"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "24.97",
                                        "string": "24° 58' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.65",
                                        "string": "149° 39' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "24.97",
                                        "string": "24° 58' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.65",
                                        "string": "149° 39' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.28",
                                        "string": "16h 16m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-20.19",
                                        "string": "-21° 48' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sco",
                                    "short": "Sco",
                                    "name": "Scorpius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 23.0487,
                                "magnitude": -3.87581
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.52066",
                                    "km": "227487606.29970"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "24.62",
                                        "string": "24° 37' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.46",
                                        "string": "149° 27' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "24.62",
                                        "string": "24° 37' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.46",
                                        "string": "149° 27' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.36",
                                        "string": "16h 21m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-20.44",
                                        "string": "-21° 33' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sco",
                                    "short": "Sco",
                                    "name": "Scorpius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 22.81549,
                                "magnitude": -3.8748
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.52460",
                                    "km": "228077053.65050"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "24.28",
                                        "string": "24° 16' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.26",
                                        "string": "149° 15' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "24.28",
                                        "string": "24° 16' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.26",
                                        "string": "149° 15' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.45",
                                        "string": "16h 27m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-20.68",
                                        "string": "-21° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "oph",
                                    "short": "Oph",
                                    "name": "Ophiuchus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 22.58214,
                                "magnitude": -3.87383
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "venus",
                            "name": "Venus",
                            "distance": {
                                "fromEarth": {
                                    "au": "1.52850",
                                    "km": "228660857.21992"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "23.94",
                                        "string": "23° 56' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.06",
                                        "string": "149° 3' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "23.94",
                                        "string": "23° 56' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "149.06",
                                        "string": "149° 3' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "16.54",
                                        "string": "16h 32m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-20.91",
                                        "string": "-21° 5' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "oph",
                                    "short": "Oph",
                                    "name": "Ophiuchus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 22.34865,
                                "magnitude": -3.87289
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "earth",
                        "name": "Earth"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6369.79183"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "360.00",
                                        "string": "360° 0' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "360.00",
                                        "string": "360° 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.33",
                                        "string": "02h 19m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-38.68",
                                        "string": "-39° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "for",
                                    "short": "For",
                                    "name": "Fornax"
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6369.79183"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.40",
                                        "string": "02h 24m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-38.68",
                                        "string": "-39° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "for",
                                    "short": "For",
                                    "name": "Fornax"
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6369.79183"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.47",
                                        "string": "02h 28m 12s"
                                    },
                                    "declination": {
                                        "degrees": "-38.68",
                                        "string": "-39° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "for",
                                    "short": "For",
                                    "name": "Fornax"
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "earth",
                            "name": "Earth",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.00004",
                                    "km": "6369.79183"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-89.81",
                                        "string": "-90° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.00",
                                        "string": "0° 0' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.53",
                                        "string": "02h 31m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-38.68",
                                        "string": "-39° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "for",
                                    "short": "For",
                                    "name": "Fornax"
                                }
                            },
                            "extraInfo": {
                                "elongation": null,
                                "magnitude": null
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "mars",
                        "name": "Mars"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.79790",
                                    "km": "119363666.52216"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-39.61",
                                        "string": "-40° 23' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "18.64",
                                        "string": "18° 38' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-39.61",
                                        "string": "-40° 23' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "18.64",
                                        "string": "18° 38' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.37",
                                        "string": "01h 22m 12s"
                                    },
                                    "declination": {
                                        "degrees": "9.31",
                                        "string": "9° 18' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "psc",
                                    "short": "Psc",
                                    "name": "Pisces"
                                }
                            },
                            "extraInfo": {
                                "elongation": 113.62223,
                                "magnitude": -0.54426
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.80648",
                                    "km": "120648034.74665"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-39.29",
                                        "string": "-40° 42' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "19.39",
                                        "string": "19° 23' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-39.29",
                                        "string": "-40° 42' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "19.39",
                                        "string": "19° 23' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.39",
                                        "string": "01h 23m 24s"
                                    },
                                    "declination": {
                                        "degrees": "9.48",
                                        "string": "9° 28' 48\""
                                    }
                                },
                                "constellation": {
                                    "id": "psc",
                                    "short": "Psc",
                                    "name": "Pisces"
                                }
                            },
                            "extraInfo": {
                                "elongation": 112.97481,
                                "magnitude": -0.5164
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.81512",
                                    "km": "121939469.90072"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-38.96",
                                        "string": "-39° 2' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "20.12",
                                        "string": "20° 7' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-38.96",
                                        "string": "-39° 2' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "20.12",
                                        "string": "20° 7' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.42",
                                        "string": "01h 25m 12s"
                                    },
                                    "declination": {
                                        "degrees": "9.64",
                                        "string": "9° 38' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "psc",
                                    "short": "Psc",
                                    "name": "Pisces"
                                }
                            },
                            "extraInfo": {
                                "elongation": 112.33371,
                                "magnitude": -0.48879
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "mars",
                            "name": "Mars",
                            "distance": {
                                "fromEarth": {
                                    "au": "0.82379",
                                    "km": "123237773.30768"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-38.63",
                                        "string": "-39° 22' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "20.84",
                                        "string": "20° 50' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-38.63",
                                        "string": "-39° 22' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "20.84",
                                        "string": "20° 50' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "1.44",
                                        "string": "01h 26m 24s"
                                    },
                                    "declination": {
                                        "degrees": "9.80",
                                        "string": "9° 48' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "psc",
                                    "short": "Psc",
                                    "name": "Pisces"
                                }
                            },
                            "extraInfo": {
                                "elongation": 111.69878,
                                "magnitude": -0.4614
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "jupiter",
                        "name": "Jupiter"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "5.91663",
                                    "km": "885114784.19947"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-10.13",
                                        "string": "-11° 52' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "107.86",
                                        "string": "107° 51' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-10.13",
                                        "string": "-11° 52' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "107.86",
                                        "string": "107° 51' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.15",
                                        "string": "20h 09m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-20.63",
                                        "string": "-21° 22' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 31.08024,
                                "magnitude": -1.97323
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "5.92439",
                                    "km": "886276755.73005"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-9.54",
                                        "string": "-10° 27' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.27",
                                        "string": "108° 16' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-9.54",
                                        "string": "-10° 27' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.27",
                                        "string": "108° 16' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.16",
                                        "string": "20h 09m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-20.58",
                                        "string": "-21° 25' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 30.2815,
                                "magnitude": -1.9712
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "5.93197",
                                    "km": "887410474.10824"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-8.95",
                                        "string": "-9° 3' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.67",
                                        "string": "108° 40' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-8.95",
                                        "string": "-9° 3' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.67",
                                        "string": "108° 40' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.18",
                                        "string": "20h 10m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-20.54",
                                        "string": "-21° 27' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 29.48361,
                                "magnitude": -1.96924
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "jupiter",
                            "name": "Jupiter",
                            "distance": {
                                "fromEarth": {
                                    "au": "5.93936",
                                    "km": "888515777.34535"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-8.36",
                                        "string": "-9° 38' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "109.07",
                                        "string": "109° 4' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-8.36",
                                        "string": "-9° 38' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "109.07",
                                        "string": "109° 4' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.19",
                                        "string": "20h 11m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-20.49",
                                        "string": "-21° 30' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 28.68655,
                                "magnitude": -1.96736
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "saturn",
                        "name": "Saturn"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "10.81706",
                                    "km": "1618209125.72204"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-10.14",
                                        "string": "-11° 51' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "107.69",
                                        "string": "107° 41' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-10.14",
                                        "string": "-11° 51' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "107.69",
                                        "string": "107° 41' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.16",
                                        "string": "20h 09m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-20.50",
                                        "string": "-21° 30' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 31.21146,
                                "magnitude": 0.511
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "10.82553",
                                    "km": "1619475828.82418"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-9.47",
                                        "string": "-10° 31' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.19",
                                        "string": "108° 11' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-9.47",
                                        "string": "-10° 31' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.19",
                                        "string": "108° 11' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.16",
                                        "string": "20h 09m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-20.48",
                                        "string": "-21° 31' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 30.30092,
                                "magnitude": 0.51024
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "10.83377",
                                    "km": "1620708246.11400"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-8.81",
                                        "string": "-9° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.68",
                                        "string": "108° 40' 48\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-8.81",
                                        "string": "-9° 11' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "108.68",
                                        "string": "108° 40' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.17",
                                        "string": "20h 10m 12s"
                                    },
                                    "declination": {
                                        "degrees": "-20.46",
                                        "string": "-21° 32' 24\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 29.39097,
                                "magnitude": 0.5094
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "saturn",
                            "name": "Saturn",
                            "distance": {
                                "fromEarth": {
                                    "au": "10.84177",
                                    "km": "1621906121.81073"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-8.15",
                                        "string": "-9° 51' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "109.17",
                                        "string": "109° 10' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-8.15",
                                        "string": "-9° 51' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "109.17",
                                        "string": "109° 10' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "20.18",
                                        "string": "20h 10m 48s"
                                    },
                                    "declination": {
                                        "degrees": "-20.44",
                                        "string": "-21° 33' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "cap",
                                    "short": "Cap",
                                    "name": "Capricornus"
                                }
                            },
                            "extraInfo": {
                                "elongation": 28.48161,
                                "magnitude": 0.5085
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "uranus",
                        "name": "Uranus"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.15312",
                                    "km": "2865265539.77370"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-37.43",
                                        "string": "-38° 34' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.51",
                                        "string": "0° 30' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-37.43",
                                        "string": "-38° 34' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "0.51",
                                        "string": "0° 30' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.30",
                                        "string": "02h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "13.32",
                                        "string": "13° 19' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "ari",
                                    "short": "Ari",
                                    "name": "Aries"
                                }
                            },
                            "extraInfo": {
                                "elongation": 127.83315,
                                "magnitude": 5.70738
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.16677",
                                    "km": "2867307491.50676"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-37.42",
                                        "string": "-38° 34' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "1.75",
                                        "string": "1° 45' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-37.42",
                                        "string": "-38° 34' 48\""
                                    },
                                    "azimuth": {
                                        "degrees": "1.75",
                                        "string": "1° 45' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.30",
                                        "string": "02h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "13.31",
                                        "string": "13° 18' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "ari",
                                    "short": "Ari",
                                    "name": "Aries"
                                }
                            },
                            "extraInfo": {
                                "elongation": 126.79454,
                                "magnitude": 5.70899
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.18060",
                                    "km": "2869376959.86400"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-37.39",
                                        "string": "-38° 36' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "2.99",
                                        "string": "2° 59' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-37.39",
                                        "string": "-38° 36' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "2.99",
                                        "string": "2° 59' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.30",
                                        "string": "02h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "13.31",
                                        "string": "13° 18' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "ari",
                                    "short": "Ari",
                                    "name": "Aries"
                                }
                            },
                            "extraInfo": {
                                "elongation": 125.75664,
                                "magnitude": 5.71062
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "uranus",
                            "name": "Uranus",
                            "distance": {
                                "fromEarth": {
                                    "au": "19.19461",
                                    "km": "2871473223.65600"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-37.35",
                                        "string": "-38° 39' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "4.22",
                                        "string": "4° 13' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-37.35",
                                        "string": "-38° 39' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "4.22",
                                        "string": "4° 13' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "2.30",
                                        "string": "02h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "13.30",
                                        "string": "13° 18' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "ari",
                                    "short": "Ari",
                                    "name": "Aries"
                                }
                            },
                            "extraInfo": {
                                "elongation": 124.71946,
                                "magnitude": 5.71227
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "neptune",
                        "name": "Neptune"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.09446",
                                    "km": "4502067145.81014"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-36.83",
                                        "string": "-37° 10' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "63.12",
                                        "string": "63° 7' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-36.83",
                                        "string": "-37° 10' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "63.12",
                                        "string": "63° 7' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.29",
                                        "string": "23h 17m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-5.74",
                                        "string": "-6° 15' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 79.15329,
                                "magnitude": 7.90302
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.11148",
                                    "km": "4504612627.51585"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-36.14",
                                        "string": "-37° 51' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "63.98",
                                        "string": "63° 58' 48\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-36.14",
                                        "string": "-37° 51' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "63.98",
                                        "string": "63° 58' 48\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.29",
                                        "string": "23h 17m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-5.73",
                                        "string": "-6° 16' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 78.14765,
                                "magnitude": 7.90424
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.12843",
                                    "km": "4507148789.99699"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-35.44",
                                        "string": "-36° 33' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "64.82",
                                        "string": "64° 49' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-35.44",
                                        "string": "-36° 33' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "64.82",
                                        "string": "64° 49' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.29",
                                        "string": "23h 17m 24s"
                                    },
                                    "declination": {
                                        "degrees": "-5.73",
                                        "string": "-6° 16' 12\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 77.14251,
                                "magnitude": 7.90546
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "neptune",
                            "name": "Neptune",
                            "distance": {
                                "fromEarth": {
                                    "au": "30.14531",
                                    "km": "4509674873.44766"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-34.75",
                                        "string": "-35° 15' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "65.65",
                                        "string": "65° 39' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-34.75",
                                        "string": "-35° 15' 0\""
                                    },
                                    "azimuth": {
                                        "degrees": "65.65",
                                        "string": "65° 39' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "23.30",
                                        "string": "23h 18m 00s"
                                    },
                                    "declination": {
                                        "degrees": "-5.72",
                                        "string": "-6° 16' 48\""
                                    }
                                },
                                "constellation": {
                                    "id": "aqr",
                                    "short": "Aqr",
                                    "name": "Aquarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 76.13788,
                                "magnitude": 7.90668
                            }
                        }
                    ]
                },
                {
                    "entry": {
                        "id": "pluto",
                        "name": "Pluto"
                    },
                    "cells": [
                        {
                            "date": "2020-12-20T09:00:00.000-05:00",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "35.07463",
                                    "km": "5247089237.02526"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-6.48",
                                        "string": "-7° 31' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "113.25",
                                        "string": "113° 15' 0\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-6.48",
                                        "string": "-7° 31' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "113.25",
                                        "string": "113° 15' 0\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.71",
                                        "string": "19h 42m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-22.55",
                                        "string": "-23° 27' 0\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 24.70196,
                                "magnitude": 14.4218
                            }
                        },
                        {
                            "date": "2020-12-21T09:00:00.000-05:00",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "35.08240",
                                    "km": "5248252178.78916"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-5.79",
                                        "string": "-6° 12' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "113.81",
                                        "string": "113° 48' 36\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-5.79",
                                        "string": "-6° 12' 36\""
                                    },
                                    "azimuth": {
                                        "degrees": "113.81",
                                        "string": "113° 48' 36\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.71",
                                        "string": "19h 42m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-22.54",
                                        "string": "-23° 27' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 23.71572,
                                "magnitude": 14.42128
                            }
                        },
                        {
                            "date": "2020-12-22T09:00:00.000-05:00",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "35.08990",
                                    "km": "5249374682.88083"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-5.11",
                                        "string": "-6° 53' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "114.37",
                                        "string": "114° 22' 12\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-5.11",
                                        "string": "-6° 53' 24\""
                                    },
                                    "azimuth": {
                                        "degrees": "114.37",
                                        "string": "114° 22' 12\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.71",
                                        "string": "19h 42m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-22.54",
                                        "string": "-23° 27' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 22.72971,
                                "magnitude": 14.42074
                            }
                        },
                        {
                            "date": "2020-12-23T09:00:00.000-05:00",
                            "id": "pluto",
                            "name": "Pluto",
                            "distance": {
                                "fromEarth": {
                                    "au": "35.09713",
                                    "km": "5250456491.43196"
                                }
                            },
                            "position": {
                                "horizontal": {
                                    "altitude": {
                                        "degrees": "-4.43",
                                        "string": "-5° 34' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "114.94",
                                        "string": "114° 56' 24\""
                                    }
                                },
                                "horizonal": {
                                    "altitude": {
                                        "degrees": "-4.43",
                                        "string": "-5° 34' 12\""
                                    },
                                    "azimuth": {
                                        "degrees": "114.94",
                                        "string": "114° 56' 24\""
                                    }
                                },
                                "equatorial": {
                                    "rightAscension": {
                                        "hours": "19.71",
                                        "string": "19h 42m 36s"
                                    },
                                    "declination": {
                                        "degrees": "-22.54",
                                        "string": "-23° 27' 36\""
                                    }
                                },
                                "constellation": {
                                    "id": "sgr",
                                    "short": "Sgr",
                                    "name": "Sagittarius"
                                }
                            },
                            "extraInfo": {
                                "elongation": 21.74396,
                                "magnitude": 14.42017
                            }
                        }
                    ]
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
Returns properties for the given body for the given date range in tabular format.
{% endswagger-description %}

{% swagger-parameter in="path" name="body" type="string" required="true" %}
ID of the body
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic
{% endswagger-parameter %}

{% swagger-parameter in="query" name="latitude" type="string" required="true" %}
Latitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="longitude" type="string" required="true" %}
Longitude of the observer's location
{% endswagger-parameter %}

{% swagger-parameter in="query" name="elevation" type="string" required="true" %}
Elevation from the sea in Meters
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from_date" type="string" required="true" %}
Starting date as Date. The maximum number of days you can query is 366 days.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to_date" type="string" required="true" %}
Ending date as Date. The maximum number of days you can query is 366 days.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="time" type="string" required="true" %}
Observer's time as Time
{% endswagger-parameter %}

{% swagger-parameter in="query" name="output" type="string" required="false" %}
Output format.

`rows`

or

`table`

. Default is

`table`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Response for a request made with " %}
```javascript
{
    "data": {
        "dates": {
            "from": "2020-12-20T09:00:00.000-05:00",
            "to": "2020-12-23T09:00:00.000-05:00"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 38.775867,
                "elevation": 1
            }
        },
        "rows": [
            {
                "body": {
                    "id": "moon",
                    "name": "Moon"
                },
                "positions": [
                    {
                        "date": "2020-12-20T09:00:00.000-05:00",
                        "id": "moon",
                        "name": "Moon",
                        "distance": {
                            "fromEarth": {
                                "au": "0.00267",
                                "km": "398770.33905"
                            }
                        },
                        "position": {
                            "horizontal": {
                                "altitude": {
                                    "degrees": "-39.40",
                                    "string": "-40° 36' 0\""
                                },
                                "azimuth": {
                                    "degrees": "70.99",
                                    "string": "70° 59' 24\""
                                }
                            },
                            "horizonal": {
                                "altitude": {
                                    "degrees": "-39.40",
                                    "string": "-40° 36' 0\""
                                },
                                "azimuth": {
                                    "degrees": "70.99",
                                    "string": "70° 59' 24\""
                                }
                            },
                            "equatorial": {
                                "rightAscension": {
                                    "hours": "23.13",
                                    "string": "23h 07m 48s"
                                },
                                "declination": {
                                    "degrees": "-11.96",
                                    "string": "-12° 2' 24\""
                                }
                            },
                            "constellation": {
                                "id": "aqr",
                                "short": "Aqr",
                                "name": "Aquarius"
                            }
                        },
                        "extraInfo": {
                            "elongation": 74.27557,
                            "magnitude": -9.45722,
                            "phase": {
                                "angel": "74.2018",
                                "fraction": "0.042",
                                "string": "Waxing Crescent"
                            }
                        }
                    },
                    {
                        "date": "2020-12-21T09:00:00.000-05:00",
                        "id": "moon",
                        "name": "Moon",
                        "distance": {
                            "fromEarth": {
                                "au": "0.00270",
                                "km": "403433.20074"
                            }
                        },
                        "position": {
                            "horizontal": {
                                "altitude": {
                                    "degrees": "-43.26",
                                    "string": "-44° 44' 24\""
                                },
                                "azimuth": {
                                    "degrees": "56.79",
                                    "string": "56° 47' 24\""
                                }
                            },
                            "horizonal": {
                                "altitude": {
                                    "degrees": "-43.26",
                                    "string": "-44° 44' 24\""
                                },
                                "azimuth": {
                                    "degrees": "56.79",
                                    "string": "56° 47' 24\""
                                }
                            },
                            "equatorial": {
                                "rightAscension": {
                                    "hours": "23.89",
                                    "string": "23h 53m 24s"
                                },
                                "declination": {
                                    "degrees": "-7.15",
                                    "string": "-8° 51' 0\""
                                }
                            },
                            "constellation": {
                                "id": "aqr",
                                "short": "Aqr",
                                "name": "Aquarius"
                            }
                        },
                        "extraInfo": {
                            "elongation": 85.52956,
                            "magnitude": -9.90583,
                            "phase": {
                                "angel": "85.5048",
                                "fraction": "0.036",
                                "string": "Waxing Crescent"
                            }
                        }
                    },
                    {
                        "date": "2020-12-22T09:00:00.000-05:00",
                        "id": "moon",
                        "name": "Moon",
                        "distance": {
                            "fromEarth": {
                                "au": "0.00272",
                                "km": "406803.88314"
                            }
                        },
                        "position": {
                            "horizontal": {
                                "altitude": {
                                    "degrees": "-45.10",
                                    "string": "-46° 54' 0\""
                                },
                                "azimuth": {
                                    "degrees": "41.52",
                                    "string": "41° 31' 12\""
                                }
                            },
                            "horizonal": {
                                "altitude": {
                                    "degrees": "-45.10",
                                    "string": "-46° 54' 0\""
                                },
                                "azimuth": {
                                    "degrees": "41.52",
                                    "string": "41° 31' 12\""
                                }
                            },
                            "equatorial": {
                                "rightAscension": {
                                    "hours": "0.61",
                                    "string": "00h 36m 36s"
                                },
                                "declination": {
                                    "degrees": "-2.20",
                                    "string": "-3° 48' 0\""
                                }
                            },
                            "constellation": {
                                "id": "cet",
                                "short": "Cet",
                                "name": "Cetus"
                            }
                        },
                        "extraInfo": {
                            "elongation": 96.54755,
                            "magnitude": -10.29789,
                            "phase": {
                                "angel": "96.5672",
                                "fraction": "0.030",
                                "string": "Waxing Gibbous"
                            }
                        }
                    },
                    {
                        "date": "2020-12-23T09:00:00.000-05:00",
                        "id": "moon",
                        "name": "Moon",
                        "distance": {
                            "fromEarth": {
                                "au": "0.00273",
                                "km": "408768.64035"
                            }
                        },
                        "position": {
                            "horizontal": {
                                "altitude": {
                                    "degrees": "-44.84",
                                    "string": "-45° 9' 36\""
                                },
                                "azimuth": {
                                    "degrees": "26.04",
                                    "string": "26° 2' 24\""
                                }
                            },
                            "horizonal": {
                                "altitude": {
                                    "degrees": "-44.84",
                                    "string": "-45° 9' 36\""
                                },
                                "azimuth": {
                                    "degrees": "26.04",
                                    "string": "26° 2' 24\""
                                }
                            },
                            "equatorial": {
                                "rightAscension": {
                                    "hours": "1.32",
                                    "string": "01h 19m 12s"
                                },
                                "declination": {
                                    "degrees": "2.74",
                                    "string": "2° 44' 24\""
                                }
                            },
                            "constellation": {
                                "id": "psc",
                                "short": "Psc",
                                "name": "Pisces"
                            }
                        },
                        "extraInfo": {
                            "elongation": 107.41558,
                            "magnitude": -10.65118,
                            "phase": {
                                "angel": "107.4676",
                                "fraction": "0.023",
                                "string": "Waxing Gibbous"
                            }
                        }
                    }
                ]
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}
