---
description: Find deep sky objects and stars
---

# 🔎 Search

Searches the catalogue by name or by position.

Give `term` to search by name, or `rightAscension` and `declination` together to
search by position. The two are mutually exclusive.

{% openapi src="../../.gitbook/assets/astronomy-api-v3.yaml" path="/search" method="get" %}
[astronomy-api-v3.yaml](../../.gitbook/assets/astronomy-api-v3.yaml)
{% endopenapi %}

## Changes from v2

| v2                                              | v3                     |
| ----------------------------------------------- | ---------------------- |
| `match_type`                                    | `matchType`            |
| `order_by`                                      | `orderBy`              |
| `ra`, `dec` (strings)                           | `rightAscension`, `declination` (numbers) |
| `limit`, `offset` declared as strings           | declared as integers   |
| `position.equatorial.rightAscension.hours`      | `rightAscension`       |
| `position.equatorial.declination.degrees`       | `declination`          |
| `*.string`                                      | `formatted.*`, with `include=formatted` |

v2 declared `limit` and `offset` as strings because query parameters arrive as
text. v3 declares the type it means and does the conversion itself.

## Examples

By name:

```
GET /api/v3/search?term=andromeda&matchType=fuzzy&limit=10
```

By position:

```
GET /api/v3/search?rightAscension=0.712&declination=41.269
```
