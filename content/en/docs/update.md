---
title: Update
date: 2016-04-20
type: book
weight: 75
---

The update process consists of:

1. [Preparation](#preparation)
2. [Updating Wowchemy](#update-wowchemy)
3. [Migrating your content](#migrate-content) front matter and configuration by applying any relevant breaking changes

Feel free to [star Wowchemy on Github](https://github.com/wowchemy/wowchemy-hugo-modules/) to help keep track of updates and check out the [release notes](/updates/) to learn what's new.

## Preparation

Before updating Wowchemy, it is strongly recommended to make a full **backup** of your website folder.

Then, **record your current version**, so that after you update Wowchemy, you can apply any relevant breaking changes to the TOML/YAML site configuration and front matter in your `content/` folder.

To find your current version, look in `themes/academic/data/academic.toml` if it exists. Otherwise, you can get the version from `go.mod` where it'll either be an exact version like `v5.0.0` or it'll be a build in the form `v<dummy-version-number>-<date>-<build-number>`. The first 7 characters of the build number can be cross-referenced in the [commit log](https://github.com/wowchemy/wowchemy-hugo-modules/commits/master) to check what development updates are available.

Note that if you installed a build in the *master* version rather than a specific release, then extra care should be taken (such as by checking the git log if you installed with git) as you may be in-between versions and some actions in the relevant release notes may have already been applied.

## Update Wowchemy

### Prerequisites

[Install]({{< relref "./install-locally/index.md" >}}) a compatible version of Hugo Extended and its dependencies.

If your site does not have a `go.mod` file, [convert your site to use the Wowchemy Hugo Module](#convert-an-old-academic-kickstarter-site).

If your site has a `go.mod` file and was created before _3rd September 2020_, having `path = "github.com/gcushen/hugo-academic"
` in `config/_default/config.toml`, update the path to `github.com/wowchemy/wowchemy-hugo-modules/wowchemy`.

### Update

Open a Terminal (Command Prompt) and navigate to your site's folder using the [`cd` command](https://linuxize.com/post/linux-cd-command/).

Update to get the very latest developments:

```
hugo mod get github.com/wowchemy/wowchemy-hugo-modules/wowchemy/@master
```

Alternatively, update to the latest official release:

```
hugo mod get -u
```

[Migrate your content](#migrate-content) front matter and configuration if necessary by applying any relevant breaking changes.

## Migrate Content

When you update Wowchemy itself, you can jump straight to the latest and greatest version. However, content migration requires consecutively applying any relevant steps from each release.

To migrate your TOML/YAML front matter and configuration, apply any relevant steps from the *Breaking Changes* section of each **consecutive [release note](/updates/)** since the version you were originally on. If a release has no *Breaking Changes* section, then no changes are required.
 
For example, if you are updating from *v2.4.0* to *v3.1.0*, then [apply the breaking changes]({{< relref "../updates" >}}) for the relevant **consecutive** releases. In this case, that would require **first** applying the breaking changes from [v3.0.0]({{< relref "../updates/v3.0.0.md#breaking-changes" >}}) **and then** applying the breaking changes from [v3.1.0]({{< relref "../updates/v3.1.0.md#breaking-changes" >}}).

To help migrate content to be compatible with new versions of Hugo and Wowchemy, there are some scripts available in the **[Hugo Scripts](https://github.com/wowchemy/hugo-scripts)** repository which you might find useful.

## Troubleshooting

Check out the [release notes]({{< relref "../updates" >}}) for the consecutive version that you are updating to, paying attention to the breaking changes. You can check which version you currently have, refer to the *Preparation* section above.

If there are any issues after updating, you may wish to compare your site with one of the latest templates, such as the  [Academic Template](https://github.com/wowchemy/starter-academic/) to check if the file structure changed, any TOML/YAML settings changed in the configuration files (i.e. all files in the `config/_default/` folder), or any options changed in the [front matter]({{< relref "front-matter.md" >}}) of content files (i.e. files in the `content/` folder).

If you overrided any Wowchemy files (by using Hugo's inheritance principle), then these may cause conflicts after updating. Consider removing them or checking if the original file(s) that you are overriding have changed in any way and require syncing with your custom version of the file(s).
