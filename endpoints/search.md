---
description: Search for stars and deep space objects.
layout: editorial
---

# 🔎 Search

Search endpoint can be used to get information for stars and deep space objects.

The response of this endpoint is an array of objects which is representing the results. Depending on the matching criteria, the resulting items could be of object type `star` or a `deep space object`.

See [Search Result Properties](../requests-and-response/body-properties-1.md) for information on response object details.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/search" method="get" summary="Get available bodies" %}
{% swagger-description %}
Returns a list of results based on the requested query
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic
{% endswagger-parameter %}

{% swagger-parameter in="query" name="term" type="string" required="true" %}
Search term. Conditionally required if

`ra`

and

`dec`

values are not provided for area search.
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

{% swagger-parameter in="query" name="limit" type="string" required="false" %}
How many records to return in the request.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="offset" type="string" required="false" %}
Use offset to paginate the results. 0 will return the first page, adding the limit to the offset will return the next page.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="order_by" type="string" required="false" %}
Order the results by the field. The supported value is

`name`

. Does not support during an area search.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The response with the term as " %}
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

### Object types and sub types

Search API can only be used for searching stars and deep space objects. For searching for planets use the [positions API](bodies.md) instead. For a list of DOS types see [DSO enums](../requests-and-response/dso-enums.md)

### Object catalogs

The following object catalogs are available for searching. Please note all objects may not be present in the database for some catalogs.

<table><thead><tr><th width="95">ID</th><th>Name</th></tr></thead><tbody><tr><td>LBN</td><td>Lynds' Catalogue of Bright Nebulae</td></tr><tr><td>NGC</td><td>The New General Catalogue</td></tr><tr><td>HCG</td><td>A Hickson Compact Group</td></tr><tr><td>ZWG</td><td>The Catalogue of Galaxies and Clusters of Galaxies</td></tr><tr><td>HR</td><td>Revised Harvard Photometry</td></tr><tr><td>IC</td><td>Index Catalogue</td></tr><tr><td>UGC</td><td>The Uppsala General Catalogue of Galaxies</td></tr><tr><td>KUG</td><td>The Kiso Ultraviolet Galaxy Catalogue</td></tr><tr><td>FCC</td><td>A Catalogue and Photometric Properties of Galaxies</td></tr><tr><td>DDO</td><td>David Dunlap Observatory Catalogue</td></tr><tr><td>ARP</td><td>The Atlas of Peculiar Galaxies</td></tr><tr><td>MCG</td><td>Morphological Catalogue of Galaxies</td></tr><tr><td>ESO</td><td>The European Southern Observatory Catalogue</td></tr></tbody></table>
