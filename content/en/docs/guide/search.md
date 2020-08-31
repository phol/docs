---
title: Add search
date: 2018-07-23
type: book
---

**Empower your users** to search your website content for keywords so that they can quickly discover relevant content.

If search is enabled, a **search icon** will automatically appear in the navigation bar and a **search box** will appear in the sidebar of any content using the docs/tutorial layout (as can be seen on this site). Clicking the search icon will toggle the search dialog.

**Keyboard shortcuts** are available to facilitate searching. Pressing `/` will toggle the search dialog and pressing `ESC` will close the dialog.

{{< figure library="1" src="docs/search.png" title="Enable users to quickly discover relevant content by searching from the navigation bar." >}}

It's possible to **customize the search system** to your needs. The search feature may either be powered by the **built-in** algorithm (default) or powered by [Algolia](#algolia). Alternatively, you can [disable](#disable) the integrated search engine and instead create your own third party (e.g. Google) search widget by following the guide in the [Alternatives](#alternatives) section below.

### Built-in

Wowchemy comes with its own integrated search engine. If it's not already enabled, it can be enabled by setting `engine = 1` under `[search]` in `config/_default/params.toml`.

Note that this search engine runs entirely in the web browser on the visitor's device. Thus, it is not scalable to an extremely large number of pages. If you have a very large amount of content and find the search running slowly, we recommend opting for a server side search engine such as Algolia or Google (see below).

### Algolia

1. Register a **free** [Algolia](https://www.algolia.com) account and follow their wizard to create a new search app 
1. Build your site by running the `hugo` command in Terminal or Command Prompt
1. Upload the generated `public/index.json` file to the *Indicies* page in your Algolia dashboard
1. Paste the Algolia *App ID*, *API Key*, and *Index Name* from the *Indicies* and *API Keys* pages of your Algolia Dashboard into the `[search.algolia]` section in `config/_default/params.toml`
1. Under `[search]` in `config/_default/params.toml`, set `engine = 2` to activate the Algolia search engine
1. Serve (or build and upload) your site and test out the shiny new search widget on your home page :smile:

Note that whenever your content changes (e.g. you add a new page), you will need to re-build and re-upload the search index to Algolia.

## Disable

To disable searching, open `config/_default/params.toml` and set `engine = 0` in the `[search]` section.  

## Alternatives

Alternative search providers, such as Google search, are not integrated with Wowchemy, but can be implemented by creating your own custom widget. For example,

1. Create a [custom widget]({{< relref "/page-builder.md" >}}) in your `/content/home/` folder
1. Signup for [Google Custom Search Engine](https://cse.google.com/cse/)
1. Paste the HTML which Google provide into the body of your custom widget
