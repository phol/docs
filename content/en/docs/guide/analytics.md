---
title: Add analytics
date: 2020-07-26
type: book
---

There are three main approaches to analysing your site traffic with Wowchemy:

- [Google Analytics](https://analytics.google.com)
  - a comprehensive, widely adopted solution
- [Google Tag Manager](https://tagmanager.google.com)
  - a service to integrate _any_ analytics provider, including Google Analytics, _without_ modifying any code
- Wowchemy JS Hook
  - to integrate other analytics services, paste the script provided by your analytics provider into [Wowchemy's custom scripts file]({{< relref "../customization.md#add-scripts-js" >}})

## Google

If you wish to use [Google Analytics](https://analytics.google.com) or [Google Tag Manager](https://tagmanager.google.com), include your associated tracking code (e.g. `UA-12345678-9`) in `config/_default/params.toml`:

```toml
############################
## Marketing
############################
[marketing]
  google_analytics = ""
  google_tag_manager = ""
```

### Troubleshooting

GA tracks users on your live _production_ website and not your own views on your _development_ site, if you have one.

Hugo's default environments are `development` when running the `hugo serve` command and `production` when running the `hugo` command. You can explicitly set the environment to production with `HUGO_ENV` or Hugo's `--environment` [option](https://gohugo.io/commands/hugo_env/#readout).

If you deploy with Netlify, the _production_ environment should already be setup in your `netlify.toml` file, but if not, check that your Netlify settings in `netlify.toml` are similar to the [latest Netlify settings in the _Academic_ template](https://github.com/wowchemy/starter-academic/blob/master/netlify.toml).

If you choose to use Google Tag Manager, you'll need to setup and configure your analytics solutions, such as Google Analytics, in the Google Tag Manager admin panel.

If you choose to use GA via Google Tag Manager (`google_tag_manager`) instead of directly via the `google_analytics` option, it will override the direct GA implementation to prevent tracking each user twice.

We recommend testing that your analytics are working as expected. If they are not, check that your production environment is as described above and check that your URL in your GA admin panel matches your site's URL. Furthermore, GA provide a troubleshooting guide to help with any issues.
