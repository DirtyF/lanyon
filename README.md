# Lanyon

Lanyon is an unassuming [Jekyll](http://jekyllrb.com) theme that places content first by tucking away navigation in a hidden drawer. It's based on [Poole](http://getpoole.com), the Jekyll butler.

![Lanyon](https://f.cloud.github.com/assets/98681/1825266/be03f014-71b0-11e3-9539-876e61530e24.png)
![Lanyon with open sidebar](https://f.cloud.github.com/assets/98681/1825267/be04a914-71b0-11e3-966f-8afe9894c729.png)


## Contents

- [Install](#install)
  - [As a fork](#as-a-fork)
  - [As a gem-based theme](#as-a-gem-based-theme)
  - [As a remote theme on GitHub Pages](#as-a-remote-theme-on-github-pages)
- [Usage](#usage)
- [Options](#options)
  - [Sidebar menu](#sidebar-menu)
  - [Themes](#themes)
  - [Reverse layout](#reverse-layout)
- [Development](#development)
- [Author](#author)
- [License](#license)


## Install

You can install Jekyll themes in three ways.

### As a Fork

Lanyon is a theme built on top of [Poole](https://github.com/poole/poole), which provides a fully furnished Jekyll setup—just download and start the Jekyll server. See [the Poole usage guidelines](https://github.com/poole/poole#usage) for how to install and use Jekyll.

### As a gem-based theme

Jekyll encourages the use of `bundler` to manage themes and plugins. [Themes](https://jekyllrb.com/docs/themes/) can be packaged as Ruby gems since Jekyll v3.3.0. If you don't intend to modify the theme a lot, this is a nice way of focusing on your content and benefit from theme updates.

1. List the theme as a dependency in your `Gemfile`:

```ruby
# frozen_string_literal: true

source "https://rubygems.org"

gem "jekyll", "~> 3.7.0"
gem "jekyll-theme-lanyon", "~> 1.1"
```

2. Copy default [`_config.yml`](docs/_config.yml), comment out `theme: jekyll-theme-lanyon` and comment or remove `remote_theme:  dirtyf/lanyon`.
3. Copy also [`index.html`](docs/index.html), [`404.html`](docs/404.html) and [`about.md`](docs/about.md) from this repository's [example files](docs) to your source directory.
3. Run `bundle update` to update all dependencies.

### As a remote theme on GitHub Pages

1. Go with the default GitHub Pages `Gemfile`:

```ruby
# frozen_string_literal: true

source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
```

2. Copy [`_config.yml`](docs/_config.yml), [`index.html`](docs/index.html), [`404.html`](docs/404.html) (and [`about.md`](docs/about.md)) from this repository's [example files](docs) to your source directory.

```ruby
remote_theme: dirtyf/lanyon
```

## Gem-based theme directory structure

If you use the theme gem and list the files in your source directory, don't be surprised if you only see:

```
├── _posts        # your posts are here
├── _site         # default destination build directory
├── _config.yml   # jekyll configuration
├── 404.html      # default 404 page template
├── about.md      # default example page
├── Gemfile       # bundler configuration
├── Gemfile.lock  # bundler version lock
└── index.html    # list all the posts on the homepage
```

:bulb: When you use gem-based themes, the themes files don't appear in your source directory, they're packaged within the gem.

If you wonder where the original theme files are, `bundler` allows you to show a gem content:

```sh
tree $(bundle show jekyll-theme-lanyon)
├── Gemfile
├── Gemfile.lock
├── LICENSE.md
├── README.md
├── _includes
│   ├── head.html
│   └── sidebar.html
├── _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── assets
│   ├── apple-touch-icon-precomposed.png
│   ├── css
│   │   ├── lanyon.css
│   │   ├── poole.css
│   │   └── syntax.css
│   └── favicon.ico
```

If you want to customize the theme, you'll have to copy the files you need to modify in your source directory.
Report to jekyll's documentation to learn [how to override a theme](https://jekyllrb.com/docs/themes/#overriding-theme-defaults).

## Usage

Run `bundle exec jekyll serve` to preview your website locally.

## Options

Lanyon includes some customizable options, typically applied via classes on the `<body>` element.


### Sidebar menu

Create a list of nav links in the sidebar by assigning each Jekyll page the correct layout in the page's [front-matter](http://jekyllrb.com/docs/frontmatter/).

```
---
layout: page
title: About
---
```

**Why require a specific layout?** Jekyll will return *all* pages, including the `atom.xml`, and with an alphabetical sort order. To ensure the first link is *Home*, we exclude the `index.html` page from this list by specifying the `page` layout.


### Themes

Lanyon ships with eight optional themes based on the [base16 color scheme](https://github.com/chriskempson/base16). Apply a theme to change the color scheme (mostly applies to sidebar and links).

![Lanyon with red theme](https://f.cloud.github.com/assets/98681/1825270/be065110-71b0-11e3-9ed8-9b8de753a4af.png)
![Lanyon with red theme and open sidebar](https://f.cloud.github.com/assets/98681/1825269/be05ec20-71b0-11e3-91ea-a9138ef07186.png)

There are eight themes available at this time.

![Available theme classes](https://f.cloud.github.com/assets/98681/1817044/e5b0ec06-6f68-11e3-83d7-acd1942797a1.png)

To use a theme, add any one of the available theme classes to the `<body>` element in the `default.html` layout, like so:

```html
<body class="theme-base-08">
  ...
</body>
```

To create your own theme, look to the Themes section of [included CSS file](https://github.com/poole/lanyon/blob/master/public/css/lanyon.css). Copy any existing theme (they're only a few lines of CSS), rename it, and change the provided colors.


### Reverse layout

![Lanyon with reverse layout](https://f.cloud.github.com/assets/98681/1825265/be03f2e4-71b0-11e3-89f1-360705524495.png)
![Lanyon with reverse layout and open sidebar](https://f.cloud.github.com/assets/98681/1825268/be056174-71b0-11e3-88c8-5055bca4307f.png)

Reverse the page orientation with a single class.

```html
<body class="layout-reverse">
  ...
</body>
```


### Sidebar overlay instead of push

Make the sidebar overlap the viewport content with a single class:

```html
<body class="sidebar-overlay">
  ...
</body>
```

This will keep the content stationary and slide in the sidebar over the side content. It also adds a `box-shadow` based outline to the toggle for contrast against backgrounds, as well as a `box-shadow` on the sidebar for depth.

It's also available for a reversed layout when you add both classes:

```html
<body class="layout-reverse sidebar-overlay">
  ...
</body>
```

### Sidebar open on page load

Show an open sidebar on page load by modifying the `<input>` tag within the `sidebar.html` layout to add the `checked` boolean attribute:

```html
<input type="checkbox" class="sidebar-checkbox" id="sidebar-checkbox" checked>
```

Using Liquid you can also conditionally show the sidebar open on a per-page basis. For example, here's how you could have it open on the homepage only:

```html
<input type="checkbox" class="sidebar-checkbox" id="sidebar-checkbox" {% if page.title =="Home" %}checked{% endif %}>
```

## Development

Lanyon has two branches, but only one is used for active development.

- `master` for development.  **All pull requests should be to submitted against `master`.**
- `gh-pages` for our hosted site, which includes our analytics tracking code. **Please avoid using this branch.**


## Author

**Mark Otto**
- <https://github.com/mdo>
- <https://twitter.com/mdo>


## License

Open sourced under the [MIT license](LICENSE.md).

<3
