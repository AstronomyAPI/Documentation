## Positions

This endpoint will return the position of Solar System bodies for a given range of dates, for the given Earth coordinates.

    GET /positions 


The following parameters are required to be sent in the request.

[Observer Parameters](/documentation/observer_parameters)

[Date Range Parameters](/documentation/date_range_parameters)


*Sample Response*

    {
        "data": {
            "dates": {
                "from": "2016-12-20T00:00:00",
                "list": [
                    "2016-12-20T00:00:00"
                ],
                "to": "2016-12-20T23:59:59"
            },
            "observer": {
                "geo": {
                    "lat": "33.775867",
                    "lon": "-84.39733"
                }
            },
            "rows": [
                {
                    "columns": [
                        {
                            "date": "2016-12-20T00:00:00",
                            "dist": {
                                "earth": {
                                    "au": 0.98382376714112019,
                                    "km": 147177940.70836419
                                },
                                "sun": {
                                    "au": 0,
                                    "km": 0
                                }
                            },
                            "id": "sun",
                            "meta": {
                                "elong": 0,
                                "mag": -26.8,
                                "radi": 0.004601224197882966,
                                "sz": 1898.1412353515625
                            },
                            "name": "Sun",
                            "pos": {
                                "altaz": {
                                    "alt": {
                                        "deg": -17.676677205653913,
                                        "str": "-17deg 40' 36.0\""
                                    },
                                    "az": {
                                        "deg": 253.20953205863395,
                                        "str": "253deg 12' 34.3\""
                                    }
                                },
                                "const": {
                                    "abbr": "Leo",
                                    "id": "leo",
                                    "name": "Leo"
                                },
                                "radec": {
                                    "dec": {
                                        "deg": -23.427243017367854,
                                        "str": "-23deg 25' 38.1\""
                                    },
                                    "ra": {
                                        "hr": 17.875687472812032,
                                        "str": "17h 52m 32.47s"
                                    }
                                }
                            }
                        }
                    ],
                    "id": "sun",
                    "name": "Sun"
                },
                {
                    "columns": [
                        {
                            "date": "2016-12-20T00:00:00",
                            "dist": {
                                "earth": {
                                    "au": 0.79518336244444721,
                                    "km": 118957737.83775564
                                },
                                "sun": {
                                    "au": 0.4070223867893219,
                                    "km": 60889682.39091436
                                }
                            },
                            "id": "mercury",
                            "meta": {
                                "elong": 0.12851867808223255,
                                "mag": 3.38,
                                "radi": 0.000026483396276688,
                                "sz": 10.925185203552246
                            },
                            "name": "Mercury",
                            "pos": {
                                "altaz": {
                                    "alt": {
                                        "deg": -3.3902502011998239,
                                        "str": "-03deg 23' 24.9\""
                                    },
                                    "az": {
                                        "deg": 244.62816986540426,
                                        "str": "244deg 37' 41.4\""
                                    }
                                },
                                "const": {
                                    "abbr": "Sex",
                                    "id": "sex",
                                    "name": "Sextans"
                                },
                                "radec": {
                                    "dec": {
                                        "deg": -22.885117161385157,
                                        "str": "-22deg 53' 06.4\""
                                    },
                                    "ra": {
                                        "hr": 19.077950188242596,
                                        "str": "19h 04m 40.62s"
                                    }
                                }
                            }
                        }
                    ],
                    "id": "mercury",
                    "name": "Mercury"
                }
                
                ...
                ...
                ...
                ...
                ...
                ...
            ]
        }
    }