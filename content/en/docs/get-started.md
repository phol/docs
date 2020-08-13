---
title: Getting started
date: 2016-04-20
type: book
weight: 25
---

This quick tutorial will show you how to setup and use Academic.

## Choose the right theme for you

Check out the [available themes]({{< relref "../templates.md" >}}) and have fun choosing a design you love.

Once you have settled on a theme, edit your `config/_default/params.toml` file in a text editor and set the `theme` option to the name of the chosen theme.

{{% alert note %}}
If you are unfamiliar with setting options in a TOML file, you can [learn more about this human-friendly configuration syntax here]({{< relref "./front-matter.md" >}}).
{{% /alert %}}

Your theme comes with a font set to style your titles and text, but you may choose to override it by specifying one of the available font sets with the `font` option:

- **Minimal** (modern)
- **Classic** (original Academic v1 style)
- **Rose** (traditional serif)
- **Mr Robot** (futuristic)

The font size may be adjusted from _XS_ (extra small) to _XL_ (extra large) with the `font_size` option.

Don't worry if you are not 100% happy with the colors or font yet, as these can be [fully customized]({{< relref "customization.md" >}}) later.

## Choose the right layout for you

Academic has a template for you whether you are you creating a website for your CV, academic research, blog, course, lab, business, photography, portfolio, or restaurant!

What kind of content would you like to publish? Academic supports:

- **Pages**: any general content
- **Widget Pages**: pages that can consist of numerous widgets, such as the **homepage**
- **Posts**: blog posts or news
- **Publications**: import your research publications from BibTeX
- **Online Courses**: share knowledge online
- **Projects**: publish your portfolio or projects
- **Notes**: collaborate on content across notebooks, sections, and pages
- **Software Documentation**: document your software projects
- **Talks/Events**: publish any talks which you are presenting
- **Slides**: write slides very efficiently with Markdown, present them at your talk, and share them online

Once you have decided on the type of content that you would like to publish, take a look at the [available homepage widgets]({{< relref "page-builder.md" >}}) and consider which ones would be most relevant to you.

Then, open your `content/home/` folder and set the `active` parameter to either `true` or `false` for each widget depending on if you wish to display it or not. Widgets that you don't need can alternatively be deleted rather than setting `active` to `false`. You can also add more instances of widgets, such as to show blog posts or publications with specific tags, or to add more _Blank_ widgets with your own custom content and design.

Next, let's **position the widgets** according to your preference. To move a widget up or down, increase or decrease the value of the `weight` parameter in each widget which you activated. The widgets will be ordered in ascending order of these weights and there is no need for the weights to be consecutive numbers.

{{% alert note %}}
If your `content/home/` folder is empty, populate it from the [example]({{< relref "install.md#inspiration" >}}).
{{% /alert %}}

## Customize it

After selecting a theme and a layout, make it your own.

### Core parameters

The core parameters for the website can be edited in the `config/_default/params.toml` file.

Edit your personal/business details under the _Contact Details_ section:

- Any details entered here will be displayed in the _Contact_ widget (if used)
- For organizations, some contact details (such as phone) may be used to enrich search results (such as on Google)
- To hide a contact field, simply clear the value to `""` or comment the line out by prefixing it with a hash (`#`) 
- The [contact form can be configured]({{< relref "page-builder.md#contact" >}}) separately in the front matter of the *Contact* widget itself

If you are an **organization or project**,

- edit your `site_type` to reflect the nature of your business
- add your organization or project name under `org_name`
- save your **logo** image as `logo.png` and upload the image to the `assets/images/` folder, creating the `assets` and `images` folders if they don't already exist at the root of your site

Enable **rich content** for your site under the _Site Features_ section. If you write technical content, consider enabling the following options, otherwise set these options to `false`:

  - [Code syntax highlighting](https://academic-demo.netlify.app/post/writing-technical-content/#code) with `highlight = true`
  - [LaTeX math](https://academic-demo.netlify.app/post/writing-technical-content/#math) with `math = true`
  - [Mermaid diagram drawing](https://academic-demo.netlify.app/post/writing-technical-content/#diagrams) with `diagram = true`

The **Privacy Pack** can also be activated from the _Site Features_ section. When the privacy pack is enabled, a cookie consent message will be shown to visitors (linking to your Privacy Policy) and visitor IPs anonymized in Google Analytics (if enabled).

To add a **Privacy Policy**, create a `privacy.md` file in your `content` folder and remove any `draft` option from the front matter to publish it.

Similarly, to add **Legal Terms**, create a `terms.md` file. Links to these documents will automatically appear in your site footer.

### Introduce yourself

By default, a superuser is created with the username *admin* and corresponding user profile located at `content/authors/admin/_index.md`. Let's open this file in a text editor and edit this file to make it *your* profile:

- Add your display name (typically your full name) to the `title` field
- Add your role/position or tagline to the `role` field
- Write a brief sentence to describe yourself in the `bio` field - this can appear in the list of authors after the page content
- Edit the `organizations` that you are affiliated with, or set this to `[]` to hide it
- List your interests or hobbies in `interests`, or set this to `[]` to hide it
- List your main qualifications using the `education` --> `courses` block
  - These blocks can be created or deleted as required
  - To hide qualifications, delete these blocks or comment out the lines by prefixing them with a hash (`#`)
- Add your social or academic networking links
  - These are defined as instances of `social` and can be created or deleted as required

Now let's add a biography or some fun facts about you after the front matter (i.e. after the last `---` line). You can utilize [Markdown and shortcodes for formatting]({{< relref "./writing-markdown-latex.md" >}}).

To display an avatar, place a square cropped portrait photo named `avatar` into your profile folder at `content/authors/admin/`, overwriting the example image. Alternatively, if you have an existing Gravatar/Wordpress avatar, you can use it by setting `gravatar` to `true` in `config/_default/params.toml` and entering your associated `email` address in `content/authors/admin/_index.md`. Note that you can delete the example `avatar` image to disable the avatar feature.

Once you have setup your account, **your username can be referenced in the `authors` field in the front matter of content**, as per the demo post.

Your _display name_, entered in your user profile, will then automatically appear in the page metadata. You can also enter additional names in the `authors` field of pages, with the option to create a user profile for them too if you wish. If a user profile doesn't exist for an author, their name will appear exactly as you entered it in the front matter.

{{% alert note %}}
The superuser username can be changed from *admin* by renaming the `admin` folder. Usernames must be lowercase with any spaces replaced with hyphens (`-`).
{{% /alert %}}

{{% alert warning %}}
If you change a username, you may wish to update any references to it from the `author` field of the About widget (`content/home/about.md`) and the `authors` field in the front matter of any pages which reference that user.
{{% /alert %}}

### Menu

The navigation menu can be edited in the `config/_default/menu.toml` file:

The `[[main]]` entries define the navigation links at the top of the website. They can be added or removed as desired, based on the layout which you chose above.

To link to a section of the homepage, use the form `#<section-filename>` where `<section-filename>` is the filename (without .md extension). For example, `#posts` references a section with filename `posts.md`. You can rename your section files in `content/home/`, just remember to use a dash (`-`) instead of spaces in the filename. 

{{% alert note %}}
To create a dropdown sub-menu, add `identifier = "a-unique-reference"` to the parent item and `parent = "a-unique-reference"` to the child item, replacing `a-unique-reference` with a unique reference of your choice.
{{% /alert %}}

Read more about the underlying Hugo menu system [here](https://gohugo.io/content-management/menus/).

### Add your content

Refer to our guide on [managing content]({{< relref "managing-content.md" >}}) to create your own content such as blog posts, publications, online courses, talks, and projects etc.

### Remove any unused example pages

Tidy up your site by [deleting any unused pages]({{< relref "managing-content.md#removing-content" >}}) leftover from the example template.

{{% alert note %}}
You will likely want to keep the `_index.md` files (notice the underscore prefix) as they configure the archive page for each content type (e.g. an index of all your blog posts).
{{% /alert %}}

Your Markdown-based site structure will be similar to:

- 📄 [LICENSE.md](https://github.com/sourcethemes/academic-kickstart/blob/master/LICENSE.md)
- 📄 [README.md](https://github.com/sourcethemes/academic-kickstart/blob/master/README.md)
- 📄 [academic.Rproj](https://github.com/sourcethemes/academic-kickstart/blob/master/academic.Rproj) - (optional) For RStudio users, otherwise can be deleted
- 📁 [assets](https://github.com/sourcethemes/academic-kickstart/blob/master/assets)
  - 📁 [images](https://github.com/sourcethemes/academic-kickstart/blob/master/assets/images)
    - 📄 [icon.png](https://github.com/sourcethemes/academic-kickstart/blob/master/assets/images/icon.png) - (optional) add your website icon here
    - 📄 logo.png - (optional) add your logo here
- 📁 [config](https://github.com/sourcethemes/academic-kickstart/blob/master/config)
  - 📁 [_default](https://github.com/sourcethemes/academic-kickstart/blob/master/config/_default)
    - 📄 [config.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/config/_default/config.toml) - define your site name and URL
    - 📄 [languages.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/config/_default/languages.toml) - edit this for non-English or multilingual sites
    - 📄 [menus.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/config/_default/menus.toml) - define your site menu
    - 📄 [params.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/config/_default/params.toml) - personalize your site
- 📄 [config.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/config.toml) - (optional) a dummy file for RStudio compatibility - non-RStudio users can delete
- 📁 [content](https://github.com/sourcethemes/academic-kickstart/blob/master/content)
  - 📁 [authors](https://github.com/sourcethemes/academic-kickstart/blob/master/content/authors) - user profiles
    - 📁 [admin](https://github.com/sourcethemes/academic-kickstart/blob/master/content/authors/admin) - your username (can rename)
      - 📄 [_index.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/authors/admin/_index.md) - your user profile
      - 📄 [avatar.jpg](https://github.com/sourcethemes/academic-kickstart/blob/master/content/authors/admin/avatar.jpg) - update with a photo of yourself or delete to not show any photo
  - 📁 [home](https://github.com/sourcethemes/academic-kickstart/blob/master/content/home) - your homepage - [personalize the homepage with widgets]({{< relref "page-builder.md" >}})
  - 📁 [post](https://github.com/sourcethemes/academic-kickstart/blob/master/content/post)
    - 📄 [_index.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/post/_index.md) - (optional) an archive of blog posts
  - 📄 [privacy.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/privacy.md) - (optional) your privacy policy
  - 📁 [publication](https://github.com/sourcethemes/academic-kickstart/blob/master/content/publication)
    - 📄 [_index.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/publication/_index.md) - (optional) an archive of publications
  - 📁 [talk](https://github.com/sourcethemes/academic-kickstart/blob/master/content/talk)
    - 📄 [_index.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/talk/_index.md) - (optional) an archive of talks
  - 📄 [terms.md](https://github.com/sourcethemes/academic-kickstart/blob/master/content/terms.md) - (optional) your site's terms and conditions
- 📁 [data](https://github.com/sourcethemes/academic-kickstart/blob/master/data)
  - 📄 [page_sharer.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/data/page_sharer.toml) - (optional) customize social sharing buttons
- 📄 [netlify.toml](https://github.com/sourcethemes/academic-kickstart/blob/master/netlify.toml) - (optional) defines Hugo version for deploying with Netlify
- 📁 [scripts](https://github.com/sourcethemes/academic-kickstart/blob/master/scripts) - (optional) scripts to maintain the template repository - **can be deleted**
- 📁 [static](https://github.com/sourcethemes/academic-kickstart/blob/master/static)
  - 📁 [admin](https://github.com/sourcethemes/academic-kickstart/blob/master/static/admin) - (optional) your Netlify CMS admin panel
- 📄 [update_academic.sh](https://github.com/sourcethemes/academic-kickstart/blob/master/update_academic.sh) - (optional) a script to help update Academic
- 📄 [view.sh](https://github.com/sourcethemes/academic-kickstart/blob/master/view.sh) - (optional) a script to view your site locally

## View your site

If you installed on your computer with **Git** or **ZIP**, view your new website by running the `hugo server` command.

If you installed using **RStudio**, run `blogdown::serve_site()` to preview your site in your web browser. We recommend previewing your site in your normal web browser as the in-built RStudio web browser is outdated and buggy.

Now visit [localhost:1313](http://localhost:1313) and your new Academic powered website will appear. Otherwise, if using **Netlify**, they will provide you with your URL.

## Deploy your site

Before deploying your site, there are some final options we can set in `config/_default/config.toml`:

- Set `title` to your desired website title, such as your name or business name
- Set `baseurl` to your website URL (this can be provided by your host such as [Netlify]({{< relref "deployment.md" >}}))
  - You can make a great impression on your visitors with your own [**custom domain name**]({{< relref "domain.md" >}})
  - If you don't have your URL/domain yet, come back to add it later - some features may not fully function until it is added

Publish your site to the world by following the [deployment steps]({{< relref "deployment.md" >}}).

## Support Academic

**Has Academic helped you?**

**Academic is a free open source platform. [Please kindly consider supporting further development.]({{< relref "/plans.md" >}})**
