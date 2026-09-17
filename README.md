# commutr landing page

One static page. No build step, no dependencies: `index.html` plus three images.

```
index.html              markup, styles and script in one file
assets/logo-navy.png    wordmark for light backgrounds (nav)
assets/logo-white.png   wordmark for navy backgrounds (phone header, footer)
assets/favicon.png      infinity mark on navy
```

Both wordmarks are extracted from the original `commutr.png` (white on navy). The navy background was keyed out to give a clean white wordmark with alpha, and that same mask was recolored navy for the light header.

## Deploying

This repo is named `commutr-app.github.io`, so Pages serves it at the org root: https://commutr-app.github.io/. Source is *Deploy from a branch*, `main`, `/ (root)`. The `.nojekyll` file keeps GitHub's Jekyll step out of the way.

## Local preview

```sh
python -m http.server 8000
```

## The waitlist form

Both email fields POST to FormSubmit, which relays each signup to the project inbox:

```js
const WAITLIST_ENDPOINT = "https://formsubmit.co/ajax/a046b01c2af5a98a08e3c1b6fb1a5be3";
```

That hash is FormSubmit's alias for the destination address, so the inbox never appears in the page source. Changing where signups land means generating a new alias from FormSubmit, not editing this file.

The form requires a `.edu` address client side. FormSubmit does not cap submissions, but it only keeps an archive of them for 30 days, so the inbox is the record.
