---
title: Getting Started With the Page Builder
linktitle: Build your homepage
date: 2016-04-19
type: book
weight: 30
---

**Building beautiful pages is easy with Academic's widget system. No programming is required!**

Loading pre-made layouts is a great way to *kickstart* your new homepage. [Academic Kickstart]({{< relref "install.md" >}}) comes with some popular **Sections** preconfigured for this purpose. A **Widget** can be added inside each Section. Hence, you can have multiple instances of widgets, such as listing recent pages of different content types or categories.

Widgets empower you to fully customize your site. They display as sections on the homepage or on [widget pages]({{< relref "managing-content.md#create-a-widget-page" >}}). They can be added, removed, and positioned as desired.

Academic comes with the following widgets built-in. Additionally, third-party widgets can also be [developed](#develop-a-new-widget) and installed.

- [Blank](#blank) - add [any elements]({{< relref "writing-markdown-latex.md" >}}) such as an image gallery
- [Hero](#hero) - encourage visitors to perform an action (CTA)
- [About](#about) - introduce yourself
- [Featurette](#featurette) - showcase skills or key features of a product
- [Experience](#experience) - list your professional experience on a timeline
- [Accomplishments](#accomplishments) - showcase your (online learning) certificates and other achievements
- [Pages](#pages) - display recent blog posts, talks, and publications
- [Featured](#featured) - display featured (*sticky*) blog posts, talks, and publications
- [Contact](#contact) - display your contact details, including an optional contact form and map
- [Portfolio](#portfolio) - showcase your work or product features in a filterable portfolio
- [Tag cloud](#tag-cloud) - enable visitors to discover popular topics
- [People](#people) - introduce your team members
- [Slider](#slider) (carousel) - promote a lot of content in a small space

{{% alert thanks %}}
**We're full steam ahead on improving Academic, and we need your help!**

- :heart: [**Become a backer** on Patreon or GitHub]({{< relref "/plans.md" >}}) and **unlock [these]({{< relref "/plans.md" >}}) rewards and extra features**
- ⭐️ [**Star** Academic on **GitHub**](https://github.com/gcushen/hugo-academic)
- :woman_technologist: [**Contribute** code, PR reviews, documentation, color themes, tutorials, etc.](https://github.com/gcushen/hugo-academic/blob/master/.github/contributing.md)
{{% /alert %}}

## Using Widgets

Academic Kickstart includes instances of all the built-in widgets. Delete the sections in `content/home/` that you don't need (or set `active = false` in their front matter) and personalize the front matter options of the sections that you wish to keep by opening them in a text editor.

The sections (widget instances) in your `home/` folder can be renamed to anything you like (but use hyphens instead of spaces). Just remember to update your main menu in `config/_default/menus.toml` if you have a link to the widget instance.

### Add a widget to the homepage

To add a widget manually, copy the relevant widget from `themes/academic/exampleSite/content/home/` to your `content/home/` folder. 

Widget identifiers are set to their respective filenames, so a `content/home/about.md` widget can be linked from the navigation bar by setting the relevant URL as `"#about"` in `config/_default/menu.toml`.

This means that if you want to use multiple instances of a widget, each widget will be assigned a unique ID based on the filename that you set. You can then use that ID for linking, like in the above example.

### Remove a widget from the homepage

If you do not require a particular widget, you can simply delete any associated files from the `content/home/` folder.

To remove a navigation link from the top of the page, remove the associated `[[main]]` entry in `config/_default/menu.toml`.

### Position sections

The order that the homepage widgets are displayed in is defined by the `weight` parameter in each of the files in the `content/home/` directory. The widgets are displayed in ascending order of their `weight`, so you can simply edit the `weight` parameters as desired.

### Link to a section

You may wish to add a navigation link to the top of the page that points to a section. This can be achieved by adding something similar to the following lines to your `config/_default/menu.toml`, where the URL will consist of the first title word in lowercase:

```toml
[[main]]
    name = "Research"  # A name for the link.
    url = "#research"  # URL of the section.
    weight = 10  # Position of the link in the menu.
```

### Develop a new widget

This section guides developers to create custom widgets using HTML and CSS. You may also be interested in the [Blank widget]({{< relref "page-builder.md#blank" >}}).

Let's create a new widget, the *Awesome* widget. First create the `layouts/partials/widgets/` folder structure in the root of your site (**not in** `themes/academic/`).

Next, create the widget file `awesome.html` in your new `layouts/partials/widgets/` folder.

Now we can open `awesome.html` in a text editor and create our desired layout using HTML and [Hugo's Go Templating](https://gohugo.io/templates/introduction/). Styling can be performed by [adding new CSS styles via the Custom CSS feature]({{< relref "customization.md#customize-style-css" >}}). In this example, let's add the following code to our `awesome.html` widget which will display the section content in a large blue font:

```html
<div style="font-size: 2rem; color: blue">
  {{ .page.Content }}
</div>
```

Finally, we will instantiate the widget on the website by creating a Markdown file, `my-widget.md` in `content/home/` and adding the following front matter to the file:

```toml
+++
widget = "awesome"  # The name of the widget that you created.
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 1  # Order that this section will appear in.
+++

Everything is awesome!
```

Good luck creating your own widgets and feel free to [share them with the community](http://discuss.gohugo.io). You can also  [open a PR on Github](https://github.com/gcushen/hugo-academic/pulls) for your widget to be considered for integration as a core Academic widget. For inspiration, you can [check out how the in-built widgets were made](https://github.com/gcushen/hugo-academic/tree/master/layouts/partials/widgets).

## Personalizing Widgets

The parameters for each section consist of general options in addition to widget-specific options. When you open a section installed in the `content/home/` folder in a text editor, the available options will be displayed in the front matter (between the pair of `+++`).

Generally, if you write any text in the file body after a widget's front matter, your text will appear at the top of the widget. This can be useful for introducing the widget content.

A title and subtitle can be set for most widgets using the `title` and `subtitle` options respectively.

### Columns

The number of columns in a section can be configured for the **Blank** and **Portfolio** widgets. Valid options are:

- `"1"`: a single full-width column with the section content appearing directly underneath the section title (if set)
- `"2"`: two columns in the classic Academic layout with the the section title appearing on the left and the section content appearing on the right

For example:

```toml
[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "1"
```

### View

Several widgets have a `view` option to let you choose the layout of the widget. The following layouts are available: 

- 1 = List (previously Simple)
- 2 = Compact (previously Stream)
- 3 = Card (previously Detailed)
- 4 = Citation (previously APA and MLA), only available for publications
  - Optionally, edit the value of `citation_style` in `params.toml` to APA or MLA
- 5 = Showcase (large images), only available for projects

### Icons

Academic enables you to use a wide range of icons from [Font Awesome](https://fontawesome.com/icons?d=gallery) and [Academicons](https://jpswalsh.github.io/academicons/).

Icon pack "fab" includes the following **brand** icons:

- twitter, weixin, weibo, linkedin, github, facebook, pinterest, twitch, youtube, instagram, soundcloud
- [See all icons](https://fontawesome.com/icons?d=gallery&s=brands)

Icon packs "fas" and "far" include the following **general** icons:

- fax, envelope (for email), comments (for discussion forum)
- [See all icons](https://fontawesome.com/icons?d=gallery&s=regular,solid)

Icon pack "ai" includes the following **academic** icons:

- cv, google-scholar, arxiv, orcid, researchgate, mendeley
- [See all icons](https://jpswalsh.github.io/academicons/)
- To enable the academic icon pack in **v5+**, set `ai = true` under `[icon.pack]` in `params.toml`

Icon pack "emoji" gives you the ability to use **emojis as icons**

- [See all icons](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md)
- Enter the emoji shortcode, such as <code>:</code><code>heart</code><code>:</code>, in Academic's `icon` field
- **Academic v4.9+ is required to utilise the _emoji_ icon pack and can currently only be used in the Featurette (skills) widget.**

Icon pack "custom" gives you the ability to use **custom SVG icons**

- Create an SVG icon in your favorite image editor or download one from a site such as [Flat Icon](https://www.flaticon.com/)
- Place the custom SVG icon in `assets/images/icon-pack/`, creating the folders if necessary
- Reference the SVG icon name (without `.svg` extension) in the `icon` field
- **Academic v4.9+ is required to utilise the _custom_ icon pack and can currently only be used in the Featurette (skills) widget.**

### Background

A background can easily be applied to any homepage section. Choose from a range of background options including **color, gradient, and image**. Then choose either a dark or light text color, by setting `text_color_light`.

Once you have chosen the type of background, delete or comment out (by prefixing `#`) any unused options. For example, if you choose an image background, set the `image*` and `text_color_light` options and delete the rest (delete `color` and `gradient*`). For colors, any [HTML color name](https://html-color-codes.info/color-names/) or [Hex value](https://html-color-codes.info) is valid.

The following excerpt shows the front matter structure for defining a background:

```toml
[background]
  # Background color.
  color = "navy"
  
  # Background gradient.
  gradient_start = "#4bb4e3"
  gradient_end = "#2b94c3"
  
  # Background image.
  image = "background.jpg"  # Name of image in `static/media/`.
  image_darken = 0.6  # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.
  image_size = "cover"  #  Options are `cover` (default), `contain`, or `actual` size.
  image_position = "center"  # Options include `left`, `center` (default), or `right`.
  image_parallax = true  # Use a fun parallax-like fixed background effect? true/false

  # Text color (true=light or false=dark).
  text_color_light = true
```

Note that `image_size`, `image_position`, and `image_parallax` were added in Academic **v4.6.0**.

### Spacing

The spacing of sections can be controlled by specifying padding for the top, right, bottom, and left sides of sections.

For example, to make a section more compact, the following parameters can be added to the front matter of a section. This example will reduce the top and bottom spacing of the section to just 20 pixels (px).

```toml
[design.spacing]
  # Customize the section spacing. Order is top, right, bottom, left.
  padding = ["20px", "0", "20px", "0"]
```

### Style

It's possible to customize the style of a specific instance of a widget with CSS. For example, the font size of a section can be changed.

First, define your custom style in CSS using the [CSS Plugin]({{< relref "customization.md#customize-style-css" >}}) feature.

To apply your new style to a widget, set `css_class` in a widget's front matter. For example `css_class = "MY_CSS_CLASS"`, where `MY_CSS_CLASS` is the name of the CSS class which you defined in the previous step.

Custom CSS code can also be directly applied to a section using the `css_style` option.

```toml
[advanced]
 # Custom CSS. 
 css_style = ""
 
 # CSS class.
 css_class = ""
```

## Blank

You can use the Blank widget to **create your own home page sections**. Add page [**elements**]({{< relref "writing-markdown-latex.md" >}}), such as an image gallery, and [**personalize the section**](#personalizing-widgets) with a background etc.

For example, a new Markdown file can be created in `content/home/` with the following front matter to begin building your new section: 

```toml
widget = "blank"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "1"
```

The *Demo* homepage section in the Demo website provides an example of using a *Blank* widget. For inspiration, the associated file can be found at `themes/academic/exampleSite/content/home/demo.md`.

For advanced use cases, HTML code can even be added to the body of the file.

You may also be interested in [developing your own widgets](#develop-a-new-widget).

### Example sections created with the Blank widget

{{< figure library="1" src="docs/widget-blank-gallery.png" title="An image gallery created with the Blank widget." >}}

{{< figure library="1" src="docs/widget-blank-text.png" title="A text block and custom background created with the Blank widget." >}}

## Hero

The Hero widget can be used to encourage visitors to perform an action (CTA). It's the first thing that visitors see when they visit your website, and it influences the way your visitors feel and behave on your site.

Typically, the Hero widget is configured to include a hero image, a tagline and a call to action (CTA). There are other possibilities as well though, such as including a secondary action, note, and [background](#background).

{{< figure library="1" src="docs/widget-hero.png" title="The Hero widget can be used to encourage visitors to perform an action (CTA)." >}}

Edit the front matter of `home/hero.md` to add the primary action that you would like your visitors to perform.

For example, the following options can be added to your section front matter in order to include the Hero widget: 

```toml
widget = "hero"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Hero image (optional). Enter filename of an image in the `static/media/` folder.
hero_media = ""

# Call to action links (optional).
#   Display link(s) by specifying a URL and label below. Icon is optional for `[cta]`.
#   Remove a link/note by deleting a cta/note block.
[cta]
  url = "https://sourcethemes.com/academic/docs/install"
  label = "Get Started"
  icon_pack = "fas"
  icon = "download"
  
[cta_alt]
  url = "https://sourcethemes.com/academic/"
  label = "View Documentation"

# Note. An optional note to show underneath the links.
[cta_note]
  label = ""
```

In this example, we have [associated an icon](#icons) with the action (`[cta]` option).

## Featurette

As an individual, use the Featurette widget to showcase your skills and expertise. As an organization, use the widget to highlight the key features of your product or service.

{{< figure library="1" src="docs/widget-featurette.png" title="Showcase personal skills or product features with the Featurette widget." >}}

Edit the front matter of `home/skills.md` to add your skills/features. [Choose from a large range of icons to depict the skills/features](#icons).

For example, the following options can be added to your section front matter in order to include the Featurette widget: 

```toml
widget = "featurette"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Showcase personal skills or business features.
# Add/remove as many `[[feature]]` blocks below as you like.
# For available icons, see: https://sourcethemes.com/academic/docs/widgets/#icons
[[feature]]
  icon = "r-project"
  icon_pack = "fab"
  name = "R"
  description = "90%"
  
[[feature]]
  icon = "chart-line"
  icon_pack = "fas"
  name = "Statistics"
  description = "100%"  
  
[[feature]]
  icon = "camera-retro"
  icon_pack = "fas"
  name = "Photography"
  description = "10%"

# Uncomment to use emoji icons.
# [[feature]]
#  icon = ":smile:"
#  icon_pack = "emoji"
#  name = "Emojiness"
#  description = "100%"  

# Uncomment to use custom SVG icons.
# Place custom SVG icon in `assets/images/icon-pack/`, creating folders if necessary.
# Reference the SVG icon name (without `.svg` extension) in the `icon` field.
# [[feature]]
#  icon = "your-custom-icon-name"
#  icon_pack = "custom"
#  name = "Surfing"
#  description = "90%"
```

**Note: Academic v4.9+ is required to utilise the _emoji_ and _custom_ icon packs.**

## About

Introduce yourself to your readers.

{{< figure library="1" src="docs/widget-about.png" title="Introduce yourself to your readers with the About widget." >}}

[Setup a user profile]({{< relref "get-started.md" >}}) and then edit the front matter of `home/about.md` to associate the About widget with your username (name of the folder your created in `authors/`).

For example, the following options can be added to your section front matter in order to include the About widget: 

```toml
widget = "about"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Choose the user profile to display
# This should be the username of a profile in your `content/authors/` folder.
author = "admin"
```

## Experience

List your professional experience on a timeline.

{{< figure library="1" src="docs/widget-experience.png" title="With the Experience widget, you can list your professional experience on a timeline." >}}

Add your experience by editing the front matter of `home/experience.md`. For example:

```toml
widget = "experience"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Date format for experience
#   Refer to https://sourcethemes.com/academic/docs/customization/#date-format
date_format = "Jan 2006"

# Experiences.
#   Add/remove as many `[[experience]]` blocks below as you like.
#   Required fields are `title`, `company`, and `date_start`.
#   Leave `date_end` empty if it's your current employer.
#   Begin/end multi-line descriptions with 3 quotes `"""`.
[[experience]]
  title = "CEO"
  company = "GenCoin"
  company_url = ""
  location = "California"
  date_start = "2017-01-01"
  date_end = ""
  description = """
  Responsibilities include:
  
  * Analysing
  * Modelling
  * Deploying
  """

[[experience]]
  title = "Professor"
  company = "University X"
  company_url = ""
  location = "California"
  date_start = "2016-01-01"
  date_end = "2016-12-31"
  description = """Taught electronic engineering and researched semiconductor physics."""
```

{{% alert note %}}
The use of three quote marks (`"""`) in the above front matter example is a [TOML configuration syntax]({{< relref "front-matter.md" >}}) that enables us to easily write multi-line content in the front matter.
{{% /alert %}}

## Accomplishments

List your accomplishments including certificates and courses attended.

{{< figure library="1" src="docs/widget-accomplishments.png" title="List your accomplishments including certificates and courses attended." >}}

Add your accomplishments by editing the front matter of `home/accomplishments.md`. For example:

```toml
widget = "accomplishments"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Date format
#   Refer to https://sourcethemes.com/academic/docs/customization/#date-format
date_format = "Jan 2006"

# Accomplishments.
#   Add/remove as many `[[item]]` blocks below as you like.
#   `title`, `organization` and `date_start` are the required parameters.
#   Leave other parameters empty if not required.
#   Begin/end multi-line descriptions with 3 quotes `"""`.

[[item]]
  organization = "Coursera"
  organization_url = "https://www.coursera.org"
  title = "Neural Networks and Deep Learning"
  url = ""
  certificate_url = "https://www.coursera.org"
  date_start = "2018-10-01"
  date_end = ""
  description = ""

[[item]]
  organization = "edX"
  organization_url = "https://www.edx.org"
  title = "Blockchain Fundamentals"
  url = "https://www.edx.org/professional-certificate/uc-berkeleyx-blockchain-fundamentals"
  certificate_url = "https://www.edx.org"
  date_start = "2018-03-01"
  date_end = ""
  description = "Formulated informed blockchain models, hypotheses, and use cases."
  
[[item]]
  organization = "DataCamp"
  organization_url = "https://www.datacamp.com"
  title = "Object-Oriented Programming in R: S3 and R6 Course"
  url = ""
  certificate_url = "https://www.datacamp.com"
  date_start = "2017-07-01"
  date_end = "2017-12-21"
  description = ""
```

## Pages

List your recently published pages such as blog posts, talks, and publications.

{{< figure library="1" src="docs/widget-publications.png" title="List your recent pages." >}}

There are three sections in the demo that use the *Pages* widget. These include `home/posts.md`, `home/talks.md`, and `home/publications.md`.

Edit the front matter of a section to personalize the [view](#view) and other options shown below:

```toml
widget = "pages"  # Use the Pages widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Page type to display. E.g. post, talk, or publication.
  page_type = "post"
  
  # Choose how much pages you would like to display (0 = all pages)
  count = 5
  
  # Choose how many pages you would like to offset by
  offset = 0

  # Page order. Descending (desc) or ascending (asc) date.
  order = "desc"

  # Filter posts by a taxonomy term.
  [content.filters]
    tag = ""
    category = ""
    publication_type = ""
    exclude_featured = false
    exclude_past = false
    exclude_future = false
    
[design]
  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view = 2
```

## Featured

Highlight featured blog posts (e.g. announcements), publications, and talks. Featured pages are also known as *sticky* pages.

The Featured widget is similar to the Pages widget, but with a focus on *featured* content rather than *recent* content.

{{< figure library="1" src="docs/widget-featured.png" title="Highlight featured pages, such as blog posts or selected publications, with the Featured widget." >}}

The `featured.md` section in the demo uses the *Featured* widget.

Edit the front matter of a section to add the Featured widget and personalize its options such as the [view](#view):

```toml
widget = "featured"  # Use the Featured widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Page type to display. E.g. post, talk, or publication.
  page_type = "publication"
  
  # Choose how much pages you would like to display (0 = all pages)
  count = 0

  # Page order. Descending (desc) or ascending (asc) date.
  order = "desc"

  # Filter posts by a taxonomy term.
  [content.filters]
    tag = ""
    category = ""
    publication_type = ""
  
[design]
  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view = 3
```

## Contact

Communication is the cornerstone of almost any website, especially business sites. With Academic, you can easily add communicate elements including a contact form, social messaging links, appointment booking, and a map to your website. A well designed contact section is essential to network with other people, spark new business, and increase conversions.

{{< figure library="1" src="docs/widget-contact.png" title="With the Contact widget, you can add elements such as a contact form, social messaging links, appointment booking, and a map to your website." >}}

The contact widget will automatically display the following information according to what you entered in `config/_default/params.toml`:

- [contact form](#contact-form) or an email link (see section below)
- [contact links](#contact-links) such as for Twitter, Skype, Weixin, Weibo, Discussion Forums, etc.
- phone number
- address
- office hours
- appointment booking link
- map

For example, the following options can be added to your section front matter in order to include the Contact widget: 

```toml
widget = "contact"
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

# Automatically link email and phone?
autolink = true

# Email form provider
#   0: Disable email form
#   1: Netlify (requires that the site is hosted by Netlify)
#   2: formspree.io
email_form = 2
```

### Contact links

Academic enables you to use a wide range of icons in your contact links. [Learn more about icons](#icons).

### Contact form

You can choose whether to display simply an email address or a contact form. This can be chosen in `content/home/contact.md` by setting the `email_form` option. If set to 0, it will display your email address as a link, based on the value of `email` that you entered in `config/_default/params.toml`. If set to 1, it will use [Netlify](https://www.netlify.com/docs/form-handling/) to add a contact form with a captcha test so that visitors can send you email and spam from bots is prevented.

{{% alert note %}}
The Netlify option is only available if you are hosting your site with Netlify. In this case, user messages to you will be sent to your Netlify account admin panel. A webhook can be created in your Netlify account if you wish to forward messages to your email address. When using Netlify to provide the contact form, you do not need to provide a value for `email` in `config/_default/params.toml` since the messages will be delivered to your Netlify admin panel.
{{% /alert %}}

Otherwise, if set to 3, the widget will display a contact form using the `email` in `config/_default/params.toml` and will use the [Formspree](https://formspree.io) service for sending the email to you. For this method, simply send yourself a test message after you have configured the contact form. Formspree will then send you an email to verify your new account with them. Note that **Formspree is usually blocked for Chinese visitors** as it uses Google reCAPTCHA (unless you upgrade to Formspree's paid plan in order to disable reCAPTCHA).

## Portfolio

With the Portfolio widget you can showcase your work and optionally enable visitors to filter the items. 

{{< figure library="1" src="docs/widget-portfolio-card.png" title="Showcase your work or product features with the Portfolio widget." >}}

Different [views](#view) are available for the content. The default view is a masonry card view made famous by Pinterest.com. Other views include a large image showcase view, a compact view with image, and a simple list view. For the *showcase* view, the `flip_alt_rows` option can be set to `true` to horizontally flip alternate rows - a style which is commonly seen on many popular sites and landing pages that showcase product features by placing large images and text side-by-side.

The widget is configurable in a one or two column structure by setting the `columns` option.

Associate your pages with tags by placing the tags option in the front matter of your pages (e.g. `tags = ["A Tag", "Another Tag"]`). The Portfolio widget can then be configured to let visitors filter results by tags. To add a filter button, add or edit a `[[content.filter_button]]` option (see below), where `name` is the filter text and `tag` is the name of the tag to filter by (type `*` to show all items).

The `projects.md` section in the demo uses the *Portfolio* widget.

To show the widget in a section, reference it in your section's front matter:

```toml
widget = "portfolio"  # Use the Portfolio widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Page type to display. E.g. project.
  page_type = "project"
  
  # Filter toolbar (optional).
  # Add or remove as many filters (`[[content.filter_button]]` instances) as you like.
  # To show all items, set `tag` to "*".
  # To filter by a specific tag, set `tag` to an existing tag name.
  # To remove toolbar, delete/comment all instances of `[[content.filter_button]]` below.
  
  # Default filter index (e.g. 0 corresponds to the first `[[filter_button]]` instance below).
  filter_default = 0
  
  [[content.filter_button]]
    name = "All"
    tag = "*"
  
  [[content.filter_button]]
    name = "Deep Learning"
    tag = "Deep Learning"
  
  [[content.filter_button]]
    name = "Other"
    tag = "Demo"

[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "2"

  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact  
  #   3 = Card
  #   5 = Showcase
  view = 3

  # For Showcase view, flip alternate rows?
  flip_alt_rows = false
```

## Tag Cloud

Enable visitors to easily discover popular topics.

{{< figure library="1" src="docs/widget-tags.png" title="Visitors can easily discover popular topics with the Tag Cloud widget." >}}

Associate your pages with tags by placing the tags option in the front matter of your pages (e.g. `tags = ["A Tag", "Another Tag"]`). The Tag Cloud widget will then display your tags. The more popular a tag is, the larger its font.

The `tags.md` section in the demo uses the *Tag Cloud* widget.

To show the widget in a section, reference it in your section's front matter:

```toml
widget = "tag_cloud"  # Use the Tag Cloud widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Choose the taxonomy from `config.toml` to display (e.g. tags, categories)
  taxonomy = "tags"
  
  # Choose how many tags you would like to display (0 = all tags)
  count = 20

[design]
  # Minimum and maximum font sizes (1.0 = 100%).
  font_size_min = 0.7
  font_size_max = 2.0
```

## People

Introduce your team members.

{{< figure library="1" src="docs/widget-people.png" title="Introduce your team members with the People widget." >}}

The People widget displays photos of people within your team or organisation, and links to their user profile page. You can choose which users to display and in which order to display them by using *user groups*.

First, [create a user account]({{< relref "get-started.md#introduce-yourself" >}}) for each user that your wish to display. (This can also be performed by duplicating the example `content/authors/admin/` folder for each user and modifying its contents appropriately.)

Add each user to a user group using the `user_groups` option in the user account at `content/authors/<USERNAME>/_index.md`. For example setting `user_groups = ["Researchers", "Visitors"]` in a user account will add that user to the *Researcher* and *Visitors* groups which we can display in the People widget.

The _Meet The Team_ section in the demo with filename `people.md` uses the *People* widget. Set `active = true` in its front matter to view the section.

Edit the front matter of a section to add the People widget. You can personalize options such as the user groups to display and whether you would like the show each user's social links and interests:

```toml
widget = "people"  # Use the People widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Choose which groups/teams of users to display.
  #   Edit `user_groups` in each user's profile to add them to one or more of these groups.
  user_groups = ["Principal Investigators",
                 "Researchers",
                 "Grad Students",
                 "Administration",
                 "Visitors",
                 "Alumni"]

[design]
  # Show user's social networking links? (true/false)
  show_social = false

  # Show user's interests? (true/false)
  show_interests = true
```

**Person not showing in the People widget?**

Hugo will only generate a user's profile if the user is associated with a piece of content by having their username appear in the `authors` field of a page's front matter. Therefore, if a user does not appear in the widget, edit the user's profile to add an `authors` field containing their username (folder name) to force Hugo to generate their profile even though it's not directly associated with any content. For example,

```
authors:
- <USERNAME>
```

## Slider

Promote a lot of content in a small space with a slider (carousel). Users can click the left and right arrows to move between slides, or you can automate slide transitions with a timer.

{{< figure library="1" src="docs/widget-slider.png" title="Promote a lot of content in a small space with the Slider (carousel) widget." >}}

The `slider.md` section in the demo uses the *Slider* widget. Set `active = true` in its front matter to view the section.

Each slide is defined as an `[[item]]` in the section front matter. A title and content can be set for each slide - Markdown formatting  and emojis can be used. The content of each slide can be left, center, or right aligned.

Optionally, a call-to-action (CTA) button can be added to a slide to encourage visitors to perform an action. The snippet below provides an example of using the `cta_*` options to add a CTA button to a slide.

Customize each slide with a background color (`overlay_color`) or image (`overlay_img`). The text color for slides is always white unless it is overrided using custom CSS styling.

To show the widget in a section, reference it in your section's front matter:

```toml
widget = "slider"  # Use the Slider widget
headless = true  # This file represents a page section.

# ... Put Your Section Options Here (section position etc.) ...

# Slide interval.
# Use `false` to disable animation or enter a time in ms, e.g. `5000` (5s).
interval = false

# Minimum slide height.
# Specify a height to ensure a consistent height for each slide.
height = "300px"

# Slides.
# Duplicate an `[[item]]` block to add more slides.
[[item]]
  title = "Hello"
  content = "I am center aligned :smile:"
  align = "center"  # Choose `center`, `left`, or `right`.

  # Overlay a color or image (optional).
  #   Deactivate an option by commenting out the line, prefixing it with `#`.
  overlay_color = "#666"  # An HTML color value.
  overlay_img = "headers/bubbles-wide.jpg"  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.

  # Call to action button (optional).
  #   Activate the button by specifying a URL and button label below.
  #   Deactivate by commenting out parameters, prefixing lines with `#`.
  cta_label = "Get Academic"
  cta_url = "https://sourcethemes.com/academic/"
  cta_icon_pack = "fas"
  cta_icon = "graduation-cap"

[[item]]
  title = "Left"
  content = "I am left aligned :smile:"
  align = "left"

  overlay_color = "#555"  # An HTML color value.
  overlay_img = ""  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.

[[item]]
  title = "Right"
  content = "I am right aligned :smile:"
  align = "right"

  overlay_color = "#333"  # An HTML color value.
  overlay_img = ""  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.
```

You may also be interested in the **[Hero](#hero) widget**.
