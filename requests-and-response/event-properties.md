# 🕚 Event Properties

And Event object is returned when body events are requested using the[ Events API](../endpoints/bodies/events.md).

<table><thead><tr><th width="166">Section</th><th width="162">Sub Section</th><th width="113">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td></td><td>string</td><td>Describes the event type. This can be either of <code>total_lunar_eclipse</code>, <code>total_solar_eclipse</code>, <code>annular_solar_eclipse</code>, <code>partial_solar_eclipse</code>, <code>partial_lunar_eclipse</code> or <code>penumbral_lunar_eclipse</code></td></tr><tr><td>eventHighlights</td><td>-</td><td>object</td><td>Contains the event highlights</td></tr><tr><td></td><td>penumbralStart</td><td>object</td><td>Start of the penumbral eclipse. Available for the moon only.</td></tr><tr><td></td><td>partialStart</td><td>object</td><td>Start of the partial eclipse and the altitude from the horizon. Available for both the sun and the moon,</td></tr><tr><td></td><td>fullStart</td><td>object</td><td>Start of the full eclipse and the altitude from the horizon. Available for the moon only.</td></tr><tr><td></td><td>totalStart</td><td>object</td><td>Start of the total eclipse and the altitude from the horizon. Available for the sun only.</td></tr><tr><td></td><td>peak</td><td>object</td><td>Peak of the event and the altitude from the horizon. Available for both the sun and the moon</td></tr><tr><td></td><td>totalEnd</td><td>object</td><td>End of the total eclipse and the altitude from the horizon. Available for the sun only.</td></tr><tr><td></td><td>fullEnd</td><td>object</td><td>End of the full eclipse and the altitude from the horizon. Available for the moon only.</td></tr><tr><td></td><td>partialEnd</td><td>object</td><td>End of the partial eclipse and the altitude from the horizon. Available for both the sun and the moon,</td></tr><tr><td></td><td>penumbralEnd</td><td>object</td><td>Endrt of the penumbral eclipse and the altitude from the horizon. Available for the moon only.</td></tr><tr><td></td><td>rise</td><td>object</td><td>Rise time of the object for the date and the altitude from the horizon.</td></tr><tr><td></td><td>set</td><td>object</td><td>Set time of the object for the date and the altitude from the horizon.</td></tr><tr><td></td><td>extraInfo</td><td>object</td><td>Any other information.</td></tr></tbody></table>

#### Sample response object

```json
{
    "data": {
        "dates": {
            "from": "2020-12-20T09:00:00.000-05:00",
            "to": "2022-12-23T09:00:00.000-05:00"
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

```json
{
    "data": {
        "dates": {
            "from": "2020-12-20T09:00:00.000-05:00",
            "to": "2022-12-23T09:00:00.000-05:00"
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
                    "id": "moon",
                    "name": "Moon"
                },
                "events": [
                    {
                        "type": "total_lunar_eclipse",
                        "eventHighlights": {
                            "pemumbralStart": {
                                "date": "2022-05-15T20:32:25.341-05:00",
                                "altitude": 9.53
                            },
                            "partialStart": {
                                "date": "2022-05-15T21:28:25.341-05:00",
                                "altitude": 17.45
                            },
                            "fullStart": {
                                "date": "2022-05-15T22:29:25.341-05:00",
                                "altitude": 24.44
                            },
                            "peak": {
                                "date": "2022-05-15T23:11:25.341-05:00",
                                "altitude": 27.93
                            },
                            "fullEnd": {
                                "date": "2022-05-15T23:53:25.341-05:00",
                                "altitude": 30.09
                            },
                            "partialEnd": {
                                "date": "2022-05-16T00:54:25.341-05:00",
                                "altitude": 30.58
                            },
                            "pemumbralEnd": {
                                "date": "2022-05-16T01:50:25.341-05:00",
                                "altitude": 28.22
                            }
                        },
                        "rise": "2022-05-16T00:28:34.597Z",
                        "set": "2022-05-17T11:22:15.102Z",
                        "extraInfo": {
                            "obscuration": 1
                        }
                    }
                ]
            }
        ]
    }
}
```
