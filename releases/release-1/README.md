# Release 1

## What we did

### Change cookie banner EventListener

Changing the `EventListener` which triggers the cookie banner to display, from `load` to `DOMContentLoaded` results in quite a bit perceived performance benefit to users because `load` waits the external resources to load: images, styles etc. whereas `DOMContentLoaded` just waits for the page HTML, and the DOM tree is built, but external resources like pictures <img> and stylesheets may be not yet loaded.

https://github.com/nhsuk/cookie-consent/issues/108

### Decrease size of Homepage promo images

Allow Wagtail to scale the homepage promo image to a smaller size as the max width it can ever be with our CSS is 720px. For the current Every Mind Matters image this change reduced size from 209 kB down to 34.4 kB. Currently this has only been done on the Homepage and should be looked at across the NHS website. 

### Inline JavaScript that is only used on individual pages

JavaScript for some legacy forms is only used on a couple of pages, instead of importing the JS on the whole website only include it on pages its used. The JavaScript main bundle goes from 64kb to 59kb (which is a 7.8125% reduction in the JS bundle for other pages).

## Data before

https://github.com/nhsuk/web-performance/tree/master/data/10-07-2020

## Data after

## Key findings

- `load` event vs `DOMContentLoaded`
