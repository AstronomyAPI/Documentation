---
description: >-
  Plants, Sun and Moon entities respond with common object properties. This page
  describes what to expect in the response.
---

# 🪐 Body Properties

Body entities returned from the [Positions API](../endpoints/bodies/positions.md) consists of the following properties.

<table data-header-hidden><thead><tr><th>Section</th><th width="150">Subsection</th><th width="150">Data Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>Section</strong></td><td><strong>Subsection</strong></td><td><strong>Data Type</strong></td><td><strong>Description</strong></td></tr><tr><td>id</td><td>-</td><td>string</td><td>Unique identifier for the body</td></tr><tr><td>name</td><td>-</td><td>string</td><td>User friendly name for the body</td></tr><tr><td>distance</td><td>-</td><td>object</td><td>Distance object</td></tr><tr><td>-</td><td>fromEarth</td><td>object</td><td>Distance from Earth in Kilometers (km) and Astronomical units (au)</td></tr><tr><td>position</td><td>-</td><td>object</td><td>Position object</td></tr><tr><td>-</td><td>horizonal</td><td>object</td><td>Position object in horizontal coordinates. Object will return the values in Altitude and Azimuth (Alt/Az) format. Numerical and literal values are returned.</td></tr><tr><td>-</td><td>equatorial</td><td>object</td><td>Position object in equatorial coordinates. Object will return the values in Right Ascension and Declination (RA/Dec) format. Numerical and literal values are returned.</td></tr><tr><td>extraInfo</td><td>-</td><td>object</td><td>Other information relating to the body</td></tr><tr><td>-</td><td>elongation</td><td>string</td><td>Angular separation between the Sun and the planet, with Earth as the reference point</td></tr><tr><td>-</td><td>magnitude</td><td>string</td><td>Apparent magnitude of the object</td></tr><tr><td></td><td>phase</td><td>object</td><td>Phase of the body as an angle and a fraction.</td></tr></tbody></table>

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

