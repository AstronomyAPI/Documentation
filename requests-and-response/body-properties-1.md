---
description: >-
  Search result items follows a common object schema. This page describes the
  different fields and what to expect as the values.
---

# 🔎 Search Result Properties

The following properties are returned in the search results objects returned from the API.&#x20;

| **Section**         | **Subsection** | **Data Type** | **Description**                                                                                                                                                         |
| ------------------- | -------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                  | -              | string        | Unique identifier for the object.                                                                                                                                       |
| name                | -              | string        | Commonly used name for the object. If a name is not found defaults to the closest possible catalog id.                                                                  |
| type                | -              | object        | The type object.                                                                                                                                                        |
| -                   | id             | string        | The type of the object as a unique id.                                                                                                                                  |
| -                   | name           | string        | The name of the type.                                                                                                                                                   |
| subType             | -              |               | Sub type object                                                                                                                                                         |
| -                   | id             | string        | The sub type of the object as a unique id. For stars this will return the spectral class while for DSO objects returns the sub type based on the type of the object.    |
| -                   | name           | string        | The description or name of the sub type                                                                                                                                 |
| crossIdentification | -              | array         | Returns any duplicated references in all catalogs. The array of objects consists of the `name` and the `catalogId` of the referring catalog.                            |
| position            | -              | object        | Position object. Note that the object contains only the equatorial coordinates object and the constellation object.                                                     |
| -                   | equatorial     | object        | Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned. |
| -                   | constellation  | object        | The id, short code and the name of the constellation where the object can be seen in.                                                                                   |

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
