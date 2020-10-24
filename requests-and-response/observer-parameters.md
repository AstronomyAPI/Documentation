---
description: >-
  When requesting for location and/or date-time related data, Observer
  parameters must be sent in the request.
---

# Observer Parameters

Observer Parameters include the current observers location and other information.

| **Parameter** | **Required** | **Description** | Sample Value |
| :--- | :---: | :--- | :--- |
| longitude | Yes | Longitude of the observer's location, as Float | -84.39733 |
| latitude | Yes | Latitude of the observer's location, as Float | 33.775867 |
| elevation | Yes | Elevation from the sea in Meters as Number | 50 |
| from\_date | Yes | Starting date as Date | 2018-12-20 |
| to\_date | Yes | Ending date as Date | 2018-12-22 |
| time | Yes | Observer's time as Time | 08:00:00 |

Maximum day span that could be requested from the API is 30 days.

