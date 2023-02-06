---
description: This section describes known issues with the system
---

# ⚠ Known Issues

#### Endpoint timeout

You may experience endpoint timeouts (`HTTP 504`) - specifically in the studio endpoints. Retrying the request with the same request parameters will work.

#### Too many requests

Due to high resource consumption, you may experience too many requests (`HTTP 429`). Rate limiting is enforced on all consumers based on their IP and overall API consumption. Retrying after some time will resolve this error. If you require high API usage please send an email to contact@astronomyapi.com.

**Rapid API and rate limiting**

If you're authenticating with Rapid API you may receive a rate limit exceeded error. Simply get your own API key from the Astronomy API console instead of using the shared Rapid API key.

#### Coordinates are slightly different from other astronomical software

Astronomy API calculates coordinates based on the geolocation details you specify in the request. Due to the precision of the location and algorithm difference, the coordinates can be slightly different than what you would find in other astronomical software.

#### The moon is upside down on the moon phase generator endpoint

Depending on the hemisphere you live on earth, the side of the moon that's up might change. Use the `orientation` parameter in the request to change the direction. see [moon-phase.md](endpoints/studio/moon-phase.md "mention") for details.
