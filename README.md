# Jekyll project for GaitQ

This repo only deals with the website navigation and structure. We have three distinctive environments, general GaitQ pages, content that is specific to a customer of GaitQ and content for professionals and the technically curious.

## Scaffolding

How this repo is organised and what the various files are. All posts, layouts, includes, stylesheets, assets, and whatever else is grouped nicely under the root folder. The compiled Jekyll site outputs to `_site/`, which is never pushed to this repo, see https://www.gaitq.madeslowly.xyz/navbar.

```
GaitQ/
|
├─ _config.yml/                   # Jekyll build settings, site. ...
|
├─ _data/                         # Site wide data, site.data. ...
|  |
|  ├─ menu.yml                    # Menu structure for GaitQ.com
|
├─ _includes/                     # HTML and Liquid templating
|  |
|  ├─ head/                       # All header content
|  |  |
|  |  ├─ descriptor/              # Site wide descriptions
|  |  |  |
|  |  |  ├─ og-meta.html
|  |  |  ├─ structured-data.html
|  |  |  ├─ twitter-meta.html
|  |  |    
|  |  ├─ styles/                  # Global and local styles
|  |  |  |
|  |  |  ├─ global.html           # Site wide stylesheets
|  |  |  ├─ gaitq.html            # URL specific
|  |  |  ├─ patients.html         # URL specific
|  |  |  ├─ clinicians.html       # URL specific
|  |  |
|  |  ├─ head.html                # <head> routine with URL conditions
|  |
|  ├─ navigation/                 # HTML and Liquid templating
|  |  |
|  |  ├─ global.html              # <nav> routine with URL conditions
|  |
|  ├─ scripts.html                # JS scripts & closing body & html
|
├─ _layouts/                      # HTML and Liquid templating
|  |
|  ├─ enviroments/                # URL specific
|  |  |
|  |  ├─ clinicians.html          # Professionals and press
|  |  ├─ patients.html            # Patients and carers
|  |  ├─ gaitq.html               # Default for GaitQ submenu
|  |
|  ├─ landing.html                # Landing page
|  |
|  ├─ default.html                # Final pass for all pages, also this is where Jekyll looks if no Front Matter def
|
├─ _posts/                        # Blog entries, undeveloped
|
├─ _sass/                         # Sass partials
|  |
|  ├─ navigation/                 # All header content
|  |  |
|  |  ├─ _variable.sass           # <nav> settings
|  |  ├─ burger.sass              # Mobile burger
|  |  ├─ mobile.sass              # Default nav CSS
|  |  ├─ desktop.sass             # Breakpoint 768 CSS
|  |  ├─ clinicians.sass          # Clinicians nav CSS & Breakpoint 768
|  |  ├─ patients.sass            # Patients nav CSS & Breakpoint 768
|  |  ├─ gaitq.sass               # GaitQ nav CSS & Breakpoint 768
|  |
|  ├─ typography/                 # All header content
|  |  |
|  |  ├─ _variable.sass           # Typography settings
|  |  ├─ resets.sass              # User agent resets
|  |
|  ├─ landing.sass                # Landing page
|
├─ assets/                        # HTML and Liquid templating
|  |
|  ├─ css/                        # Sass imports
|  |  |
|  |  ├─ gaitq_global.sass        # Global CSS, included on ALL pages
|  |  ├─ gaitq_gaitq.sass         # GaitQ env CSS
|  |  ├─ gaitq_patients.sass      # Patient env CSS
|  |  ├─ gaitq_clinician.sass     # Clinician env CSS
|  |  ├─ gaitq_landing.sass       # Landing page CSS
|  |
|  ├─ img/                        # All our imagery
|  |
|  ├─ JS/                         # All our JavaScript
|  |
|  ├─ vendor/                     # Third party CSS and JS code, never edit! If we need to overwrite something we add our own CSS or JS to do so.
```
---

### Site Wide Configuration

`_config.yml` is where most variables are set.

#### title:

The global title of the website.

#### subtitle:

The global subtitle of the website.

Pages are given titles according to

```Liquid
{% if page.title %}
  {{ page.title }} | {{ site.title }}
{% else %}
  {{ site.title }} | {{ site.subtitle }}
{% endif %}
```


#### logo

Site wide logo, used as a default image for Twitter Cards and og_image when not defined in page front matter.

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

To set what links appear in the top navigation edit `_data/menu.yml`. Use the following format to set the URL and title for as many links as you'd like.

```yaml
group_name:
  - name:  Page name
    url:   /pageURL.html
    env:   environment
    submenu:
      - name: Page name
        url:  /pageURL.html
```

We for loop  `group_name` = `navigation`. The `env:` controls where and how we see the navigation link and it's submenu contents. Currently we have three allowable `envs:`, `gaitq`, `clinicians` and `patients`.

---
