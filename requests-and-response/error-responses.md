---
description: Common error responses.
---

# 🚩 Error Responses

Error response from the API should return a JSON object with the key `error` describing the nature of the error. A request validation failure will cause a `422` http code to be produced.

### Sample validation error response

The below response was caused by not providing the value for `latitude` parameter.

```javascript
 {
    "statusCode": 422,
    "errors": [
        {
            "path": [],
            "property": "instance",
            "message": "requires property \"latitude\"",
            "schema": {
                "latitude": {
                    "type": "string"
                },
                "longitude": {
                    "type": "string"
                },
                "elevation": {
                    "type": "string"
                },
                "from_date": {
                    "type": "string"
                },
                "to_date": {
                    "type": "string"
                },
                "time": {
                    "type": "string"
                },
                "required": [
                    "latitude",
                    "longitude",
                    "elevation",
                    "from_date",
                    "to_date",
                    "time"
                ]
            },
            "instance": {
                "elevation": "1000",
                "from_date": "2017-12-20",
                "longitude": "-84.39733",
                "time": "08:00:00",
                "to_date": "2017-12-27"
            },
            "name": "required",
            "argument": "latitude",
            "stack": "instance requires property \"latitude\""
        }
    ]
}
```
