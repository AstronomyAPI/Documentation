---
description: 'Generates a star chart with the given parameters, and returns the url'
---

# Star Chart

{% api-method method="post" host="https://api.astronomyapi.com" path="/api/v2/studio/star-chart" %}
{% api-method-summary %}
Generate star chart
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Basic &lt;hash&gt;
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="style" type="string" required=false %}
Style of the map to be generated. If not provided will use the default style. To see a demo of available styles see styles section on this page. 
{% endapi-method-parameter %}

{% api-method-parameter name="observer" type="object" required=true %}
Observer object must contain the `latitude`, `longitude` and `date` of the observer.
{% endapi-method-parameter %}

{% api-method-parameter name="view" type="object" required=true %}
View object is used to configure the view of the rendered image. The view object must contain a `type` and `parameters` object. Parameters object can vary based on the `type`.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```typescript
{
 "data": {
     "imageUrl": "https://widgets.astronomyapi.com/star-chart/generated/1234567890.png"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Rendering different views

#### Constellation

To generate an image of a constellation the `type` in the `view` object must be set to `constellation`. The 3 letter id of the constellation must be passed in the parameters for the view object.

{% hint style="info" %}
The 3 letter constellation id is case sensitive, only lower case is allowed
{% endhint %}

```typescript
{
    "style": "inverted",
    "observer": {
        "latitude": 33.775867,
        "longitude": -84.39733,
        "date": "2019-12-20"
    },
    "view": {
        "type": "constellation",
        "parameters": {
            "constellation": "ori" // 3 letter constellation id
        }
    }
}
```

#### Area

To generate an image of an area in the sky, set the `type` to `area`, then pass the RA and Dec values in the `position` object for the view `parameters`. Currently equatorial coordinates are supported by the API. Additionally the parameter `zoom` can be provided to scale the image, but it's optional.

```typescript
// Note how this request does not have the field `style` 
// The API will use the default style
{
    "observer": {
        "latitude": 33.775867,
        "longitude": -84.39733,
        "date": "2019-12-20"
    },
    "view": {
        "type": "area",
        "parameters": {
            "position": {
                "equatorial": {
                    "rightAscension": 14.83,
                    "declination": -15.23
                }
            },
            "zoom": 3 //optional
        }
    }
}
```

## Styles

### `default`

![](../../.gitbook/assets/a458456e6535de44ec8cf5fc78e54230efd961319d1e04615235585de53a4c98.png)

### `inverted`

![](../../.gitbook/assets/d11505ad53287e9bbb36be2f059b09fa3e0b765408e2df6659bb8e37957668db.png)

### `navy`

![](../../.gitbook/assets/b7654698395061f2e6985b49c5f9b4e6a55c5aec350f9919a3e00818c701d199.png)

### `red`

![](../../.gitbook/assets/9094a7b39b3ff6b06cf577ceb8f4c1cac3d2aa25fd07c74cb23f109ff32f5f59.png)



