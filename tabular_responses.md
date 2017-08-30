## Tabular Responses

Certain API endpoints might return you data in a tabular format, thus making it easier for you to render them in your template files.

You can get the `table` object from response object using `data.table`.

    
    {
        "data": {
            "dates": {
                "from": "2016-12-20T00:00:00",
                "to": "2016-12-22T23:59:59"
            },
            "observer": {
                "geo": {
                    "lat": "17.2",
                    "lon": "70"
                }
            },
            "table": {
                .... table object
            }
        }
    }
    

A typical `table` object response will include a `header` and `rows`. The `header` contains the column names, while the `rows` contains the row data.

Each row object consists of a `cells` array and an `entry` object. The `entry` is the label for current row. While cells are the values for the corresponding columns of the row.

For more information on how to render this type of data refer to the [samples repository](https://github.com/AstronomyAPI/Samples)

    
    
    {
        "header": [
            "Column 1",
            "Column 2"
        ],
        "rows": [
            {
                "cells": [
                    {
                        .. Row 1, Col 1
                    },
                    {
                        .. Row 1, Col 2
                    }
                ],
                "entry": {
                    "id": "Row 1"
                }
            },
            {
                "cells": [
                    {
                        .. Row 2, Col 1
                    },
                    {
                        .. Row 2, Col 2
                    }
                ],
                "entry": {
                    "id": "Row 2"
                }
            },
            {
                "cells": [
                    {
                        .. Row 3, Col 1
                    },
                    {
                        .. Row 3, Col 2
                    }
                ],
                "entry": {
                    "id": "Row 3"
                }
            }
        ]
    }