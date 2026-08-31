---
description: Rendered images of the sky
---

# 📸 Studio

The studio endpoints render an image and return a URL to it. Both take the same
`observer` and `time`, and differ only in what they draw.

## What changed from v2

**`time` sits beside `observer`, not inside it.** v2 nested `date` within the
observer object. A moment is not a property of a place, and every other endpoint
treats them separately.

**Elevation is accepted.** v2's studio endpoints took only latitude and longitude
and assumed sea level.

## ✨ Star Chart

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/studio/star-chart" method="post" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

A chart can be framed either on a point in the sky with a zoom level, or on a
named constellation.

```json
{
    "observer": { "latitude": 51.4779, "longitude": -0.0015, "elevation": 0 },
    "time": "2024-06-21T22:00:00Z",
    "view": {
        "type": "area",
        "parameters": {
            "position": { "rightAscension": 5.5, "declination": -5.4 },
            "zoom": 4
        }
    },
    "style": "default"
}
```

v2 wrapped the position in a further `equatorial` object. There is only one frame
involved, so v3 does not.

## 🌒 Moon Phase

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/studio/moon-phase" method="post" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

```json
{
    "observer": { "latitude": 51.4779, "longitude": -0.0015, "elevation": 0 },
    "time": "2024-06-21T22:00:00Z",
    "view": { "type": "portrait-simple", "orientation": "north-up" },
    "style": { "moonStyle": "default", "backgroundStyle": "stars" },
    "format": "png"
}
```

## Notes

**Images are cached.** An identical request returns the same URL without
re-rendering.

**`format` accepts `png` or `svg`**, and defaults to `png`.
