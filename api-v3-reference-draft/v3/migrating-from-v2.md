---
description: A field-by-field mapping from v2 to v3
---

# 🔀 Migrating from v2

v2 is unchanged and keeps working. Move when it suits you.

## Positions

### The request

| v2                     | v3                    | Notes                                                                 |
| ---------------------- | --------------------- | --------------------------------------------------------------------- |
| `/bodies/positions/{body}` | `?bodies=mars`    | A list, so several bodies need one request rather than several.        |
| `/bodies/positions`    | omit `bodies`         | v2 made "all bodies" the meaning of an absent path segment.            |
| `from_date`            | `from`                | Now an instant, not only a date.                                       |
| `to_date`              | `to`                  | Now an instant, not only a date.                                       |
| `time`                 | folded into `from`/`to` | v2 applied one time of day to every date.                            |
| —                      | `step`                | New. ISO 8601 duration. Defaults to `P1D`, which is what v2 did.       |
| —                      | `timezone`            | New. `auto` is v2's behaviour and the default.                         |
| `elevation` (required) | `elevation` (optional) | Defaults to sea level.                                                |
| `output=table\|rows`   | removed               | One shape now. Laying it out is the client's job.                      |
| —                      | `origin`              | New. `topocentric` or `geocentric`.                                    |
| —                      | `refraction`          | New. `standard` or `none`.                                             |
| —                      | `include=formatted`   | New. Opt in to the sexagesimal strings v2 always sent.                 |

Parameter names are camelCase throughout v3. v2 mixed `from_date` in the query
string with `backgroundStyle` in JSON bodies.

### The response

| v2                                                    | v3                          |
| ----------------------------------------------------- | --------------------------- |
| `data.table.rows[].cells[]` or `data.rows[].positions[]` | `data[].samples[]`       |
| `cell.date`                                           | `sample.time`               |
| `position.equatorial.rightAscension.hours` (string)   | `sample.rightAscension` (number) |
| `position.equatorial.declination.degrees` (string)    | `sample.declination` (number)  |
| `position.horizontal.altitude.degrees` (string)       | `sample.altitude` (number)  |
| `position.horizontal.azimuth.degrees` (string)        | `sample.azimuth` (number)   |
| `position.horizonal.*`                                | removed — it was a misspelling of `horizontal` and duplicated it |
| `*.string`                                            | `sample.formatted.*`, only with `include=formatted` |
| `distance.fromEarth.au` (string)                      | `sample.distance.au` (number) |
| `distance.fromEarth.km` (string)                      | `sample.distance.km` (number) |
| `position.constellation.id`                           | removed — a lowercase copy of the abbreviation |
| `position.constellation.short`                        | `sample.constellation.abbreviation` |
| `position.constellation.name`                         | `sample.constellation.name` |
| `extraInfo.elongation`                                | `sample.elongation`         |
| `extraInfo.magnitude`                                 | `sample.magnitude`          |
| `extraInfo.phase.angel`                               | `sample.phase.angle` — spelling corrected |
| `extraInfo.phase.fraction`                            | `sample.phase.fraction` — **value corrected**, see below |
| `extraInfo.phase.string`                              | `sample.phase.name`         |
| `cell.id` / `cell.name`                               | `data[].body.id` / `.name`, once per body rather than on every sample |

### Two corrections

**`phase.angel` → `phase.angle`.** A misspelling in v2 that reached the wire.

**`phase.fraction` was wrong.** v2 reported a value between 0 and 0.067, and it
ran backwards: largest at new moon, zero at full. v3 reports the fraction of the
Moon's disc that is lit, 0 at new and 1 at full. Anything that compensated for
the old behaviour needs unwinding.

### Precision

v2 rounded angles to two decimal places, which is 36 arcseconds — far coarser
than the underlying calculation. v3 returns five decimal places, about 0.04
arcseconds. Parsers that assumed a fixed width need to stop assuming it.

### Errors

| v2                                              | v3                                     |
| ----------------------------------------------- | -------------------------------------- |
| `{ "errors": [ { "property": "instance.latitude", ... } ] }` | RFC 9457 problem details |
| 422 for every validation failure                | 400 for unparseable, 422 for unacceptable |
| No stable code                                  | `type` URI and a per-parameter `code`  |

## Events

### The request

| v2                        | v3                  |
| ------------------------- | ------------------- |
| `/bodies/events/{body}`   | `/events?bodies=moon` |
| `from_date`, `to_date`, `time` | `from`, `to`   |

### The response

| v2                                     | v3                        |
| -------------------------------------- | ------------------------- |
| `data.table.rows[].cells[]`            | `data[].events[]`         |
| `type: "partial_lunar_eclipse"`        | `type: "lunar_eclipse"` and `kind: "partial"` |
| `eventHighlights`                      | `contacts`                |
| `eventHighlights.fullStart` (lunar)    | `contacts.totalStart`     |
| `eventHighlights.fullEnd` (lunar)      | `contacts.totalEnd`       |
| `eventHighlights.*.date`               | `contacts.*.time`         |
| `extraInfo.obscuration`                | `obscuration`             |

v2 named the same two moments `fullStart`/`fullEnd` for lunar eclipses and
`totalStart`/`totalEnd` for solar ones. v3 uses the `total` names for both.

## Search

| v2                                           | v3                     |
| -------------------------------------------- | ---------------------- |
| `match_type`                                 | `matchType`            |
| `order_by`                                   | `orderBy`              |
| `ra`, `dec` (strings)                        | `rightAscension`, `declination` (numbers) |
| `limit`, `offset` (declared as strings)      | declared as integers   |
| `position.equatorial.rightAscension.hours`   | `rightAscension`       |
| `position.equatorial.declination.degrees`    | `declination`          |

## Studio

| v2                                  | v3                          |
| ----------------------------------- | --------------------------- |
| `observer.date`                     | `time`, beside `observer`   |
| observer had no `elevation`         | `observer.elevation`, optional |
| `view.parameters.position.equatorial.rightAscension` | `view.parameters.position.rightAscension` |

The response is unchanged: `{ "data": { "imageUrl": "..." } }`.

## Bodies

**`GET /bodies` is gone.** It returned a fixed list of ten identifiers that never
change. That list is in the specification, so `bodies` is an enumerated type in
generated clients and there is nothing to fetch. Anything that called `/bodies`
to populate a picker can hold the list directly.

**`earth` is no longer among them.** Seen from the Earth it is at zero distance
and has no direction, so the numbers v2 returned for it were arbitrary.
Requesting it from `/positions` returns 422.
