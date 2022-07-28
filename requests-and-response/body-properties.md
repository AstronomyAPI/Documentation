---
description: >-
  Plants, Sun and Moon entities respond with common object properties. This page
  describes what to expect in the response.
---

# Body Properties

Body entities returned from the API consists of the following properties.

| **Section** | **Subsection** | **Data Type** | **Description**                                                                                                                                                         |
| ----------- | -------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | -              | string        | Unique identifier for the body                                                                                                                                          |
| name        | -              | string        | User friendly name for the body                                                                                                                                         |
| distance    | -              | object        | Distance object                                                                                                                                                         |
| -           | fromEarth      | object        | Distance from Earth in Kilometers (km) and Astronomical units (au)                                                                                                      |
| position    | -              | object        | Position object                                                                                                                                                         |
| -           | horizonal      | object        | Position object in horizontal coordinates. Object will return the values in Altitude and Azimuth (Alt/Az) format. Numerical and literal values are returned.            |
| -           | equatorial     | object        | Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned. |
| extraInfo   | -              | object        | Other information relating to the body                                                                                                                                  |
| -           | elongation     | string        | Angular separation between the Sun and the planet, with Earth as the reference point                                                                                    |
| -           | magnitude      | string        | Apparent magnitude of the object                                                                                                                                        |
|             | phase          | object        | Phase of the body as an angle and a fraction.                                                                                                                           |

{% hint style="info" %}
`phase` property is available only in the Moon body&#x20;
{% endhint %}

#### Sample response object

```javascript
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
