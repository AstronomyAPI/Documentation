---
description: >-
  Plants, Sun and Moon entities respond with common object properties. This page
  describes what to expect in the response.
---

# Body properties

Body entities returned from the API consists of the following properties.

| **Section** | **Subsection** | **Description**                                                                                                                                                         |
| ----------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | -              | Unique identifier for the body                                                                                                                                          |
| name        | -              | User friendly name for the body                                                                                                                                         |
| distance    | -              | Distance object                                                                                                                                                         |
| -           | fromEarth      | Distance from Earth in Kilometers (km) and Astronomical units (au)                                                                                                      |
| position    | -              | Position object                                                                                                                                                         |
| -           | horizonal      | Position object in horizontal coordinates. Object will return the values in Altitude and Azimuth (Alt/Az) format. Numerical and literal values are returned.            |
| -           | equatorial     | Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned. |
| extraInfo   | -              | Other information relating to the body                                                                                                                                  |
| -           | elongation     | Angular separation between the Sun and the planet, with Earth as the reference point                                                                                    |
| -           | magnitude      | Apparent magnitude of the object                                                                                                                                        |
|             | phase          | Phase of the body as an angle and a fraction.                                                                                                                           |

{% hint style="info" %}
`phase` property is available only to the Moon body&#x20;
{% endhint %}

#### Sample response object

```
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
}
```
