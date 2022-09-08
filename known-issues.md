---
description: This section describes known issues with the system
---

# ⚠ Known Issues

#### Endpoint timeout

You may experience endpoint timeouts - specifically in the studio endpoints. Retrying the request with the same request parameters will work.

#### Coordinates are slightly different from other astronomical software

Astronomy API calculates coordinates based on the geolocation details you specify in the request. Due to the precision of the location and algorithm difference, the coordinates can be slightly different than what you would find in other astronomical software.

#### Moon is upside down on the moon phase generator endpoint

Depending on the hemisphere you live on earth, the side of the moon that's up might change. Use the `orientation` parameter in the request to change the direction. see [moon-phase.md](endpoints/studio/moon-phase.md "mention") for details.
