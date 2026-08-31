---
description: What changed in v3, and why
---

# 🛰 API v3 Reference

v3 is a breaking redesign of the request and response shapes. v2 is unchanged and
continues to work; nothing here affects it.

{% hint style="info" %}
v3 is being built. These pages are published as each endpoint is settled, so that
the design can be read and argued with before it ships. Anything not yet listed
in the sidebar is still being written.
{% endhint %}

## Three conventions

Knowing these removes most of the surprises.

**Numbers are numbers.** v2 returned every figure as a string, so `"41.26"` had
to be parsed back before it could be used. v3 uses the JSON number type.

**One representation per value.** v2 sent each angle twice: once as a number and
once pre-formatted for display, as `"41° 15' 36\""`. It also sent the whole
horizontal position twice, under `horizontal` and under a misspelled `horizonal`.
v3 sends the number once. The formatted form is available on request through
`include=formatted`, and the misspelling is gone.

**Units are declared, not implied.** Every response carries a `meta.units` block.
Right ascension is in hours, following astronomical convention; every other angle
is in degrees. v2 stated this nowhere.

Together these make a positions response about 60% smaller while carrying more
information.

## Sampling

v2 returned one position per day, at a single time of day. Asking for an
altitude curve meant twenty-four requests.

v3 takes `from` and `to` as instants and a `step` as an ISO 8601 duration, so
one request covers whatever resolution is wanted:

```
?from=2024-06-21T00:00:00Z&to=2024-06-22T00:00:00Z&step=PT1H
```

`step=P1D` reproduces v2's behaviour exactly, and is the default.

## Time zones

v2 inferred the time zone from the observer's coordinates and gave no way to
override it, so two callers asking about the same instant received differently
labelled timestamps and neither could ask for UTC.

v3 takes an explicit `timezone`. `auto` keeps v2's behaviour and remains the
default; `UTC` is the unambiguous choice.

## Errors

v2 returned the raw output of its schema validator, exposing internal paths such
as `instance.latitude` and offering no stable code to branch on.

v3 returns [RFC 9457](https://www.rfc-editor.org/rfc/rfc9457) problem details as
`application/problem+json`, with a stable `type` URI and a machine-readable code
for each parameter at fault.

## Corrections

Two v2 responses were wrong rather than merely awkward, and v3 fixes both.

`extraInfo.phase.angel` was misspelled. It is `phase.angle` in v3.

`extraInfo.phase.fraction` was wrong twice over: it was scaled to a range of 0 to
0.067 instead of 0 to 1, and it ran backwards, reporting its largest value at new
moon and zero at full. In v3 it is the fraction of the Moon's disc that is lit,
from 0 at new to 1 at full.

## The bodies

The Sun, the Moon, and Mercury, Venus, Mars, Jupiter, Saturn, Uranus, Neptune
and Pluto. The list is fixed, so v3 carries it in the specification rather than
serving it: v2's `/bodies` endpoint spent a request to return ten constants that
never change, and generated clients now get the ids as a type instead.

`earth` is not among them. Seen from the Earth it is at zero distance and has no
direction, so the right ascension, declination, altitude and azimuth v2 reported
for it were whatever fell out of the arithmetic. Asking for it returns 422.

## Moving across

See [Migrating from v2](migrating-from-v2.md) for a field-by-field mapping.
