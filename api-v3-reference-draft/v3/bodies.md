---
description: The bodies this API can report on
---

# 🪐 Bodies

Returns the identifiers accepted by the `bodies` parameter elsewhere.

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/bodies" method="get" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

## `earth` is not listed

v2 included `earth`, and asking for its position returned numbers. They were
meaningless: seen from the Earth it is at zero distance and has no direction, so
the right ascension, declination, altitude and azimuth v2 reported for it were
whatever fell out of the arithmetic.

v3 leaves it out, and `/positions?bodies=earth` returns 422.
