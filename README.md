<div align="center">

  # Chirpy Jekyll Theme

  A minimal, responsive, and powerful Jekyll theme for presenting professional writing.

  [![Gem Version](https://img.shields.io/gem/v/jekyll-theme-chirpy?color=brightgreen)](https://rubygems.org/gems/jekyll-theme-chirpy)
  [![CI](https://github.com/cotes2020/jekyll-theme-chirpy/actions/workflows/ci.yml/badge.svg)](https://github.com/cotes2020/jekyll-theme-chirpy/actions/workflows/ci.yml)
  [![Codacy Badge](https://app.codacy.com/project/badge/Grade/4e556876a3c54d5e8f2d2857c4f43894)](https://www.codacy.com/gh/cotes2020/jekyll-theme-chirpy/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=cotes2020/jekyll-theme-chirpy&amp;utm_campaign=Badge_Grade)
  [![GitHub license](https://img.shields.io/github/license/cotes2020/jekyll-theme-chirpy.svg)](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/LICENSE)
  [![996.icu](https://img.shields.io/badge/link-996.icu-%23FF4D5B.svg)](https://996.icu)

  [**Live Demo →**](https://cotes2020.github.io/chirpy-demo)

  [![Devices Mockup](https://chirpy-img.netlify.app/commons/devices-mockup.png)](https://cotes2020.github.io/chirpy-demo)

</div>

## Features

- Dark/Light Theme Mode
- Localized UI language
- Pinned Posts
- Hierarchical Categories
- Trending Tags
- Table of Contents
- Last Modified Date of Posts
- Syntax Highlighting
- Mathematical Expressions
- Mermaid Diagram & Flowchart
- Dark/Light Mode Images
- Embed Videos
- Disqus/Utterances/Giscus Comments
- Search
- Atom Feeds
- Google Analytics
- Page Views Reporting
- SEO & Performance Optimization

## Quick Start

Before starting, please follow the instructions in the [Jekyll Docs](https://jekyllrb.com/docs/installation/) to complete the installation of `Ruby`, `RubyGems`, `Jekyll`, and `Bundler`. In addition, [Git](https://git-scm.com/) is also required to be installed.

### Step 1. Creating a New Site

Create a new repository from the [**Chirpy Starter**](https://github.com/cotes2020/chirpy-starter/generate) and name it `<GH_USERNAME>.github.io`, where `GH_USERNAME` represents your GitHub username.

### Step 2. Installing Dependencies

Before running for the first time, go to the root directory of your site, and install dependencies as follows:

```console
$ bundle
```

### Step 3. Running Local Server

Run the following command in the root directory of the site:

```console
$ bundle exec jekyll s
```

Or run with Docker:

```console
$ docker run -it --rm \
    --volume="$PWD:/srv/jekyll" \
    -p 4000:4000 jekyll/jekyll \
    jekyll serve
```

After a while, navigate to the site at <http://localhost:4000>.

<<<<<<< HEAD
### Deployment

Before the deployment begins, check out the file `_config.yml` and make sure the `url` is configured correctly. Furthermore, if you prefer the [**project site**](https://help.github.com/en/github/working-with-github-pages/about-github-pages#types-of-github-pages-sites) and don't use a custom domain, or you want to visit your website with a base URL on a web server other than **GitHub Pages**, remember to change the `baseurl` to your project name that starts with a slash, e.g, `/project-name`.

Now you can choose ONE of the following methods to deploy your Jekyll site.

#### Deploy by Using Github Actions

For security reasons, GitHub Pages build runs on `safe` mode, which restricts us from using plugins to generate additional page files. Therefore, we can use **GitHub Actions** to build the site, store the built site files on a new branch, and use that branch as the source of the GitHub Pages service.

Quickly check the files needed for GitHub Actions build:

- Ensure your Jekyll site has the file `.github/workflows/pages-deploy.yml`. Otherwise, create a new one and fill in the contents of the [sample file][workflow], and the value of the `on.push.branches` should be the same as your repo's default branch name.

- Ensure your Jekyll site has file `tools/deploy.sh`. Otherwise, copy it from here to your Jekyll site.

- Furthermore, if you have committed `Gemfile.lock` to the repo, and your runtime system is not Linux, don't forget to update the platform list in the lock file:

  ```console
  $ bundle lock --add-platform x86_64-linux
  ```

After the above steps, rename your repository to `<GH_USERNAME>.github.io` on GitHub.

Now publish your Jekyll site by:

1. Push any commit to remote to trigger the GitHub Actions workflow. Once the build is complete and successful, a new remote branch named `gh-pages` will appear to store the built site files.

2. Browse to your repository on GitHub. Select the tab _Settings_, then click _Pages_ in the left navigation bar, and then in the section **Source** of _GitHub Pages_, select the `/(root)` directory of branch `gh-pages` as the [publishing source][pages-src]. Remember to click <kbd>Save</kbd> before leaving.

    ![gh-pages-sources](https://cdn.jsdelivr.net/gh/cotes2020/chirpy-images@f4e0354b674f65a53b8917f0f786ed2956898cc1/posts/20190809/gh-pages-sources.png)

3. Visit your website at the address indicated by GitHub.

#### Manually Build and Deploy

On self-hosted servers, you cannot enjoy the convenience of **GitHub Actions**. Therefore, you should build the site on your local machine and then upload the site files to the server.

Go to the root of the source project, and build your site as follows:

```console
$ JEKYLL_ENV=production bundle exec jekyll b
```

Or build the site on Docker:

```console
$ docker run -it --rm \
    --env JEKYLL_ENV=production \
    --volume="$PWD:/srv/jekyll" \
    jekyll/jekyll \
    jekyll build
```

Unless you specified the output path, the generated site files will be placed in folder `_site` of the project's root directory. Now you should upload those files to the target server.

### Upgrading

It depends on how you use the theme:

- If you are using the theme gem (there will be `gem "jekyll-theme-chirpy"` in the `Gemfile`), editing the `Gemfile` and update the version number of the theme gem, for example:

    ```diff
    - gem "jekyll-theme-chirpy", "~> 3.2", ">= 3.2.1"
    + gem "jekyll-theme-chirpy", "~> 3.3", ">= 3.3.0"
    ```

    And then execute the following command:

    ```console
    $ bundle update jekyll-theme-chirpy
    ```

    As the version upgrades, the critical files (for details, see the [Startup Template][starter]) and configuration options will change. Please refer to the [Upgrade Guide](https://github.com/cotes2020/jekyll-theme-chirpy/wiki/Upgrade-Guide) to keep your repo's files in sync with the latest version of the theme.

- If you forked from the source project (there will be `gemspec` in the `Gemfile` of your site), then merge the [latest upstream tags][latest-tag] into your Jekyll site to complete the upgrade.
The merge is likely to conflict with your local modifications. Please be patient and careful to resolve these conflicts.

=======
>>>>>>> 65a38c8 (Simplify the README)
## Documentation

For more details on usage, please refer to the tutorial on the [demo website](https://cotes2020.github.io/chirpy-demo/) / [wiki](https://github.com/cotes2020/jekyll-theme-chirpy/wiki). Note that the tutorial is based on the [latest release](https://github.com/cotes2020/jekyll-theme-chirpy/releases/latest), and the features of the default branch are usually ahead of the documentation.

## Contributing

Welcome to report bugs, improve code quality or submit a new feature. For more information, see [contributing guidelines](.github/CONTRIBUTING.md).

## Credits

This theme is mainly built with [Jekyll](https://jekyllrb.com/) ecosystem, [Bootstrap](https://getbootstrap.com/), [Font Awesome](https://fontawesome.com/) and some other wonderful tools (their copyright information can be found in the relevant files). The avatar and favicon design come from [Clipart Max](https://www.clipartmax.com/middle/m2i8b1m2K9Z5m2K9_ant-clipart-childrens-ant-cute/).

:tada: Thanks to all the volunteers who contributed to this project, their GitHub IDs are on [this list](https://github.com/cotes2020/jekyll-theme-chirpy/graphs/contributors). Also, I won't forget those guys who submitted the issues or unmerged PR because they reported bugs, shared ideas, or inspired me to write more readable documentation.

Last but not least, thank [JetBrains][jb] for providing the OSS development license.

## Sponsoring

If you like this theme or find it helpful, please consider sponsoring me, because it will encourage and help me better maintain the project, I will be very grateful!

[![Ko-fi](https://img.shields.io/badge/-Buy%20Me%20a%20Coffee-ff5f5f?logo=ko-fi&logoColor=white)](https://ko-fi.com/coteschung)
[![Wechat Pay](https://img.shields.io/badge/-Tip%20Me%20on%20WeChat-brightgreen?logo=wechat&logoColor=white)][cn-donation]
[![Alipay](https://img.shields.io/badge/-Tip%20Me%20on%20Alipay-blue?logo=alipay&logoColor=white)][cn-donation]

## License

This work is published under [MIT](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/LICENSE) License.

<!-- ReadMe links -->

[jb]: https://www.jetbrains.com/?from=jekyll-theme-chirpy
[cn-donation]: https://sponsor.cotes.page/
