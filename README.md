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

Both email fields POST to FormSubmit, which relays each signup to the project inbox. The address is base64 in `WAITLIST_ENDPOINT` so crawlers that scrape page source for email addresses come up empty:

```js
const WAITLIST_ENDPOINT = "https://formsubmit.co/ajax/" + atob("...");
```

That is obfuscation, not secrecy. FormSubmit's activation email carries a hashed endpoint (`formsubmit.co/ajax/<hash>`) that reaches the same inbox with no address in the page at all. Replace the whole expression with that string once you have it.

FormSubmit does not deliver anything until the first submission is confirmed: submit the form once, then click the link it emails you.

The form requires a `.edu` address client side.
