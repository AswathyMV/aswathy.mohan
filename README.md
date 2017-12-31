# Jalpc. [![Analytics](https://ga-beacon.appspot.com/UA-73784599-1/welcome-page)](https://github.com/jarrekk/Jalpc)

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)](https://opensource.org/licenses/mit-license.php)
[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)
[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/ellerbrock/open-source-badge/)

<https://DeepLearnerCNN.github.io/aswathy.mohan/>

<http://www.jarrekk.com>  -- Personal website

![Blog](https://github.com/DeepLearnerCNN/aswathy.mohan/static/assets/img/landing/NN_Transfer_out.jpg)
I just spent one day building this blog with Jekyll and github page and it's now up. Many thanks to Jalpc Jekyll Blog which I git cloned and tweaked to avoid building from scratch.

- [3 steps to setup this theme at your website!](#3-steps-to-setup-this-theme-at-your-website)
- [Features](#features)
  - [Index page](#index-page)
    - [`_data/*.yml`](#_datayml)
  - [Chart Skills](#chart-skills)
  - [Categories in blog page](#categories-in-blog-page)
  - [Pagination](#pagination)
  - [Page views counter](#page-views-counter)
  - [Multilingual Page](#multilingual-page)
  - [Web analytics](#web-analytics)
  - [Comment](#comment)
  - [Share](#share)
  - [Search engines](#search-engines)
  - [Compress CSS and JS files](#compress-css-and-js-files)
- [Put in a Jalpc Plug](#put-in-a-jalpc-plug)
- [Upgrading Jalpc](#upgrading-jalpc)
  - [Ensure there's an upstream remote](#ensure-theres-an-upstream-remote)
  - [Pull in the latest changes](#pull-in-the-latest-changes)
- [Todo](#todo)
- [Donate Jalpc](#donate-jalpc)
- [Wiki](#wiki)
- [Ad](#ad)

This is a simple, beautiful and swift theme for Jekyll. It's mobile first, fluidly responsive, and delightfully lightweight.

If you're completely new to Jekyll, I recommend checking out the documentation at <http://jekyllrb.com> or there's a tutorial by Smashing Magazine.

# 3 steps to setup this theme at your website!



The following is mapping between *yml files* to *sections*.

* landing.yml ==> index.html
* index/language.yml ==> index.html
* index/careers.yml  ==>  _includes/sections/career.html
* index/skills.yml  ==>  _includes/sections/skills.html
* index/projects.yml  ==>  _includes/sections/projects.html
* index/links.yml  ==>  _includes/sections/links.html

This *yml file* is about blog page navbar

* blog.yml ==> _includes/header.html

## Chart Skills

I use [Chart.js](http://www.chartjs.org/) to show skills, the type of skills' chart is radar, if you want to custom, please read document of Chart.js and edit **_includes/sections/skills.html** and **_data/index/skills.yml**.

## Categories in blog page

In blog page, we categorize posts into several categories by url, all category pages use same template html file - `_includes/category.html`.

For example: URL is `http://127.0.0.1:4000/python/`. In `_data/blog.yml`, we define this category named `Python`, so in `_includes/category.html` we get this URL(/python/) and change it to my category(Python), then this page are posts about **Python**. The following code is about how to get url and display corresponding posts in  `_includes/category.html`.

```html
<div class="row">
    <div class="col-lg-12 text-center">
        <div class="navy-line"></div>
        {% assign category = page.url | remove:'/' | capitalize %}
        {% if category == 'Html' %}
        {% assign category = category | upcase %}
        {% endif %}
        <h1>{{ category }}</h1>
    </div>
</div>
<div class="wrapper wrapper-content  animated fadeInRight blog">
    <div class="row">
        <ul id="pag-itemContainer" style="list-style:none;">
            {% assign counter = 0 %}
            {% for post in site.categories[category] %}
            {% assign counter = counter | plus: 1 %}
            <li>
```

## Pagination

The pagination in jekyll is not very perfect,so I use front-end web method,there is a [blog](http://www.jarrekk.com/html/2016/06/04/jekyll-pagination-with-jpages.html) about the method and you can refer to [jPages](http://luis-almeida.github.io/jPages).

## Page views counter

Many third party page counter platforms are too slow,so I count my website page view myself,the javascript file is [static/js/count.min.js](https://github.com/jarrekk/jalpc_jekyll_theme/blob/gh-pages/static/js/count.min.js) ([static/js/count.js](https://github.com/jarrekk/jalpc_jekyll_theme/blob/gh-pages/static/js/count.js)),the backend API is written with flask on [Vultr VPS](https://www.vultr.com/), detail code please see [ztool-backhend-mongo](https://github.com/Z-Tool/ztool-backhend-mongo).



## Web analytics

I use [Google analytics](https://www.google.com/analytics/) and [GrowingIO](https://www.growingio.com/) to do web analytics, you can choose either to realize it,just register a account and replace id in `_config.yml`.



## Compress CSS and JS files

All CSS and JS files are compressed at `/static/assets`.

I use [UglifyJS2](https://github.com/mishoo/UglifyJS2), [clean-css](https://github.com/jakubpawlowicz/clean-css) to compress CSS and JS files, customised CSS files are at `_sass` folder which is feature of [Jekyll](https://jekyllrb.com/docs/assets/). If you want to custom CSS and JS files, you need to do the following:

1. Install [NPM](https://github.com/npm/npm) then install **UglifyJS2** and **clean-css**: `npm install -g uglifyjs; npm install -g clean-css`, then run `npm install` at root dir of project.
2. Compress script is **build.js**
3. If you want to add or remove CSS/JS files, just edit **build/build.js** and **build/files.conf.js**, then run `npm run build` at root dir of project, link/src files will use new files.

OR

Edit CSS files at `_sass` folder.



# Upgrading Jalpc

Jalpc is always being improved by its users, so sometimes one may need to upgrade.

## Ensure there's an upstream remote

If `git remote -v` doesn't have an upstream listed, you can do the following to add it:

```
git remote add upstream https://github.com/jarrekk/Jalpc.git
```

## Pull in the latest changes

```
git pull upstream gh-pages
```

There may be merge conflicts, so be sure to fix the files that git lists if they occur. That's it!

# Todo
- [ ] `jekyll server --watch` mode need to use original CSS/JS files
- [ ] User can customise index page's section title.
- [x] Non-github projects also have links.
- [ ] Add some custom color themes for selection(Nav bar, background, words, dominant hue).

# Wiki

* [Multilingual Page](https://github.com/jarrekk/Jalpc/wiki/Multilingual-Page)
* [How to add posts](https://github.com/jarrekk/Jalpc/wiki/How-to-add-posts)
* [Change Log](https://github.com/jarrekk/Jalpc/wiki/Change-Log)
* [Contributors](https://github.com/jarrekk/Jalpc/wiki/Contributors)
* [Thanks to the following](https://github.com/jarrekk/Jalpc/wiki/Thanks-to-the-following)


