## Body Position

This endpoint will return the position of a given system body for a given range of dates, for the given earth coordinates.

    GET /positions/<body_name>

For a list of valid body names see [Bodies](/documentation/bodies).

The following parameters are required to be sent in the request.

|| **Parameter** || **Description** ||
|| lon || Longitude of the observer's location ||
|| lat || Latitude of the observer's location ||
|| from_year || Numeric value of the start date year ||
|| from_month || Numeric value of the end date year ||
|| from_day || Numeric value of the start date day ||
|| to_year || Numeric value of the to date day ||
|| to_month || Numeric value of the start date month ||
|| to_day || Numeric value of the to date month ||

*Sample Response*

