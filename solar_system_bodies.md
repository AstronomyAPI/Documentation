## Solar System Bodies

The Astronomy API supports the following Solar System bodies by their name. Certain API endpoints might require you to pass one or more of these Solar System bodies. 

More will be added soon.

`sun`, `mercury`, `venus`, `moon`, `mars`, `jupiter`, `saturn`, `uranus`, `neptune`, `pluto`

### Body properties

#### distance

Distances to the body from both Sun and Earth are returned on this property, in Kilo Meters `(km)` and Astronomical Units `(au)`.

#### position

Position of the body is returned by the `constellation`, Altitude `alt` / Azimuth `az` pairs and in Right Accession `(ra)` / Declination `(dec)` pairs.

Note that `alt/az` values also contain literal string values and degree values while the `ra/dec` values contain degree and hour values.