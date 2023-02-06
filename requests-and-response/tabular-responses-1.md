---
description: Some endpoints return data as rows for easy rendering data as a list.
---

# 🔢 Row Responses

Certain API endpoints might return data as a list, so it's easier for you to render them in your template files.

You can get the `rows` array from the response object using `data.rows`.

```javascript
{
    "data": {
        "dates": {
            "from": "2016-12-20T00:00:00",
            "to": "2016-12-22T23:59:59"
        },
        "observer": {
            "location": {
                "longitude": -84.39733,
                "latitude": 33.775867,
                "elevation": 1000
            }
        },
        "rows": [
            .... rows
        ]
    }
}
```

Each object in the rows array can be accessed by iterating the array.

For more information on how to render this type of data refer to the [samples repository](https://github.com/AstronomyAPI/Samples)
