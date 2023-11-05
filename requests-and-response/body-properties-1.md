---
description: >-
  Search result items follows a common object schema. This page describes the
  different fields and what to expect as the values.
---

# 🔎 Search Result Properties

The following properties are returned in the search results objects returned from the API.&#x20;

<table data-header-hidden><thead><tr><th>Section</th><th width="150">Subsection</th><th width="150">Data Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>Section</strong></td><td><strong>Subsection</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>id</td><td>-</td><td>string</td><td>Unique identifier for the object.</td></tr><tr><td>name</td><td>-</td><td>string</td><td>Commonly used name for the object. If a name is not found defaults to the closest possible catalog id.</td></tr><tr><td>type</td><td>-</td><td>object</td><td>The type object.</td></tr><tr><td>-</td><td>id</td><td>string</td><td>The type of the object as a unique id.</td></tr><tr><td>-</td><td>name</td><td>string</td><td>The name of the type.</td></tr><tr><td>subType</td><td>-</td><td></td><td>Sub type object</td></tr><tr><td>-</td><td>id</td><td>string</td><td>The sub type of the object as a unique id. For stars this will return the spectral class while for DSO objects returns the sub type based on the type of the object.</td></tr><tr><td>-</td><td>name</td><td>string</td><td>The description or name of the sub type</td></tr><tr><td>crossIdentification</td><td>-</td><td>array</td><td>Returns any duplicated references in all catalogs. The array of objects consists of the <code>name</code> and the <code>catalogId</code> of the referring catalog.</td></tr><tr><td>position</td><td>-</td><td>object</td><td>Position object. Note that the object contains only the equatorial coordinates object and the constellation object.</td></tr><tr><td>-</td><td>equatorial</td><td>object</td><td>Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned.</td></tr><tr><td>-</td><td>constellation</td><td>object</td><td>The id, short code and the name of the constellation where the object can be seen in.</td></tr></tbody></table>

#### Sample response object

```javascript
{
    "meta": {
        "limit": 10,
        "offset": 0
    },
    "data": [
        {
            "id": "3ecb894e-99c0-5b4b-9fcf-6d4441fe351d",
            "name": "M 1",
            "type": {
                "id": "SNR",
                "name": "Super Nova Remnant"
            },
            "subType": {
                "id": "SNR",
                "name": "Super Nova Remnant"
            },
            "crossIdentification": [
                {
                    "name": "NGC 1952",
                    "catalogId": "NGC"
                },
                {
                    "name": "LBN 833",
                    "catalogId": "LBN"
                },
                {
                    "name": "Crab Nebula",
                    "catalogId": null
                },
                {
                    "name": "Taurus A",
                    "catalogId": null
                },
                {
                    "name": "M 1",
                    "catalogId": "M"
                }
            ],
            "position": {
                "equatorial": {
                    "rightAscension": {
                        "hours": "5.58",
                        "string": "05h 34m 48s"
                    },
                    "declination": {
                        "degrees": "22.01",
                        "string": "22° 0' 36\""
                    }
                },
                "constellation": {
                    "id": "tau",
                    "short": "Tau",
                    "name": "Taurus"
                }
            }
        }
    ]
}
```
