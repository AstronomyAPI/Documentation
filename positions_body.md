## Body Position

This endpoint will return the position of a given system body for a given range of dates, for the given earth coordinates.

    GET /positions/<body_name>

For a list of valid body names see [Solar Bodies](/documentation/solar_bodies).


The following parameters are required to be sent in the request.

[Observer Parameters](/documentation/observer_parameters)

[Date Range Parameters](/documentation/date_range_parameters)



*Sample Response*
    
    {
        "data": {
            "dates": {
                "from": "2016-12-20T00:00:00",
                "to": "2016-12-22T23:59:59"
            },
            "observer": {
                "geo": {
                    "lat": "17.2",
                    "lon": "70"
                }
            },
            "table": {
                "header": [
                    "2016-12-20T00:00:00",
                    "2016-12-21T00:00:00",
                    "2016-12-22T00:00:00"
                ],
                "rows": [
                    {
                        "cells": [
                            {
                                "from_earth": {
                                    "au": 11.018684194657643,
                                    "km": 1648371693.4365277
                                },
                                "from_sun": {
                                    "au": 10.061439514160156,
                                    "km": 1505169927.4952018
                                }
                            },
                            {
                                "from_earth": {
                                    "au": 11.016045026021089,
                                    "km": 1647976879.428081
                                },
                                "from_sun": {
                                    "au": 10.061439514160156,
                                    "km": 1505169927.4952018
                                }
                            },
                            {
                                "from_earth": {
                                    "au": 11.013147184137678,
                                    "km": 1647543368.4526973
                                },
                                "from_sun": {
                                    "au": 10.061439514160156,
                                    "km": 1505169927.4952018
                                }
                            }
                        ],
                        "entry": {
                            "id": "distance",
                            "name": "distance"
                        }
                    },
                    {
                        "cells": [
                            {
                                "elong": 1.8111542051836544,
                                "mag": 0.41,
                                "radi": 0.00004107421552844921,
                                "sz": 16.9443302154541
                            },
                            {
                                "elong": 1.8111542051836544,
                                "mag": 0.41,
                                "radi": 0.00004107421552844921,
                                "sz": 16.9443302154541
                            },
                            {
                                "elong": 1.8111542051836544,
                                "mag": 0.41,
                                "radi": 0.00004107421552844921,
                                "sz": 16.9443302154541
                            }
                        ],
                        "entry": {
                            "id": "extra_info",
                            "name": "extra_info"
                        }
                    },
                    {
                        "cells": [
                            {
                                "alt_az": {
                                    "alt": {
                                        "deg": -15.470164165630274,
                                        "str": "-15deg 28' 12.6\""
                                    },
                                    "az": {
                                        "deg": 108.49305736205524,
                                        "str": "108deg 29' 35.0\""
                                    }
                                },
                                "constellation": {
                                    "abbr": "Oph",
                                    "id": "oph",
                                    "name": "Ophiuchus"
                                },
                                "ra_dec": {
                                    "dec": {
                                        "deg": -21.756012687132451,
                                        "str": "-21deg 45' 21.6\""
                                    },
                                    "ra": {
                                        "hr": 17.263433136940701,
                                        "str": "17h 15m 48.36s"
                                    }
                                }
                            },
                            {
                                "alt_az": {
                                    "alt": {
                                        "deg": -14.693787193949527,
                                        "str": "-14deg 41' 37.6\""
                                    },
                                    "az": {
                                        "deg": 108.68618594261598,
                                        "str": "108deg 41' 10.3\""
                                    }
                                },
                                "constellation": {
                                    "abbr": "Oph",
                                    "id": "oph",
                                    "name": "Ophiuchus"
                                },
                                "ra_dec": {
                                    "dec": {
                                        "deg": -21.76556372262808,
                                        "str": "-21deg 45' 56.0\""
                                    },
                                    "ra": {
                                        "hr": 17.271821018295324,
                                        "str": "17h 16m 18.56s"
                                    }
                                }
                            },
                            {
                                "alt_az": {
                                    "alt": {
                                        "deg": -13.918143524837724,
                                        "str": "-13deg 55' 05.3\""
                                    },
                                    "az": {
                                        "deg": 108.88227922465126,
                                        "str": "108deg 52' 56.2\""
                                    }
                                },
                                "constellation": {
                                    "abbr": "Oph",
                                    "id": "oph",
                                    "name": "Ophiuchus"
                                },
                                "ra_dec": {
                                    "dec": {
                                        "deg": -21.77497058782096,
                                        "str": "-21deg 46' 29.9\""
                                    },
                                    "ra": {
                                        "hr": 17.280196401978358,
                                        "str": "17h 16m 48.71s"
                                    }
                                }
                            }
                        ],
                        "entry": {
                            "id": "position",
                            "name": "position"
                        }
                    }
                ]
            }
        }
    }