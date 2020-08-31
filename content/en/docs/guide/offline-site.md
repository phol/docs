---
title: Build an offline site
date: 2020-04-13
type: book
---

Wish to build an _offline_ site?

Or an _online_ site that _does not attempt to speed up your site's load time_ by serving assets via a third party Content Distribution Network (CDN)?

Then read on for some tips to help guide you.

1. Remove the `static/admin/` folder if it exists
2. [Install]({{< relref "customization.md#custom-font" >}}) the [_native_ font theme](https://github.com/gcushen/hugo-academic/blob/master/data/fonts/native.toml) in `data/fonts/` if it's not preinstalled at `themes/academic/data/fonts/native.toml`
2. In `params.toml`:
    1. Change the `font` to `native` (use local native fonts optimised for every device)
    2. Set `netlify_cms` to `false` (disable the Netlify CMS integration)
3. Add concatenated JS assets to `static/js/vendor/main.min.js`
    - View the list of full assets to download in `themes/academic/data/assets.toml`
4. Add concatenated CSS assets to `static/css/vendor/main.min.css`
    - View the list of full assets to download in `themes/academic/data/assets.toml`
5. Add Font Awesome font assets to `static/`

Notes

- Installing the [Wowchemy Admin](https://github.com/wowchemy/wowchemy-admin) tool and running `academic import --assets` within your site's folder may help with **Steps 3 and 4** on importing JS and CSS assets.
- [Join the discussion](https://github.com/gcushen/hugo-academic/issues/1167) on contributing improvements to make it easier to create standalone sites
