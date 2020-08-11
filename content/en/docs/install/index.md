---
title: Create a site with Github/Gitlab
date: 2020-06-18
type: book
weight: 10
---

{{< figure src="featured.png" title="" >}}

{{% cta cta_link="https://app.netlify.com/start/deploy?repository=https://github.com/sourcethemes/academic-kickstart" cta_text="Create your **resumé** or **academic site** now with Github :rocket:" %}}

{{% cta cta_link="https://app.netlify.com/start/deploy?repository=https://github.com/sourcethemes/academic-starter-blog" cta_text="Create your **blog** now with Github :rocket:" %}}

{{% cta cta_link="https://app.netlify.com/start/deploy?repository=https://github.com/sourcethemes/academic-starter-book" cta_text="Create a **documentation site** or **notebook** with Github :rocket:" %}}

{{% cta cta_alt_link="../install-locally/" cta_alt_text="Alternatively, install on your computer" %}}

You'll be greeted with the welcome screen below.

Click the big _Connect To Github_ button on the welcome screen (or alternatively click the link underneath to connect with _Gitlab_):

{{< figure src="1-netlify-welcome.png" title="Netlify welcome screen" numbered="true" >}}

Login with your Github account (or create a new Github account):

{{< figure src="2-netlify-login.png" title="Login with your Github account (or create a new Github account)" numbered="true" width="50%" >}}

Click _Save & Deploy_ to create a repository for your site in Github:

{{< figure src="3-netlify-create-repo.png" title="Confirm creation of a repository for your site in Github" numbered="true" >}}

Netlify will now generate your new site. Generally this takes around 1 to 5 minutes, but can take longer during busy periods. You'll see the green "Published" notice appear under _Production Deploys_ once it has completed.

{{< figure src="4-netlify-deploy.png" title="Netlify will now generate your shiny new site" numbered="true" >}}

{{% alert warning %}}
In the very unlikely case the build fails with a red "Failed" notice, click on the notice, and review the log. During exceptionally busy periods the error may read `Error scheduling build` in which case, wait a minute and then click _Retry Deploy > Deploy Site_ to retry.
{{% /alert %}}

The random URL assigned to us by Netlify is quite irrelevant. Let's customize the URL to something more relevant to our site...

{{< figure src="4.1-domain-view.png" title="View your domain (URL)" numbered="true" >}}

Click _Edit site name_...

{{< figure src="4.2-domain-edit-button.png" title="Click _edit site name_" numbered="true" >}}

Enter your name, separating your first and last name with a hyphen (`-`) rather than a space.

Alternatively, enter an organisation name if you're creating a site for an organisation.

Some creativity may be required to find a subdomain that is freely available. Don't worry about finding the perfect subdomain as later, we'll [register our own custom domain name]({{< relref "domain.md" >}}) and connect it with our site.

{{< figure src="4.3-domain-edit-save.png" title="Click _edit site name_" numbered="true" >}}

Lastly, click _Save_ to update our Netlify subdomain.

Awesome! We can now visit the site at the URL you chose!

We'll see something similar to the [Demo website](https://academic-demo.netlify.app/), but without the demo content.

Now, let's personalize our shiny new site based on our requirements :star: :star: :star:

## Personalize your site

Login to [GitHub](https://github.com/) and view the `academic-kickstart` repository which you created in the steps above:

{{< figure src="5-github-repo.png" title="View your site's Markdown files on Github" numbered="true" >}}

Let's click through to the `config/_default/` folder:

{{< figure src="6-github-config-dir.png" title="" numbered="true" >}}

Following this guide, we can click a file within the `config/_default/` folder, click the pencil icon in the top right to edit the settings, and scroll to the bottom of the page to click the green `Commit changes` button to save the file. Optionally, when saving the file, we can add a message for our records, to describe the change.

First, let's edit `config.toml` to update our site with a title (such as your name or organisation) and the URL assigned to us by Netlify:

{{< figure src="7-github-config-view.png" title="" numbered="true" >}}
{{< figure src="8-github-config-edit.png" title="" numbered="true" >}}

Click the green `Commit changes` button to save the `config.toml` file:

{{< figure src="9-github-config-save.png" title="" numbered="true" >}}

Next, let's edit `params.toml` to choose a theme and decide which features we'd like to use on our site. The [Getting Started]({{< relref "get-started.md" >}}) guide walks us through the main options to personalize our site.

{{< figure src="10-github-params-view.png" title="" numbered="true" >}}
{{< figure src="11-github-params-edit.png" title="" numbered="true" >}}

Click the green `Commit changes` button to save the `params.toml` file:

{{< figure src="12-github-params-save.png" title="" numbered="true" >}}

A few minutes after saving (i.e. committing a file), your site will automatically update.

Next, let's setup the admin panel and use it to edit our author profile and begin adding content to our site!

## Edit content online

To **easily edit your site in a rich online editor in your browser**,

- [Login to Netlify](https://www.netlify.com/) and click the site you deployed with Netlify
- Go to **Settings > Identity**, and select **Enable Identity** service
- Under **Registration** preferences, select **Invite Only**
- Scroll down to **Services > Git Gateway**, and click **Enable Git Gateway**

Head over to **`YOUR_SITE.netlify.app/admin/`** to view your content management panel and begin publishing content, replacing `YOUR_SITE` with the subdomain assigned to you earlier in this guide (or your custom URL, in the form `YOUR-URL.com/admin/`)

{{< figure src="netlify-cms.png" title="" numbered="true" >}}

For support with _Netlify CMS_ admin panel, refer to the [Netlify CMS docs](https://www.netlifycms.org/docs/add-to-your-site/#authentication) and the very active [Netlify CMS community](https://www.netlifycms.org/community/).

Check out the [Content]({{< relref "managing-content.md" >}}) and [Elements]({{< relref "writing-markdown-latex.md" >}}) guides to learn about all the different kinds of content we can create with Academic.

Note that the preview window in the online editor is limited to rendering basic Markdown and doesn't accurately represent how your site will be rendered. However, it can be useful for getting started or writing on the go.

For the full experience of seeing exactly what you are editing, check out the next section to edit on your computer.

{{% alert info %}}
If you prefer not to use the admin panel, you can optionally delete the `admin` folder at `static/admin/` and set `netlify_cms = false` under the `[cms]` section of `config/_default/params.toml`.
{{% /alert %}}

## Personalize your homepage

View the [Homepage Builder]({{< relref "page-builder.md" >}}) guide to learn how to add widgets to the homepage or other widget pages.

Navigate to the `content/home/` folder in [Github](https://github.com/) to edit your homepage widgets or to create/remove widgets.

## Edit content on your computer

To edit your site in a Markdown editor on your computer, perform the steps in the [*Install with Git*]({{< relref "install-locally.md#install-with-git" >}}) guide.

We highly recommend using either the beautifully simple [Typora](https://www.typora.io) editor (which supports math and diagrams) or the incredibly popular free [Visual Studio Code](https://code.visualstudio.com/) editor for writing content.

Alternatively, to edit **Rmarkdown** content, check out the [*Install with RStudio*]({{< relref "install-locally.md#install-with-rstudio" >}}) guide.

## Inspiration

For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://academic-demo.netlify.app/).

## Unlock rewards

{{% alert thanks %}}
**We're full steam ahead on improving Academic, and we need your help!**

- :heart: [**Become a backer** on Patreon or GitHub]({{< relref "/plans.md" >}}) and **unlock [these]({{< relref "/plans.md" >}}) rewards and extra features**
- ⭐️ [**Star** Academic on **GitHub**](https://github.com/gcushen/hugo-academic)
- {{< icon name="twitter" pack="fab" >}} [**Share your new site** with the Academic community](https://twitter.com/intent/tweet?text=I%27m%20creating%20a%20beautiful%20website%20using%20the%20Academic%20Website%20Builder%20for%20%40GoHugoIO%20by%20%40GeorgeCushen!&amp;hashtags=MadeWithAcademic&amp;url=https://sourcethemes.com/academic/)
{{% /alert %}}

{{< poll_academic >}}
