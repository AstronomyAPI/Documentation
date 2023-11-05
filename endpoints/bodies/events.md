---
description: Get celestial events for a given body for the given date range.
---

# 🗓 Events

Events API can return events for a single body for the given date range. In the events API currently, only the bodies `Sun` and `Moon` are supported.

See [Event Properties](../../requests-and-response/event-properties.md) for available event properties for bodies.

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/bodies/events/:body" method="get" summary="Get events for the given body" %}
{% swagger-description %}
Returns events for the given body for the given date range in tabular format.
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
            "to": "2021-12-23T09:00:00.000-05:00"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 38.775867,
                "elevation": 0
            }
        },
        "rows": [
            {
                "body": {
                    "id": "sun",
                    "name": "Sun"
                },
                "events": [
                    {
                        "type": "partial_solar_eclipse",
                        "eventHighlights": {
                            "partialStart": {
                                "date": "2021-06-10T03:45:15.241-05:00",
                                "altitude": -13.56
                            },
                            "totalStart": null,
                            "peak": {
                                "date": "2021-06-10T04:37:30.267-05:00",
                                "altitude": -5.85
                            },
                            "totalEnd": null,
                            "patialEnd": {
                                "date": "2021-06-10T05:32:52.677-05:00",
                                "altitude": 2.92
                            }
                        },
                        "rise": "2021-06-10T10:12:14.143Z",
                        "set": "2021-06-11T01:02:13.766Z",
                        "extraInfo": {
                            "obscuration": 0.76
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
