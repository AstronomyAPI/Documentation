## Date Range Parameters

Date Range Parameters include the current date and time in UTC.

|| **Parameter** || **Required** || **Description** ||
|| from_year  || Yes || Starting year, as Number ||
|| from_month  || Yes || Starting month, as Number ||
|| from_day  || Yes || Starting day, as Number ||
|| to_year  || Yes || Ending year, as Number ||
|| to_month  || Yes || Ending month, as Number ||
|| to_day  || Yes || Ending day, as Number ||
|| hour  || No || Observing hour, as Number ||
|| minute  || No || Observing minute, as Number ||

`hour` and `minute` are optional. If not supplied will default to `00:00`

Maximum day span that could be requested from the API is seven days.