---
description: >-
  Search result items follows a common object schema. This page describes the
  different fields and what to expect as the values.
---

# Search Result Properties

The following properties are returned in the search results objects returned from the API.&#x20;

| **Section** | **Subsection**   | **Data Type** | **Description**                                                                                                                                                         |
| ----------- | ---------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | -                | string        | Unique identifier for the object. A `str_` prefix denotes a start while `dso_` prefix denotes a deep space object.                                                      |
| name        | -                | string        | Commonly used name for the object. If a name is not found defaults to the closest possible catalog id.                                                                  |
| type        | -                | object        | Type object                                                                                                                                                             |
| -           | id               | string        | The type of the object as a unique id.                                                                                                                                  |
| -           | name             | string        | The name of the type.                                                                                                                                                   |
| subType     | -                |               | Sub type object                                                                                                                                                         |
| -           | id               | string        | The sub type of the object as a unique id. For stars this will return the spectral class while for DSO objects returns the sub type based on the type of the object     |
| -           | name             | string        | The description or name of the sub type                                                                                                                                 |
| catalogIds  | -                | object        | Returns any ids if the object is included in different catalogs.                                                                                                        |
|             | ngc              | number        | New generation catalog id                                                                                                                                               |
|             | ic               | number        | Index catalog id                                                                                                                                                        |
|             | messier          | number        | Messier object id                                                                                                                                                       |
|             | hip              | number        | Hipparchus catalog id                                                                                                                                                   |
|             | hd               | number        | Henry Draper catalog id                                                                                                                                                 |
|             | hr               | number        | Harvard revised catalog id                                                                                                                                              |
| position    | -                | object        | Position object. Note that the object contains only the equatorial coordinates object and the constellation object.                                                     |
| -           | equatorial       | object        | Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned. |
| -           | constellation    | object        | The id, short code and the name of the constellation where the object can be seen in.                                                                                   |
| magnitude   | -                | object        | Magnitude object                                                                                                                                                        |
| -           | apparent         | number        | Apparent magnitude of the object                                                                                                                                        |
| -           | absolute         | number        | Absolute magnitude of the object                                                                                                                                        |
| extraInfo   | -                | object        | Extra information of the object                                                                                                                                         |
| -           | luminosity       | number        | Luminosity of the star. Available for stars only                                                                                                                        |
| -           | bayerDesignation | string        | Bayer designation of the star within the constellation.  Available for stars only                                                                                       |
| -           | companionStar    | string        | If the star is part of a star system, id of the parent star                                                                                                             |

#### Sample response object

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
