---
description: >-
  When requesting for location and/or date-time related data, Observer
  parameters must be sent in the request.
---

# Observer Parameters

Observer Parameters include the current observers location and other information.

{% hint style="info" %}
Note how the casing of the properties change from camel case to snake case when doing a GET request.
{% endhint %}

| **Parameter** | **Required** | **Description** | Sample Value |
| :--- | :---: | :--- | :--- |
| longitude | Yes | Longitude of the observer's location, as Float | -84.39733 |
| latitude | Yes | Latitude of the observer's location, as Float | 33.775867 |
| elevation | Yes | Elevation from the sea in Meters as Number | 50 |
| from\_date/fromDate | Yes | Starting date as Date. When doing a GET request from\_date must be used. | 2018-12-20 |
| to\_date/toDate | Yes | Ending date as Date. When doing a GET request to\_date must be used. | 2018-12-22 |
| time | Yes | Observer's time as Time | 08:00:00 |

{% hint style="info" %}
Maximum day span that could be requested from the API is 30 days.
{% endhint %}

