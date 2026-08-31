---
description: Eclipses visible from the observer's location
---

# 🗓 Events

Returns the eclipses falling between two instants, as seen from the observer's
location. Each contact carries the altitude of the body at that moment, so it is
clear how much of the event actually happens above the horizon.

Only the Sun and the Moon have events. A solar eclipse is reported as the
observer sees it, so the same eclipse is total from one place and partial from
another.

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/events" method="get" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

## Two changes from v2

**`type` and `kind` are separate.** v2 returned a single string such as
`partial_lunar_eclipse`, which had to be split before either half could be used.
v3 returns `type: "lunar_eclipse"` and `kind: "partial"`.

**The contact names are consistent.** v2 named the beginning and end of totality
`fullStart` and `fullEnd` for a lunar eclipse but `totalStart` and `totalEnd` for
a solar one, for the same idea. v3 uses `totalStart` and `totalEnd` throughout,
and calls the block `contacts` rather than `eventHighlights`.

## Example

Every eclipse visible from London in 2026:

```
GET /api/v3/events?bodies=sun,moon&latitude=51.4779&longitude=-0.0015
    &from=2026-01-01&to=2026-12-31
```

## Notes

**A contact may be below the horizon.** Its `altitude` will be negative. An
eclipse is reported when any part of it is above the horizon, so check the
altitudes to know which stages are actually observable.

**`totalStart` and `totalEnd` are null** for an eclipse that does not reach
totality where the observer stands.
