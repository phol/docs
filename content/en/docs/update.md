---
title: Update
date: 2016-04-20
type: book
weight: 75
---

The update process consists of:

1. [Preparation](#preparation)
2. [Updating Academic](#update-academic)
3. [Migrating your content](#migrate-content) front matter and configuration by applying any relevant breaking changes

Feel free to [star Academic on Github](https://github.com/gcushen/hugo-academic/) to help keep track of updates and check out the [release notes](/academic/updates/) to learn what's new.

## Preparation

Before updating Academic, it is strongly recommended to make a full **backup** of your website folder (including `themes/academic/`).

Then, **record your current version**, so that after you update Academic, you can apply any relevant breaking changes to the TOML/YAML site configuration and front matter in your `content/` folder. To find your current version, look in `themes/academic/data/academic.toml`. Note that if you installed the *master* version rather than a specific release, then extra care should be taken (such as by checking the git log if you installed with git) as you may be in-between versions.

{{% alert note %}}
Academic Kickstart comes with an [update script](https://github.com/sourcethemes/academic-kickstart/blob/master/update_academic.sh) to check for available updates.
{{% /alert %}}

## Update Academic

Please follow the method below which corresponds to how you originally installed Academic:

### If you installed Blog or Book Starter

Install [Hugo Extended]({{< relref "./install-locally/index.md" >}}) if it's not already on your machine.

Install Hugo's _Go_ dependency

- with [Brew](https://brew.sh/) on Mac: `brew install go`
- [Windows and Linux](https://golang.org/dl/)

Open a Terminal (Command Prompt) and navigate to your site's folder using the [`cd` command](https://linuxize.com/post/linux-cd-command/).

Update to get the very latest developments:

```
hugo mod get github.com/gcushen/hugo-academic@master
```

Alternatively, update to the latest official release:

```
hugo mod get -u
```

[Migrate your content](#migrate-content) front matter and configuration if necessary by applying any relevant breaking changes.

### If you installed Academic Kickstart

By default, Academic is installed as a Git sub-module which can be updated by opening a Terminal at the root of your site and running the following command from :

```bash
git submodule update --remote --merge
cd themes/academic
git checkout <VERSION>
```

where `<VERSION>` is the [version](https://github.com/gcushen/hugo-academic/releases) in the form *vX.X.X* that you wish to update to. Otherwise, to update to the latest development version, substitute `<VERSION>` with *master*.

### If you installed by Git cloning *hugo-academic*

Before updating for the first time, the remote *origin* repository should be renamed to *upstream*:

    cd themes/academic
    git remote rename origin upstream

To list all available updates:

    cd themes/academic
    git fetch upstream
    git log --pretty=oneline --abbrev-commit --decorate HEAD..upstream/master

Then, update by running:

    git checkout <VERSION>
    git pull upstream

where `<VERSION>` is defined in the previous section.

### If you installed from a ZIP

Uninstall your current version of Academic by deleting the contents of `themes/academic/`. [Download](https://github.com/gcushen/hugo-academic/archive/master.zip) and extract the latest version of Academic to your `themes/academic/` folder.

## Migrate Content

When you update Academic itself, you can jump straight to the latest and greatest version. However, content migration requires consecutively applying any relevant steps from each release.

To migrate your TOML/YAML front matter and configuration, apply any relevant steps from the *Breaking Changes* section of each **consecutive [release note](/academic/updates/)** since the version you were originally on. If a release has no *Breaking Changes* section, then no changes are required.
 
For example, if you are updating from *v2.4.0* to *v3.1.0*, then [apply the breaking changes]({{< relref "../updates" >}}) for the relevant **consecutive** releases. In this case, that would require **first** applying the breaking changes from [v3.0.0]({{< relref "../updates/v3.0.0.md#breaking-changes" >}}) **and then** applying the breaking changes from [v3.1.0]({{< relref "../updates/v3.1.0.md#breaking-changes" >}}).

To help migrate content to be compatible with new versions of Academic, there are some tools available in the **[Academic Scripts](https://github.com/sourcethemes/academic-scripts)** repository.

## Troubleshooting

Check out the [release notes]({{< relref "../updates" >}}) for the consecutive version that you are updating to, paying attention to the breaking changes. You can check which version you currently have, refer to the *Preparation* section above.

If there are any issues after updating, you may wish to compare your site with the latest [example site](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) to check if any TOML/YAML settings changed in the configuration files (i.e. all files in the `config/_default/` folder) or in the [front matter]({{< relref "front-matter.md" >}}) of content files (i.e. files in the `content/` folder).

If you have modified files in `themes/academic`, git will attempt to auto-merge changes. If conflicts are reported, you will need to manually edit the files with conflicts and add them back (`git add <filename>`).

Also, if you overrided any Academic files (by using Hugo's inheritance principle), then these may cause conflicts after updating. Consider removing them or checking if the original file(s) that you are overriding have changed in any way and require syncing with your custom version of the file(s).
