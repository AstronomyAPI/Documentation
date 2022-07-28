---
description: Search for stars and deep space objects.
layout: editorial
---

# Search

Search endpoint can be used to get information for stars and deep space objects.

The response of this endpoint is an array of objects which is representing the results. Resulting items could be of object type star or a deep space object depending of the matching criteria.

Star objects can be identified with the prefix `str_` in the id field while deep space objects will have the prefix `dso_`

See [body-properties-1.md](../requests-and-response/body-properties-1.md "mention") for information on response object details.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/search" method="get" summary="Get available bodies" %}
{% swagger-description %}
Returns a list of results based on the requested query
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-parameter in="query" name="term" type="string" required="true" %}
Search term
{% endswagger-parameter %}

{% swagger-parameter in="query" name="match_type" type="string" %}
Matching algorithm. Valid values are 

`fuzzy`

 or 

`exact`

. Defaults to 

`fuzzy`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The response with the term as "orion"" %}
```javascript
{
    "data": [
        {
            "id": "dso_1976",
            "name": "Great Orion Nebula",
            "type": {
                "id": "SNR",
                "name": "Super Nova Remnant"
            },
            "subType": {
                "id": "EN+RN",
                "name": null
            },
            "catalogIds": {
                "ngc": 1976,
                "ic": null,
                "messier": 42,
                "hipparchus": null,
                "hd": null,
                "hr": null
            },
            "position": {
                "equatorial": {
                    "rightAscension": {
                        "hours": "5.59",
                        "string": "05h 35m 17.3"
                    },
                    "declination": {
                        "degrees": "-4.61",
                        "string": "-5° 23' 24\""
                    }
                },
                "constellation": {
                    "id": "ori",
                    "short": "Ori",
                    "name": "Orion"
                }
            },
            "magnitude": {
                "apparent": null,
                "absolute": 4
            },
            "extraInfo": {}
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="The response with the term as "bernard"" %}
```javascript
{
    "data": [
        {
            "id": "str_87937",
            "name": "Barnard's Star",
            "type": {
                "id": "str",
                "name": null
            },
            "subType": {
                "id": "multiple",
                "name": null
            },
            "catalogIds": {
                "ngc": null,
                "ic": null,
                "messier": null,
                "hipparchus": 87937,
                "hd": null,
                "hr": null
            },
            "position": {
                "equatorial": {
                    "rightAscension": {
                        "hours": "17.96",
                        "string": "17h 57m 48s"
                    },
                    "declination": {
                        "degrees": "4.69",
                        "string": "4° 41' 36\""
                    }
                },
                "constellation": {
                    "id": "oph",
                    "short": "Oph",
                    "name": "Ophiuchus"
                }
            },
            "magnitude": {
                "apparent": 9.54,
                "absolute": 13.235
            },
            "extraInfo": {
                "spectralClass": "sdM4",
                "luminosity": 0.0004,
                "bayerDesignation": null
            }
        },
        {
            "id": "dso_6822",
            "name": "Barnards Galaxy",
            "type": {
                "id": "G",
                "name": "Galaxy"
            },
            "subType": {
                "id": "IBm",
                "name": "Irregular / Magellanic Cloud"
            },
            "catalogIds": {
                "ngc": 6822,
                "ic": 4895,
                "messier": null,
                "hipparchus": null,
                "hd": null,
                "hr": null
            },
            "position": {
                "equatorial": {
                    "rightAscension": {
                        "hours": "19.75",
                        "string": "19h 44m 56s"
                    },
                    "declination": {
                        "degrees": "-14.81",
                        "string": "-15° 11' 23\""
                    }
                },
                "constellation": {
                    "id": "sgr",
                    "short": "Sgr",
                    "name": "Sagittarius"
                }
            },
            "magnitude": {
                "apparent": 8.7,
                "absolute": 9.3
            },
            "extraInfo": {}
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}
