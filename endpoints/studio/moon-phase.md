---
description: Generate an image of the Moon based on the given parameters.
---

# Moon Phase

{% api-method method="post" host="https://api.astronomyapi.com" path="/api/v2/studio/moon-phase" %}
{% api-method-summary %}
Generate Moon Phase
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
{% api-method-parameter name="format" type="string" required=false %}
Image format to be returned. Valid values are `png` or `svg`. Defaults to `png`
{% endapi-method-parameter %}

{% api-method-parameter name="style" type="object" required=true %}
Style object contains the styling parameters for the image generated.
{% endapi-method-parameter %}

{% api-method-parameter name="observer" type="object" required=true %}
Observer object must contain the `latitude`, `longitude` and `date` of the observer. 
{% endapi-method-parameter %}

{% api-method-parameter name="view" type="object" required=true %}
View object is used to configure the view of the rendered image. The view object must contain a `type` object. 
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```typescript
{
    "data": {
        "imageUrl": "https://widgets.astronomyapi.com/moon-phase/generated/1234567890.png"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

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
        "type": "portrait-simple"
    }
}
```

## Format

The API currently supports outputting images in `svg` and `png` formats. These can be used in different use cases, depending on how and where you want them to be displayed. 

## Style

#### `moonStyle`

Valid values are `default`, `sketch` and `shaded.` Below are sample moons for each value.

![default](../../.gitbook/assets/moon.285d.png)

![shaded](../../.gitbook/assets/moon.285s.png)

![sketch](../../.gitbook/assets/moon.285k.png)

#### `backgroundStyle`

Background style supports the values either `stars` or `solid`. Passing `stars` will render a stars background while `solid` will render the background with a colid colour specified by the `backgroundColor` property.

#### `backgroundColor, headingColor and textColor`

These properties could be used to customize the image further. Colors could be defined as hex or as any of the 140 html color names.

## View

View object should specify which template to be used when rendering the image. Currently two templates are available.

![portrait-simple](../../.gitbook/assets/e86043757e0a337db6d529d42e6c67e9e832b104f75d92bf9e6a09fc4d44cc25.png)

![landscape-simple](../../.gitbook/assets/f2968861e774a453f7826a48bb0c1f41c22693a3b58475cbec0435e97171d8e2.png)

