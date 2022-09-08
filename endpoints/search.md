---
description: Search for stars and deep space objects.
layout: editorial
---

# 🔎 Search

{% hint style="danger" %}
This part of the documentation refers to a feature that's currently in development. The request and response may be changed without notice.
{% endhint %}

Search endpoint can be used to get information for stars and deep space objects.

The response of this endpoint is an array of objects which is representing the results. The resulting items could be of object type star or a deep space object depending on the matching criteria.

See [body-properties-1.md](../requests-and-response/body-properties-1.md "mention") for information on response object details.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/search" method="get" summary="Get available bodies" %}
{% swagger-description %}
Returns a list of results based on the requested query
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic <hash>
{% endswagger-parameter %}

{% swagger-parameter in="query" name="term" type="string" required="true" %}
Search term. No need to provide if 

`ra`

 and 

`dec`

 values are provided for area search.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="match_type" type="string" required="true" %}
Matching algorithm. Valid values are 

`fuzzy`

 or 

`exact`

. A fuzzy match will return results starting with the given term while an exact match will exactly match the term. Defaults to 

`fuzzy`

. Optional for term search.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="ra" type="string" required="true" %}
Right ascension value to search around. Must be a decimal value as a string representation. Required if 

`dec`

 value is provided.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="dec" type="string" required="true" %}
Declination value to search around. Must be a decimal value as a string representation. Required if 

`ra`

 value is provided.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
How many records to return in the request.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="string" %}
Use offset to paginate the results. 0 will return the first page, adding the limit to the offset will return the next page.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="order_by" type="string" %}
Order the results by the field. The supported value is 

`name`

. Cannot use while doing an area search.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The response with the term as "orion"" %}
```javascript
{
    "meta": {
        "limit": 10,
        "offset": 0
    },
    "data": [
        {
            "id": "f9ea7803-44d6-56ea-a4c5-714d74d31237",
            "name": "Orion Nebula",
            "type": {
                "id": "SNR",
                "name": "Super Nova Remnant"
            },
            "subType": {
                "id": "EN+RN"
            },
            "crossIdentification": [
                {
                    "name": "M 42",
                    "catalogId": "M"
                },
                {
                    "name": "NGC 1976",
                    "catalogId": "NGC"
                },
                {
                    "name": "LBN 974",
                    "catalogId": "LBN"
                },
                {
                    "name": "Orion Nebula",
                    "catalogId": null
                },
                {
                    "name": "Great Orion Nebula",
                    "catalogId": null
                }
            ],
            "position": {
                "equatorial": {
                    "rightAscension": {
                        "hours": "5.59",
                        "string": "05h 35m 24s"
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
            }
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}
