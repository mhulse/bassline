# Rex (O'Herlihan)

[![ScreenShot](rex.gif)](http://youtu.be/LBkYqku11V0?t=1m58s)

<a href="http://gruntjs.com/" title="Built with Grunt"><img src="https://cdn.gruntjs.com/builtwith.png" alt="Built with Grunt" align="right"></a>

**Oh yeah, root's kicking in!**

## Table of contents

- [About](#about)
	- [What is a baseline?](#what-is-a-baseline)
	- [What is a "global" baseline grid?](#what-is-a-global-baseline-grid)
	- [What is a "local" baseline grid?](#what-is-a-local-baseline-grid)
	- [Why use a "local" baseline?](#why-use-a-local-baseline)
	- [Why "Rex"?](#why-rex)
- [Demonstration](#demonstration)
- [Installation](#installation)
	- [Build process](#build-process)
- [SCSS API](#scss-api)
	- [Variables](#variables)
	- [Functions](#functions)
	- [Mixins](#mixins)
- [CSS](#css)
	- [Features](#features)
- [Caveats, limitations and/or assumptions](#caveats-limitations-andor-assumptions)
- [Q & A](#qa)
- [Contributing](#contributing)
	- [Bumping the version](#bumping-the-version)
- [Feedback](#feedback)
- [Changelog](#changelog)
- [Release history](#release-history)
- [LEGAL](#legal)

## About&nbsp;[&#8613;](#table-of-contents)

Essentially, this code serves as a slightly opinionated yet very simple "local baseline grid" toolkit for use in other css projects.

### What is a baseline?

[Wikipedia](http://en.wikipedia.org/wiki/Baseline_%28typography%29) says:

> … the baseline is the line upon which most letters "sit" and below which descenders extend.

### What is a "global" baseline grid?

A "global" baseline grid (or, "document-based" baseline grid) consists of applying a grid to the document's `<body>` and then aligning all the text to a vertical grid, set in even increments all the way down the page, where the bottom of each letter is positioned onto the grid, just like writing on lined paper.

### What is a "local" baseline grid?

A "local" baseline grid is exactly like the above, except the grid gets applied directly to "modules", "content areas" or elements and the alignment happens relative to the application of the vertical grid.

### Why use a "local" baseline?

While a "global" baseline grid might work well in print, on the web there are numerous situations where baseline grid alignment isn't practical.

Using a "local" baseline allows the developer to focus on the baseline grid alignment for a particular "module", "content area" or element whilst relieving the pressure to maintain baseline alignment between the aforementioned items.

The goal is to use a "local" baseline (and the math that powers it) as a quick and easy way to add vertical "meaning" to a page's content (much in the same way that a "horizontal" grid (rows/cols) gives "meaning" to a page's layout).

### Why "Rex"?

Just watch **[Rustlers' Rhapsody](http://amzn.to/19CUPdE)** ([Amazon VOD](http://amzn.to/18PXwre)) and all will be explained. :)

## Demonstration&nbsp;[&#8613;](#table-of-contents)

DEVELOPMENT &bull;&nbsp;[html](https://raw.github.com/mhulse/rex/gh-pages/demo/index.html) &bull;&nbsp;[css](https://raw.github.com/mhulse/rex/gh-pages/rex/rex.css) | PRODUCTION &bull;&nbsp;[html](https://raw.github.com/mhulse/rex/gh-pages/demo/index.min.html) &bull;&nbsp;[css](https://raw.github.com/mhulse/rex/gh-pages/rex/rex.min.css)
:-: | :-:
[![qr code](http://chart.apis.google.com/chart?cht=qr&chl=http://mhulse.github.io/rex/demo/&chs=240x240)](http://mhulse.github.io/rex/demo/) | [![qr code](http://chart.apis.google.com/chart?cht=qr&chl=http://mhulse.github.io/rex/demo/index.min.html&chs=240x240)](http://mhulse.github.io/rex/demo/index.min.html)

**Note:** Only the [`DEVELOPMENT` demo](http://mhulse.github.io/rex/demo/) uses [`normalize.css`](http://necolas.github.io/normalize.css/).

## Installation&nbsp;[&#8613;](#table-of-contents)

There are several ways to install this code:

1. Download as a [`zip`](https://github.com/mhulse/rex/archive/gh-pages.zip).
1. Clone it: `$ git clone https://github.com/mhulse/rex.git`.
1. Fork it and clone: `$ git clone git@github.com:USERNAME/rex.git`.
1. Just grab the relevant [CSS](https://raw.github.com/mhulse/rex/gh-pages/rex/rex.css) ([minified](https://raw.github.com/mhulse/rex/gh-pages/rex/rex.min.css)) and/or [SCSS](https://github.com/mhulse/rex/tree/gh-pages/rex/scss) files.
1. Using [Bower](http://bower.io/): `$ bower install https://github.com/mhulse/rex.git`.

### Build process:

In order to build from source, you'll need to install [Grunt.js: The JavaScript Task Runner](http://gruntjs.com/).

From there, `$ cd source/` and run `$ npm install`; after the [dependencies](https://github.com/mhulse/rex/blob/gh-pages/source/package.json) have been installed, run `$ grunt bower` (this installs [`normalize.css`](http://necolas.github.io/normalize.css/) as a [Bower](http://bower.io/) dependency).

For subsequent builds, just run `$ grunt`; this default task will generate or copy files, based on the [`Gruntfile.js`](https://github.com/mhulse/rex/blob/gh-pages/source/Gruntfile.js) configuration and files found in the `/source` folder, into the `/demo` folder.

Run `$ grunt watch` to automatically regenerate build files when you modify the `Gruntfile.js`, any of the templates or SCSS files.

## SCSS API&nbsp;[&#8613;](#table-of-contents)

Available SCSS overrides and utilities:

### Variables:

Name | Description | Default
:-- | :-- | :--
`$REX` | Selector's "pseudo namespace" prefix | `rex_`
`$rex_browser-font-size` | Browser default `font-size`. | `16px`
`$rex_base-font-size` | Base `font-size`. | `16px`
`$rex_base-line-height` | Base `line-height`. | `24px`
`$rex_flag-natural-box-model` | Natural box layout? | `true`
`$rex_flag-heading-classes` | Heading classes? | `true`
`$rex_flag-subheading-classes` | Subheading classes? | `true`
`$rex_flag-tables` | Table styles? | `true`
`$rex_flag-forms` | Form styles? | `true`
`$rex_flag-baseline` | Include the baseline class? | `true`
`$rex_baseline-major-grid-color` | Baseline "major" grid color. | `#f00`
`$rex_baseline-minor-grid-color` | Baseline "minor" grid color. | `#0ff`
`$rex_baseline-outline-color` | Baseline "outline" grid color. | `#f00`

### Functions:

Name | Description
:-- | :--
`rex_strip($value, ...)` | Remove units from `$value`.
`rex_relative($value, ...)` | Convert `$value` to relative number.
`rex_baseline($value, ...)` | Calculate baseline from `$value`, which is assumed to be the baseline's element's `font-size`.

### Mixins:

Name | Shorthand | Description
:-- | :-- | :--
`rex_baseline` | `rex_bl` | Simple baseline mixin.
`rex_baseline-grid` | `rex_blg` | Baseline grid css.

## CSS&nbsp;[&#8613;](#table-of-contents)

CSS details:

### Features:

Feature | Description
:-- | :--
`rex_` | All rex classes have a "pseudo namespace" (which is controlled via the SCSS `$REX` variable).
`16px`/`24px` | Base `font-size` is `16px` and base `line-height` is `24px`; both of these values can be controlled via the SCSS variables `$rex_base-font-size` and `$rex_base-line-height` respectively.
`rem` & `em` | All units are relative; using `rem` and `em` where appropriate.
`border-box` | If `$rex_flag-natural-box-model` is `true`, then all elements (including pseudo elements) will use `box-sizing: border-box;`; this change affects the box model in that the `width` and `height` properties include the `padding` and `border`, but not the `margin`.
`.baseline` | If `$rex_flag-baseline` is `true`, then a `.baseline` class becomes available for use; this class should be applied to a wrapping `div` in order to test a "module", "content area" or element's placement on a "local" baseline grid. When the grid is clicked (i.e., `:active`) the base lines will hide and each child element will be outlined with a red border.
`.h1`-`.h6` | All headings (e.g., `h1` through `h6`) have a corresponding class of the same name (i.e., `.h1` through `.h6`); for more information, read: [Don’t Style Headings Using HTML5 Sections](http://www.stubbornella.org/content/2011/09/06/style-headings-using-html5-sections/). These classes can be disabled via the `$rex_flag-heading-classes` variable.
`.sh1`-`.sh6` | In the same vein as the heading classes above, there's a set of subheading classes (i.e., `.sh1` through `.sh6`) that have similar functionality and can be disabled via the `$rex_flag-subheading-classes` variable.

## Caveats, limitations and/or assumptions&nbsp;[&#8613;](#table-of-contents)

1. If you change the base `font-size` and `line-height`, there's no guarantees that out of the box styles will adapt well; in other words, changing these variables will probably require one to adjust each of Rex's elements to fit the new base values (for more information, see [Q & A](#qa) section below).
1. Due to the proverbial "fudge factor", the `.baseline` class does not actually align its grid lines to the baseline of a character; instead, this class aligns the text to the vertical center of a grid line.
1. Buyer beware: I make heavy use of the [`rem` unit](http://snook.ca/archives/html_and_css/font-size-with-rem), with [no fallbacks](http://caniuse.com/#search=rem).

## Q&nbsp;&amp;&nbsp;A&nbsp;[&#8613;](#table-of-contents)

**Q: How do I make everything smaller?**

**A:** Easy. Just override these two variables:

```text
$rex_base-font-size: 14px;
$rex_base-line-height: 22px;
```

![Bam!](https://f.cloud.github.com/assets/218624/1966914/e42a5ee8-82ce-11e3-8fe1-758f00f88f65.gif)

## Contributing&nbsp;[&#8613;](#table-of-contents)

Please review the [contributing guidelines](https://github.com/mhulse/rex/blob/gh-pages/CONTRIBUTING.md) for this repository.

### Bumping the version:

When a build is ready for a version bump ...

1. Update `version` key value in `source/package.json`.
1. Update `version` key value in `bower.json`.
1. Build: `$ grunt`.
1. Update the [changelog](#changelog) and [release history](#release-history) in the [README.md](https://github.com/mhulse/rex/blob/gh-pages/README.md) (if copy/pasting, don't forget to update the date and version numbers).
1. Push changes to GitHub.
1. Visit the [releases page](https://github.com/mhulse/rex/releases) and click "[Draft a new release](https://github.com/mhulse/rex/releases/new)".
1. Type the new version number in the "Tag version" field (e.g., `v1.2.1`).
1. Click "Publish release".

**Note:** REX uses [Semantic Versioning](http://semver.org/).

## Feedback&nbsp;[&#8613;](#table-of-contents)

[Bugs? Constructive feedback? Questions?](https://github.com/mhulse/rex/issues/new?title=Your%20code%20sucks!&body=Here%27s%20why%3A%20)

## Changelog&nbsp;[&#8613;](#table-of-contents)

* [v3.0.0 milestones](https://github.com/mhulse/rex/issues?direction=desc&milestone=4&page=1&sort=updated&state=closed)
* [v2.0.0 milestones](https://github.com/mhulse/rex/issues?direction=desc&milestone=4&page=1&sort=updated&state=closed)
* [v1.2.0 milestones](https://github.com/mhulse/rex/issues?direction=desc&milestone=3&page=1&sort=updated&state=closed)
* [v1.1.0 milestones](https://github.com/mhulse/rex/issues?direction=desc&milestone=2&page=1&sort=updated&state=closed)
* [v1.0.0 milestones](https://github.com/mhulse/rex/issues?direction=desc&milestone=1&page=1&sort=updated&state=closed)

## [Release history](https://github.com/mhulse/rex/releases)&nbsp;[&#8613;](#table-of-contents)

* 2014-01-24   [v3.0.0](https://github.com/mhulse/rex/releases/tag/v3.0.0)   Namespaces.
* 2013-11-09   [v2.0.0](https://github.com/mhulse/rex/releases/tag/v2.0.0)   Simplified base styles.
* 2013-11-03   [v1.2.1](https://github.com/mhulse/rex/releases/tag/v1.2.1)   Minor v1.2.1 patch.
* 2013-11-01   [v1.2.0](https://github.com/mhulse/rex/releases/tag/v1.2.0)   More control.
* 2013-09-15   [v1.1.0](https://github.com/mhulse/rex/releases/tag/v1.1.0)   Better organization.
* 2013-09-13   [v1.0.0](https://github.com/mhulse/rex/releases/tag/v1.0.0)   On, Wildfire, on!
* 2013-08-25   [v0.4.0](https://github.com/mhulse/rex/releases/tag/v0.4.0)   Bower version bump.
* 2013-08-18   [v0.3.0](https://github.com/mhulse/rex/releases/tag/v0.3.0)   SCSS build setup.
* 2013-08-16   [v0.2.0](https://github.com/mhulse/rex/releases/tag/v0.2.0)   Bower pre-release.
* 2013-08-10   [v0.1.0](https://github.com/mhulse/rex/releases/tag/v0.1.0)   Maximum Grunt setup.

---

#### LEGAL

Copyright &copy; 2013-2014 [Micky Hulse](http://mky.io)

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

<img width="20" height="20" align="absmiddle" src="https://github.global.ssl.fastly.net/images/icons/emoji/octocat.png" alt=":octocat:" title=":octocat:" class="emoji">