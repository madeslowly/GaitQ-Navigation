# Jekyll Project for GaitQ

This repo only deals with the website navigation and structure

## Scaffolding

How this repo is organised and what the various files are. All posts, layouts, includes, stylesheets, assets, and whatever else is grouped nicely under the root folder. The compiled Jekyll site outputs to `_site/`, which is never pushed to this repo, see https://www.gaitq.madeslowly.xyz/navbar.

```
/
├── _includes/
|    ├── head/                              # All header content
|        ├── descriptor/                    # Site wide descriptions
|        |   ├── og-meta.html
|        |   ├── structured-data.html
|        |   ├── twitter-meta.html
|        |    
|        ├── styles/                        # Global and local styles
|        |   ├── global.html
|        |   ├── gaitq.html
|        |   ├── patients.html
|        |   ├── clinicians.html
|        |    
|        ├── head.html                       # <head> routine
|
|    ├── navigation/                         # Topbar navigation, we may need to add more routines here
|        ├── global.html                     # <nav> routine
|
|    ├── scripts.html                        # All JS scripts followed by body & html closing
|
├── _layouts/

```

---

### Site Wide Configuration

`_config.yml` is where most variables are set.

#### title

The global title of the site. This is overwritten by page markup `title:`

#### logo

Site wide logo, used as a default image for Twitter Cards and og_image when not defined in Front Matter.

#### url

Used to generate absolute URLs for sitemaps, feeds and for generating canonical URLs in a page's `<head>`. When developing locally either comment this out or use something like `http://localhost:4000` so all assets load properly. *Don't include a trailing `/`*.

Examples:

```yaml
url: https://gaitq.github.io
url: http://localhost:4000
url: http://www.gaitq.com
url:
```

#### Google Analytics and Webmaster Tools

Google Analytics UA and Webmaster Tool verification tags can be entered under `owner` in `_config.yml`. For more information on obtaining these meta tags check [Google Webmaster Tools](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35179) and [Bing Webmaster Tools](https://ssl.bing.com/webmaster/configure/verify/ownership) support.

### Navigation Links

To set what links appear in the top navigation edit `_data/menu.yml`. Use the following format to set the URL and title for as many links as you'd like. *External links will open in a new window.*

```yaml
group name:
  - name:  Page name
    url:   /pageURL.html
    env:   Owning page environment
    submenu:
      - name: Page name
        url:  /pageURL.html
```

We for loop  group name = navigation. The `env:` controls where and how we see the navigation link and it's submenu contents. Currently we have three allowable `envs:`, `gaitq`, `clinicians` and `patients`.
---


## Layouts and Content

Explanations of the various `_layouts` included with the theme and when to use them.
---

### Post and Page

---

## Twitter Cards

Feature and thumbnail images are used by [Open Graph](https://developers.facebook.com/docs/opengraph/) and [Twitter Cards](https://dev.twitter.com/docs/cards) as well. If you don't assign a thumbnail the site logo is used.

Here's an example of a tweet with Twitter Cards enabled.

![Twitter Card summary large image screenshot]({{ site.url }}/images/twitter-card-summary-large-image.jpg)

---
