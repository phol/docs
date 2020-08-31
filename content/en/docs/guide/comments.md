---
title: Add comments
date: 2020-07-24
type: book
---

Wish to empower users to comment on your pages?

Wowchemy supports the following comment providers:

- [Disqus](https://disqus.com)
  - widely adopted but not particularly minimal and may contain adverts
- [Commento](https://commento.io)
  - privacy focussed with support for threaded Markdown comments

You may also add your own comment provider by overriding the comments file with the code from your provider.

To configure the provider, open `config/_default/params.toml`, scroll down to the `[comments]` section, and change `engine` to the provider you wish to use.

For Disqus, copy your `shortname` from your Disqus admin panel and paste it in the Disqus config section:

```toml
[comments.disqus]
  shortname = ""  # Paste the shortname from your Disqus dashboard.
  show_count = true  # Show comment count in page header? (true/false)
```

## Choose where users can comment

Under the `[comments]` section, you also have the option to choose which types of pages a user may comment on. Simply add the type of page (if it's not already in the list) and set it's value to `true` to enable comments. For example,

```toml
commentable = {page = true, post = true, book = true, project = true, publication = true, talk = true}
```

Alternatively, you can make page specific exceptions to this rule by adding `commentable: true` (or `false`) to the front matter of a page that you wish to enable/disable comments on.
