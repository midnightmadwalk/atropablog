<div align="center">

  # Chirpy Jekyll Theme

  A minimal, responsive and feature-rich Jekyll theme for technical writing.

  [![Gem Version](https://img.shields.io/gem/v/jekyll-theme-chirpy?color=brightgreen)][gem]&nbsp;
  [![CI](https://github.com/cotes2020/jekyll-theme-chirpy/actions/workflows/ci.yml/badge.svg?branch=master&event=push)][ci]&nbsp;
  [![Codacy Badge](https://app.codacy.com/project/badge/Grade/4e556876a3c54d5e8f2d2857c4f43894)][codacy]&nbsp;
  [![GitHub license](https://img.shields.io/github/license/cotes2020/jekyll-theme-chirpy.svg)][license]&nbsp;
  [![996.icu](https://img.shields.io/badge/link-996.icu-%23FF4D5B.svg)](https://996.icu)

  [**Live Demo →**][demo]

  [![Devices Mockup](https://chirpy-img.netlify.app/commons/devices-mockup.png)][demo]

</div>

## Features

<details>
  <summary>
    <i>Click to view features</i>
  </summary>
  <p>

  - Dark / Light Theme Mode
  - Localized UI language
  - Pinned Posts on Home Page
  - Hierarchical Categories
  - Trending Tags
  - Table of Contents
  - Last Modified Date
  - Syntax Highlighting
  - Mathematical Expressions
  - Mermaid Diagrams & Flowcharts
  - Dark / Light Mode Images
  - Embed Videos
  - Disqus / Utterances / Giscus Comments
  - Built-in Search
  - Atom Feeds
  - Google Analytics
  - SEO & Performance Optimization

  </p>
</details>

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

To explore usage, development, and upgrade guide of the project, please refer to the [**Wiki**][wiki].

## Contributing

Reporting bugs and helping to improve source code or documentation is always welcome.
For more information, see the "[Contributing Guidelines][contribute-guide]".

## Credits

This theme is mainly built with [Jekyll][jekyllrb] ecosystem,
[Bootstrap][bootstrap], [Font Awesome][icons] and some other [wonderful tools][lib].
The avatar and favicon design come from [Clipart Max][image].

Many thanks to the [contributors][contributors] who participated in the development
and to the folks who reported bugs or shared ideas.

Last but not least, thanks to [JetBrains][jetbrains] for providing the _Open Source License_.

## Sponsoring

If you'd like to sponsor this project, the following options are available.

[![Ko-fi](https://img.shields.io/badge/Support_Me_on_Ko--fi-ff5e5b?logo=ko-fi&logoColor=white)][ko-fi]&nbsp;
[![Wechat Pay](https://img.shields.io/badge/Tip_Me_on_WeChat-brightgreen?logo=wechat&logoColor=white)][donation]&nbsp;
[![Alipay](https://img.shields.io/badge/Tip_Me_on_Alipay-blue?logo=alipay&logoColor=white)][donation]

## License

This work is published under [MIT License][license].

[gem]: https://rubygems.org/gems/jekyll-theme-chirpy
[ci]: https://github.com/cotes2020/jekyll-theme-chirpy/actions/workflows/ci.yml?query=event%3Apush+branch%3Amaster
[codacy]: https://app.codacy.com/gh/cotes2020/jekyll-theme-chirpy/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_grade
[license]: https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/LICENSE
[jekyllrb]: https://jekyllrb.com/
[bootstrap]: https://getbootstrap.com/
[icons]: https://fontawesome.com/
[image]: https://www.clipartmax.com/middle/m2i8b1m2K9Z5m2K9_ant-clipart-childrens-ant-cute/
[demo]: https://cotes2020.github.io/chirpy-demo/
[wiki]: https://github.com/cotes2020/jekyll-theme-chirpy/wiki
[contribute-guide]: https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/.github/CONTRIBUTING.md
[contributors]: https://github.com/cotes2020/jekyll-theme-chirpy/graphs/contributors
[lib]: https://github.com/cotes2020/chirpy-static-assets
[jetbrains]: https://www.jetbrains.com/?from=jekyll-theme-chirpy
[ko-fi]: https://ko-fi.com/coteschung/
[donation]: https://sponsor.cotes.page/
