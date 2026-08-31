---
description: Where the Sun, the Moon and the planets are
---

# 🌐 Positions

Returns where each requested body appears from the observer's location, sampled between two instants.

One request covers as many bodies and as many instants as needed. Omit `bodies` to get all of them; set `step` to sample more finely than once a day.

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/positions" method="get" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

## Examples

Mars right now, from London:

```
GET /api/v3/positions?bodies=mars&latitude=51.4779&longitude=-0.0015
    &from=2024-06-21T11:00:00Z&to=2024-06-21T11:00:00Z
```

The Moon's altitude every fifteen minutes through a night, in UTC:

```
GET /api/v3/positions?bodies=moon&latitude=51.4779&longitude=-0.0015
    &from=2024-06-21T18:00:00Z&to=2024-06-22T06:00:00Z
    &step=PT15M&timezone=UTC
```

Everything visible, once a day for a week, with sexagesimal strings alongside the numbers:

```
GET /api/v3/positions?latitude=51.4779&longitude=-0.0015
    &from=2024-06-21&to=2024-06-28&step=P1D&include=formatted
```

## Notes

**`earth` is not available here.** Seen from the Earth it is at zero distance and has no direction, so v2's answer for it was arbitrary. Asking for it returns 422.

**Altitude may be negative.** A body below the horizon is a legitimate answer, not an error. Filter on `altitude > 0` if only what is up matters.

**Refraction is applied by default**, because that is where a body appears rather than where it geometrically is. Pass `refraction=none` for the geometric altitude. The difference is about half a degree at the horizon and negligible overhead.

**Large spans paginate.** With a fine `step` a long span can run to tens of thousands of samples; when `limit` is reached, `meta.sampling.nextCursor` carries the continuation.
