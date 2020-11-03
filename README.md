# DPSG Hugo Theme

**DPSG** is a responsive, simple, clean and content-focused
[Hugo](https://gohugo.io/) theme that imitates the [official Wordpess
theme](https://dpsg.de/de/fuer-mitglieder/oeffentlichkeitsarbeit/vorlagen/vorlagen-online/wordpress.html)
featured by the DPSG German scout association. It's forked from the
[Mainroad](https://github.com/Vimux/Mainroad) Hugo theme.

The reference implementation is visible on the [website of DPSG Stamm Bruder
Klaus Konstanz](https://pfadfinder-konstanz.de).

![screenshot](https://github.com/pfadfinder-konstanz/hugo-dpsg/blob/master/images/screenshot.png)

**Features:**

* Hugo internal templates (Open Graph, Schema, Twitter Cards)
* No inclusion of third-party libraries, but all hosted locally (fonts, JS etc.)
* Responsive menu
* Secondary menus
* SVG icons
* Theme options (Sidebar position, Author Box, Post Navigation, highlight color)
  available through config.toml file parameters
* Table of Contents

**Browser support:**

* **Desktop:** IE11+, Chrome, Firefox, Safari
* **Mobile:** Android browser (on Android 4.4+), Safari (on iOS 7+), Google Chrome, Opera mini

Other browsers (like Opera on Blink engine) are also supported, but not tested.

## Installation

*Before starting, please be sure that you have
[installed Hugo](https://gohugo.io/getting-started/quick-start/#step-1-install-hugo) and
[created a new site](https://gohugo.io/getting-started/quick-start/#step-2-create-a-new-site).
After that, you ready to install **DPSG**.*

In your Hugo site `themes` directory, run:

```
git clone https://github.com/pfadfinder-konstanz/hugo-dpsg
```

Or, if you don't plan to make any significant changes, but want to track and
update the theme, you can add it as a git submodule via the following command:

```
git submodule add https://github.com/pfadfinder-konstanz/hugo-dpsg
```

Next, open `config.toml` in the base of the Hugo site and ensure the theme
option is set to `hugo-dpsg`:

```
theme = "hugo-dpsg"
```

For more information read the official [setup guide](https://gohugo.io/themes/installing-and-using-themes/) of Hugo.

## Configuration

### Config.toml example

```toml
baseurl = "/"
title = "Hugo DPSG"
languageCode = "de"
DefaultContentLanguage = "de"
paginate = "10" # Number of posts per page
theme = "hugo-dpsg"

[Author] # Used in authorbox
  name = "Scout Master"
  bio = "The Scout Master is the leader of this local scout group"
  avatar = "img/avatar.png"

[Params]
  description = "Welcome to our scout group!" # Site description. Used in meta description
  copyright = "DGSP local group" # Footer copyright holder, otherwise will use site title
  opengraph = true # Enable OpenGraph if true
  schema = true # Enable Schema
  twitter_cards = true # Enable Twitter Cards if true
  readmore = false # Show "Read more" button in list if true
  authorbox = true # Show authorbox at bottom of pages if true
  toc = true # Enable Table of Contents
  pager = true # Show pager navigation (prev/next links) at the bottom of pages if true
  indexPager = false # Show pager navigation on index page
  post_meta = ["author", "date", "categories", "translations"] # Order of post meta information
  mainSections = ["post", "blog", "news"] # Specify section pages to show on home page and the "Recent articles" widget
  photosSections = ["photos"] # Specify section pages to show on home page and the "Recent photos" widget
  dateformat = "02.01.2006" # Change the format of dates
  customCSS = ["css/custom.css"] # Include custom CSS files
  customJS = ["js/custom.js"] # Include custom JS files

[Params.style.vars]
  highlightColor = "#003056" # Override main theme color

[Params.logo]
  image = "img/placeholder.png" # Logo image. Path relative to "static"
  header = "img/header.jpg" # Header image. Path relative to "static"
  title = "DPSG local group" # Logo title, otherwise will use site title
  subtitle = "Welcome to our group site" # Logo subtitle

[Params.sidebar]
  home = "right" # Configure layout for home page
  list = "left"  # Configure layout for list pages
  single = false # Configure layout for single pages
  # Enable widgets in given order
  widgets = ["search", "recent", "recent_photos", "categories", "taglist", "social", "languages"]
  # alternatively "ddg-search" can be used, to search via DuckDuckGo
  # widgets = ["ddg-search", "recent", "categories", "taglist", "social", "languages"]

[Params.footer]
  text = "[Imprint and Privacy](/imprint)" # Extra text in footer row, understands markdown

[Params.widgets]
  recent_num = 5 # Set the number of articles in the "Recent articles" widget
  tags_counter = false # Enable counter for each tag in "Tags" widget

[Params.widgets.social]
  # Enable parts of social widget
  facebook = "username"
  twitter = "username"
  instagram = "username"
  linkedin = "username"
  telegram = "username"
  github = "username"
  gitlab = "username"
  bitbucket = "username"
  email = "example@example.com"

# Custom social links
[[Params.widgets.social.custom]]
  title = "Youtube"
  url = "https://youtube.com/user/username"
  icon = "youtube.svg" # Optional. Path relative to "layouts/partials"

[[Params.widgets.social.custom]]
  title = "My Home Page"
  url = "http://example.com"
```

A good idea is not to copy all these settings without understanding how it
works. Use only those parameters that you need.

For more information about all available standard configuration settings, please
read [All Hugo Configuration
Settings](https://gohugo.io/getting-started/configuration/#all-configuration-settings).

### Front Matter example

```yaml
---
# Common-Defined params
title: "Example article title"
date: "2017-08-21"
description: "Example article description"
categories:
  - "Category 1"
  - "Category 2"
tags:
  - "Test"
  - "Another test"
menu: main # Optional, add page to a menu. Options: main, side, footer

# Theme-Defined params
thumbnail: "img/placeholder.jpg" # Thumbnail image
thumbnail_hide_post: false # Hide thumbnail on single post view
lead: "Example lead - highlighted near the title" # Lead text
authorbox: true # Enable authorbox for specific page
pager: true # Enable pager navigation (prev/next) for specific page
toc: true # Enable Table of Contents for specific page
sidebar: "right" # Enable sidebar (on the right side) per page
widgets: # Enable sidebar widgets in given order per page
  - "search"
  - "recent"
  - "taglist"
sitemap_hide: false # Do not add this page to the sitemap
---
```

For more information about front matter variables read [Hugo Front
Matter](https://gohugo.io/content-management/front-matter) from Hugo official
documentation.

### Sidebar

**Hugo DPSG** comes with a configurable sidebar that can be on the left, on the right, or
disabled. The default layout can be specified in the `[Params.sidebar]` section
of the configuration. The position can be specified for home, list and single
pages individually. Use the keys `home`, `list` and `single` with values
`"left"`, `"right"` or `false`. The layout can be configured per page, by
setting the `sidebar` parameter with one of the same values in the page's front
matter.

The sidebar consists of multiple widgets. Widgets can be enabled individually
using the `widgets` key with a list of widget names as value. You can add your
own widgets, by placing a template under `layouts/partials/widgets/<name>.html`.
The list of widgets can be overwritten from a page's front matter.

Some widget respect optional configuration. Have a look at the
`[Params.widgets]` and `[Params.widgets.social]` sections in the example
configuration above.

### Menus

**Hugo DPSG** supports multiple menus. The `main` menu is fully responsive and displayed right
under the site header. The secondary menus `side` and `footer` are displayed in
a sidebar widget and the page footer. To add a page to a menu, add a `menu:
<menu>` parameter to the page's front matter:

```yaml
menu: main # Add page to a main menu
```

You can also add a page to multiple menus by providing a list:

```yaml
menu: ["main", "side", "footer"] # Add page to a main, side, and footer menu
```

**Note:** Don't forget to enable the `sidemenu` widget in the `widgets`
configuration param if you want to use the `side` menu.

**Note:** Please keep in mind that the menus don't support nested items
i.e. submenus.

### Social Widget: custom links

**Hugo DPSG** contains built-in social links in the social widget. In addition,
you can also set custom social links by adding `Params.widgets.social.custom` to
your `config.toml`. Here is an example.

```toml
[[Params.widgets.social.custom]]
  title = "Youtube"
  url = "https://youtube.com/user/username"
  icon = "youtube.svg"
```

**Note:** You need to put your icon file in `layouts/partials` directory under your
project's root if you want to display an icon of your social link. The `icon`
filed, which is optional, should be a path relative to `layouts/partials`.

**Note:** *Only* SVG files are supported to be used as custom social icons in the current
version. If you use any files of another format, PNG for example, a compile
error will be raised by Hugo.

**Note:** Not every SVG icon can be used. For better results, it should be one-color SVG
file with a special class attribute `{{ with .class }}{{ . }} {{ end }}` and
24x24 size. At a minimum, custom SVG icon needs these attributes:

```html
<svg class="{{ with .class }}{{ . }} {{ end }} icon" width="24" height="24">...</svg>
```

## Contributing

Have you found a bug or got an idea for a new feature? Feel free to use the
[issue tracker](https://github.com/pfadfinder-konstanz/hugo-dpsg/issues) to let
me know. Or make directly a [pull
request](https://github.com/pfadfinder-konstanz/hugo-dpsg/pulls).

## License

This theme is released under the [GPLv2 license](https://github.com/pfadfinder-konstanz/hugo-dpsg/blob/master/LICENSE.md) (GPL-2.0-only).
