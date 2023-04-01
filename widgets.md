---
description: Embeddable scripts for your website
---

# 🧩 Widgets

Need to integrate any of the studio endpoints on your website quickly? You might be looking for AstronomyAPI Widgets.

## Bare minimum

Widgets script can be loaded to your webpage by including a script tag inside the `<HEAD></HEAD>` tags, as shown below. Make sure to update the `yourEncryptedAuthString` with the base64 string you created as mentioned in the [authentication instructions](./#basic-authentication). Notice how the string should not include the term `Basic`.

{% code overflow="wrap" %}
```javascript
<html>
  <head>
    <title>My Website</title>
    <script src="https://widgets.astronomyapi.com/cdn/astronomy-api-widgets.js"></script>
  </head>
<body>
    <div id="moon-phase"></div>
    <div id="star-chart"></div>
    
    <script>
       document.addEventListener("DOMContentLoaded", function () {
        var client = new AstronomyAPI({
          basicToken: "yourEncryptedAuthString",
        });

        client.moonPhase();

        client.starChart();
      });
    </script>
  </body>
</html>
```
{% endcode %}

A \<DIV> tag is required to populate the widget. By default, the element id must be `moon-phase` or `star-chart`, depending on the type of widget you need.

A full list of examples could be found in the [examples folder on GitHub](https://github.com/AstronomyAPI/Widgets/tree/main/examples)

## Plugin API

The client instance is created using `new AstronomyAPI({...options})`. The parameter `basicToken` is required to initiate the class.

All methods follow the same payload body as the [moon phase](endpoints/studio/moon-phase.md) or [star chart](endpoints/studio/star-chart.md) API with an optional parameter `element` which can be used to attach a custom HTML element instead of the default element selector.

```
client.moonPhase({..options}, (response) => {})
client.starChart({..options}, (response) => {})
```

A callback function can be passed as the second parameter for each method. The callback function will be passed with the original response received from the API.

```javascript
  var client = new AstronomyAPI({
          basicToken: "yourEncryptedAuthString", // required
        });

        client.moonPhase(
          {
            element: "#moon-phase-element", // custom html element
            format: "png",
            style: {
              moonStyle: "sketch",
              backgroundStyle: "stars",
              backgroundColor: "red",
              headingColor: "white",
              textColor: "white",
            },
            observer: {
              latitude: 40.712772,
              longitude: -73.935242,
              date: "2020-10-28",
            },
            view: {
              type: "portrait-simple",
            },
          },
          (re) => { // callback function
            console.log("done", re);
          },
        );
      });
```

```javascript
var client = new AstronomyAPI({
          basicToken: "yourEncryptedAuthString",
        });

        client.starChart(
          {
            element: "#star-chart-element", // custom html element
            style: "navy",
            observer: {
              latitude: 12.775867,
              longitude: -23.39733,
              date: "2012-12-21",
            },
            view: {
              type: "constellation",
              parameters: {
                constellation: "ori",
              },
            },
          },
          (re) => { // callback function
            console.log("done", re);
          },
        );
      });
```
