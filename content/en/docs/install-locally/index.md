---
title: Edit your site on your PC
linktitle: Edit on your PC
date: 2016-04-20
type: book
weight: 20
---

We highly **recommend** the [**one-minute Github/Gitlab install** using your web browser]({{< relref "install.md" >}}) **before** considering following the steps on this page to download and edit your site on your computer.

Alternatively, we can skip the Github install for now, edit your site directly on your computer, and [deploy later to your preferred provider]({{< relref "deployment.md" >}}).

For **beginners**, we recommend using the [cloud editing tools]({{< relref "install.md" >}}) rather than setting up an editing environment on your computer.

## Prerequisites

Before downloading your site, lets first install [_Hugo Extended_](https://gohugo.io/getting-started/installing/) and [its prerequisites](https://gohugo.io/hugo-modules/use-modules/#prerequisite).

Choose your operating system below to get started.

### Windows

Open the Windows [Powershell 5](https://aka.ms/wmf5download) app, installing it if necessary.

Install _Scope_, the package manager for Windows, by pasting the following commands into Powershell and pressing the  _Enter_ ↵ key:

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
iwr -useb get.scoop.sh | iex
```

Press `Y` and enter if asked `Do you want to change the execution policy?`.

Install Hugo and its dependencies:

```sh
scoop install git openssh go hugo-extended
```

### Mac

Open the **Terminal** app.

Install _Homebrew_, the Mac package manager, by pasting the following command and pressing the _Enter_ ↵ key:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Apply any Homebrew updates:

```
brew update && brew upgrade
```

Install Hugo and its dependencies:

```sh
brew install git golang hugo
```

Open the hidden `~/.zshrc` (or `~/.bashrc`) file in a text editor, add the following line, and restart your Terminal app so that Hugo can find the location of its Go dependency.

```sh
export PATH=$PATH:/usr/local/go/bin
```

### Linux

For *Ubuntu* based distributions:

 - [Download](https://github.com/gohugoio/hugo/releases) the Hugo Extended installer for Debian (`hugo_extended_<VERSION>_Linux-64bit.deb`) and double-click the downloaded file to install with _Ubuntu Software Center_.

For other Linux distributions:

- [Download](https://github.com/gohugoio/hugo/releases) the Hugo Extended binary (`hugo_extended_<VERSION>_Linux-64bit.tar.gz`)
- Extract the download and move the `hugo` app to your website folder
  - Or, better yet, [move the `hugo` app to your app folder and add Hugo to the system path](https://gohugo.io/getting-started/installing/#binary-cross-platform)

Install Hugo's Go dependency using [Snap](https://snapcraft.io/go):

```sh
sudo snap install --classic go
```

<!--
### Docker

Guide coming soon. Ask on our Discord.
-->

### Troubleshooting

For issues installing Hugo Extended, [ask the Hugo community](https://discourse.gohugo.io).

## Download a Template

If you already [created your site with Github]({{< relref "install.md" >}}):

 - locate your [Github](https://github.com/) repository, and either download the ZIP or use Git clone to download it
 
{{< figure src="download.png" title="" numbered="false" width="50%" >}}

**Otherwise**, create a new site by downloading a [Starter Template]({{< relref "/templates" >}}) either directly, or using Git:

- [Download _Academic_ Template](https://github.com/wowchemy/starter-academic/archive/master.zip)
  - Or with Git: `git clone https://github.com/wowchemy/starter-academic.git`
- [Download _Blog_ Template](https://github.com/wowchemy/starter-blog/archive/master.zip)
  - Or with Git: `git clone https://github.com/wowchemy/starter-blog.git`
- [Download _Book_ Template](https://github.com/wowchemy/starter-book/archive/master.zip)
  - Or with Git: `git clone https://github.com/wowchemy/starter-book.git`

If you downloaded a template, **extract the ZIP** file's contents to a folder.

Then open your **Terminal** (Mac/Linux) or **Powershell** (Windows) app and [use the `cd` command to navigate](https://www.4winkey.com/windows-10/change-directory-in-cmd-on-windows-10-via-command-line.html) to your website folder.

- On Windows, for example: `cd ~\Downloads\starter-academic-master\starter-academic-master\`
- On Mac or Linux, for example: `cd ~/Downloads/starter-academic-master/starter-academic-master/`

View your site by running the following command:

```sh
hugo server
```

Hugo then provides you with a link (e.g. `http://localhost:1313/`) to open in your web browser.

### Convert an old Academic Kickstarter site

If you have an existing site based on the Academic Kickstarter Template that was created before 3rd September 2020, it may need converting to use Hugo's new modular system.

Open your **Terminal** (Mac/Linux) or **Powershell** (Windows) app and [use the `cd` command to navigate](https://www.4winkey.com/windows-10/change-directory-in-cmd-on-windows-10-via-command-line.html) to your website folder.

Remove the Git submodule for Academic:

```sh
git submodule deinit themes/academic    
git rm themes
```

(Alternatively, deleting the `.gitmodules` file and the `themes` folder will remove most of the old system.)

Then [update `config/_defaults/config.toml`](https://github.com/wowchemy/starter-academic/blob/master/config/_default/config.toml):

- Remove `theme = "academic"`
- Add to the bottom of the file:
  ```toml
  [module]
    [[module.imports]]
      path = "github.com/wowchemy/wowchemy-hugo-modules/wowchemy"
  ```

## Install a Markdown Editor

Choose a Markdown editor. If you're unsure, we recommend Typora.

### Typora

[Get Typora](https://typora.io/), a beautifully simple and user-friendly editor with support for visualizing technical content, such as math and diagrams.

### Visual Studio Code

[Get Visual Studio Code](https://code.visualstudio.com/), a popular editor with an active online community for support.

### JupyterLab

[Get JupyterLab](https://jupyter.org/install), a familiar editor for data analysts, data scientists, and researchers.

### RStudio

A popular editor with statisticians.

1. Open [RStudio](https://www.rstudio.com/products/rstudio/) and install *Blogdown*:

        install.packages("blogdown")

1. Open `academic.Rproj` from your site's folder, [downloading it if necessary](https://github.com/wowchemy/starter-academic/blob/master/academic.Rproj)

1. Workaround a [Blogdown bug](https://github.com/rstudio/blogdown/issues/359) by moving your site's `config/_default/config.toml` to `config.toml` at your project root

1. In the RStudio menu bar, choose **Addins > Serve Site** (clicking this button will call `blogdown:::serve_site()`)
   - Paste the local URL which RStudio provides (e.g. http://127.0.0.1:4321) into your web browser to preview your new site
   - Avoid using the integrated RStudio web browser as it is very outdated and buggy

**We recommend** saving R content as Markdown with the **`.Rmarkdown` file extension** rather than as HTML with the `.Rmd` extension.

## Unlock rewards

{{% alert thanks %}}
**We're full steam ahead on improving Wowchemy, and we need your help!**

- :heart: [**Become a backer** on Patreon or GitHub]({{< relref "/plans.md" >}}) and **unlock [these]({{< relref "/plans.md" >}}) rewards and extra features**
- ⭐️ [**Star** Wowchemy on **GitHub**](https://github.com/wowchemy/wowchemy-hugo-modules/)
- {{< icon name="twitter" pack="fab" >}} [**Share your new site** with the Wowchemy community](https://twitter.com/intent/tweet?text=I%27m%20creating%20a%20beautiful%20website%20using%20the%20Wowchemy%20Website%20Builder%20for%20%40GoHugoIO%20by%20%40GeorgeCushen!&amp;hashtags=MadeWithWowchemy&amp;url=https://wowchemy.com)
- :woman_technologist: [**Contribute** code, PR reviews, documentation, color themes, tutorials, etc.](https://github.com/wowchemy/wowchemy-hugo-modules/blob/master/.github/contributing.md)
{{% /alert %}}

## Edit your site

[Follow the step by step guide to setup your new site]({{< relref "get-started.md" >}}).

For inspiration, refer to the [Markdown content](https://github.com/wowchemy/starter-academic) which powers the [Academic Template](https://academic-demo.netlify.app/).
