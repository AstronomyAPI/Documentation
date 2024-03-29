---
description: Generate an image of the Moon based on the given parameters.
---

# 🌒 Moon Phase

If you're looking to quickly integrate this feature on your website without making API calls, checkout [Widgets](../../widgets.md)

{% swagger baseUrl="https://api.astronomyapi.com" path="/api/v2/studio/moon-phase" method="post" summary="Generate Moon Phase" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
Basic \<hash>
{% endswagger-parameter %}

{% swagger-parameter in="body" name="format" type="string" required="false" %}
Image format to be returned. Valid values are `png` or `svg`. Defaults to `png`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="style" type="object" %}
Style object contains the styling parameters for the image generated.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="observer" type="object" required="true" %}
Observer object must contain the `latitude`, `longitude` and `date` of the observer.&#x20;
{% endswagger-parameter %}

{% swagger-parameter in="body" name="view" type="object" required="true" %}
View object is used to configure the view of the rendered image. The view object must contain a `type` object.&#x20;



`orientation` specifies which side of the moon should be up depending on the hemisphere you live in the world. This parameter is optional. If not provided AstronomyAPI will determine the values automatically.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```typescript
{
    "data": {
        "imageUrl": "https://widgets.astronomyapi.com/moon-phase/generated/1234567890.png"
    }
}
```
{% endswagger-response %}
{% endswagger %}

```typescript
{
    "format": "png",
    "style": {
        "moonStyle": "sketch",
        "backgroundStyle": "stars",
        "backgroundColor": "red",
        "headingColor": "white",
        "textColor": "red"
    },
    "observer": {
        "latitude": 6.56774,
        "longitude": 79.88956,
        "date": "2020-11-01"
    },
    "view": {
        "type": "portrait-simple",
        "orientation": "south-up"
    }
}
```

## Format

The API currently supports outputting images in `svg` and `png` formats. These can be used in different use cases, depending on how and where you want them to be displayed.&#x20;

## Style

#### `moonStyle`

Valid values are `default`, `sketch` and `shaded.` Below are sample moons for each value.

<div align="left">

<img src="../../.gitbook/assets/moon.285d.png" alt="default">

</div>

<div align="left">

<img src="../../.gitbook/assets/moon.285s.png" alt="shaded">

</div>

<div align="left">

<img src="../../.gitbook/assets/moon.285k.png" alt="sketch">

</div>

#### `backgroundStyle`

Background style supports the values either `stars` or `solid`. Passing `stars` will render a stars background while `solid` will render the background with a solid color specified by the `backgroundColor` property.

#### `backgroundColor, headingColor and textColor`

These properties could be used to customise the image further. Colours could be defined as hex or as any of the [140 html colour names](https://www.w3schools.com/tags/ref\_colornames.asp).

## View

#### `type`

The type parameter in the view object should specify which template to be used when rendering the image. Currently two templates are available.

<div align="left">

<img src="../../.gitbook/assets/e86043757e0a337db6d529d42e6c67e9e832b104f75d92bf9e6a09fc4d44cc25.png" alt="portrait-simple">

</div>

<div align="left">

<img src="../../.gitbook/assets/f2968861e774a453f7826a48bb0c1f41c22693a3b58475cbec0435e97171d8e2.png" alt="landscape-simple">

</div>

#### `orientation`

Orientation parameter in the view object, determines which orientation to use when rendering the moon. By default it will render north side up, as seen by an observer facing the south side of the sky. This parameter is optional.

Below is an example of the same image with different orientations.

<div align="left">

<img src="../../.gitbook/assets/33574d6b80418fce7f3cb4ba97e09ea0f460f7780b6a3367dda5e58643896230.png" alt="north-up">

</div>

<div align="left">

<img src="../../.gitbook/assets/0b12c46d2b33d72b4f848cd40d878221e57689ab2880d104d615721912dd5593.png" alt="south-up">

</div>
