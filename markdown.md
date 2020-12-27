
## Shortcode to allow embedding markdown in .njk files

[clenemt/eleventy-webpack » **utils/shortcodes.js**](https://github.com/clenemt/eleventy-webpack/blob/master/utils/shortcodes.js)

```js
module.exports = {
  // Allow embedding markdown in `.njk` files
  // {% markdown %}
  // # Heading
  // {% endmarkdown %}
  markdown: (content) => markdown.render(outdent.string(content)),
```

[clenemt/eleventy-webpack » **.eleventy.js**](https://github.com/clenemt/eleventy-webpack/blob/master/.eleventy.js)

```js
const shortcodes = require('./utils/shortcodes');

...

config.addPairedShortcode('markdown', shortcodes.markdown);
```

## Multiple Markdown plugins

[brycewray/eleventy_solo_starter » **.eleventy.js**](https://github.com/brycewray/eleventy_solo_starter/blob/main/.eleventy.js)

```js
  /* Markdown plugins */
  // https://www.11ty.dev/docs/languages/markdown/
  // --and-- https://github.com/11ty/eleventy-base-blog/blob/master/.eleventy.js
  // --and-- https://github.com/planetoftheweb/seven/blob/master/.eleventy.js
  let markdownIt = require("markdown-it")
  let markdownItFootnote = require("markdown-it-footnote")
  let markdownItPrism = require('markdown-it-prism')
  let markdownItAttrs = require('markdown-it-attrs')
  let markdownItBrakSpans = require('markdown-it-bracketed-spans')
  let markdownItLinkAttrs = require('markdown-it-link-attributes')
  let markdownItOpts = {
    html: true,
    linkify: false,
    typographer: true
  }
  const markdownEngine = markdownIt(markdownItOpts)
  markdownEngine.use(markdownItFootnote)
  markdownEngine.use(markdownItPrism)
  markdownEngine.use(markdownItAttrs)
  markdownEngine.use(markdownItBrakSpans)
  markdownEngine.use(markdownItLinkAttrs, {
    pattern: /^https:/,
    attrs: {
      target: '_blank',
      rel: 'noreferrer noopener'
    }
  })
  eleventyConfig.setLibrary("md", markdownEngine)
  ```
