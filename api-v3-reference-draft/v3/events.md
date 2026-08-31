---
description: Eclipses and apsides for the observer's location
---

# 🗓 Events

Returns the events falling between two instants, as seen from the observer's
location.

Two kinds are reported, told apart by `type`:

| `type`                          | What it is                                            | Bodies       |
| ------------------------------- | ----------------------------------------------------- | ------------ |
| `lunar_eclipse`, `solar_eclipse` | The Earth's shadow on the Moon, or the Moon's on us   | Sun and Moon |
| `apsis`                          | Nearest to, or farthest from, the Earth               | All          |

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/events" method="get" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

## Eclipses

Each contact carries the altitude of the body at that moment, so it is clear how
much of the event actually happens above the horizon. A solar eclipse is reported
as this observer sees it, so the same eclipse is total from one place and partial
from another.

`totalStart` and `totalEnd` are null for an eclipse that does not reach totality
where the observer stands.

## Apsides

A body's distance from the Earth rises and falls, and an apsis is a moment it
turns around. They alternate: perigee, apogee, perigee, and so on.

For the Moon these are the familiar ones, about 13.8 days apart, and the reason
some full Moons look larger than others.

For a planet the perigee is when it appears largest and brightest. It falls
within a few days of opposition for the outer planets, and of inferior
conjunction for Mercury and Venus. Jupiter's perigee on 6 December 2024 sat one
day before its opposition; Saturn's on 8 September 2024 fell on the same day as
its own.

The Sun's perigee is the Earth's perihelion, in early January, when the Earth is
about 0.9833 AU from the Sun rather than the 1.0167 AU it reaches in July.

## Examples

Everything visible from London in 2026:

```
GET /api/v3/events?latitude=51.4779&longitude=-0.0015
    &from=2026-01-01&to=2026-12-31
```

Only eclipses:

```
GET /api/v3/events?types=lunar_eclipse,solar_eclipse
    &latitude=51.4779&longitude=-0.0015&from=2026-01-01&to=2026-12-31
```

When Mars is next closest, and how far away that is:

```
GET /api/v3/events?bodies=mars&types=apsis
    &latitude=51.4779&longitude=-0.0015&from=2024-06-01&to=2025-06-01
```

## Changes from v2

**Apsides are new.** v2 had no notion of them.

**Every body has events now.** v2 accepted only `sun` and `moon`, because
eclipses were all it knew about.

**`type` and `kind` are separate.** v2 returned a single string such as
`partial_lunar_eclipse`, which had to be split before either half could be used.
v3 returns `type: "lunar_eclipse"` and `kind: "partial"`.

**The contact names are consistent.** v2 named the beginning and end of totality
`fullStart` and `fullEnd` for a lunar eclipse but `totalStart` and `totalEnd` for
a solar one, for the same idea. v3 uses `totalStart` and `totalEnd` throughout,
and calls the block `contacts` rather than `eventHighlights`.
