
## Inline SVG shortcode

https://github.com/maxboeck/eleventastic/blob/master/utils/shortcodes.js

```js
module.exports = {
    icon: function (name) {
        return `<svg class="icon icon--${name}" role="img" aria-hidden="true" width="24" height="24">
                    <use xlink:href="#icon-${name}"></use>
                </svg>`
    }
}
```

Usage:

```njk
{% icon "github" %}
```

