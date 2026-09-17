# commutr landing page

One static page. No build step, no dependencies: `index.html` plus three images.

```
docs/
  index.html              the whole page (markup, styles, script inline)
  assets/logo-navy.png    wordmark for light backgrounds (nav)
  assets/logo-white.png   original wordmark (phone header, footer)
  assets/favicon.png      infinity mark on navy
```

Both wordmarks are extracted from the original `commutr.png` (white on navy). The navy background was keyed out to give a clean white wordmark with alpha, and that same mask was recolored navy for the light header.

## Deploying to GitHub Pages

Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder **`/docs`**.

To serve from the repo root instead, move the contents of `docs/` up one level and pick folder `/ (root)`.

## Local preview

```sh
python -m http.server 8000 --directory docs
```

## Wiring up the waitlist

Both email forms are inert until you give them an endpoint. Near the bottom of `index.html`:

```js
const WAITLIST_ENDPOINT = "";   // e.g. https://formspree.io/f/xxxxxxx
```

Paste a Formspree / Getform / Basin URL there and both forms POST to it. Until then the form says it isn't connected rather than pretending to sign people up. Client side it already requires a `.edu` address.
