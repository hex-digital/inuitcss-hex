# ![inuitcss](http://inuitcss.com/img/logo-small.png)

[![CircleCI](https://img.shields.io/circleci/project/inuitcss/inuitcss/master.svg?maxAge=2592000?style=flat-square)](https://circleci.com/gh/inuitcss/inuitcss)  
[![CircleCI](https://img.shields.io/circleci/project/hex-digital/inuitcss-hex/master.svg?maxAge=2592000?style=flat-square)](https://circleci.com/gh/hex-digital/inuitcss-hex)

**An extension to the extensible, scalable, Sass-based, OOCSS framework for 
large and long-lasting UI projects.**

inuitcss is a framework in its truest sense: it does not provide you with UI and
design out of the box, instead, it provides you with a solid architectural
baseline upon which to complete your own work.

This extension is a means of bringing commonly used areas from Hex sites into a
package that can then be used ontop of inuit.

The following README assumes you have already followed the inuitcss installation
and setup guide in thee [inuitcss repo](https://github.com/inuitcss/inuitcss).

## Installation

You can install inuitcss-hex in your project by using a package manager (we 
recommend yarn):

**yarn:**

    yarn add inuitcss-hex --dev

**npm:**

    npm install inuitcss-hex --save-dev

## Getting Started

Assuming you have got inuitcss-hex into your project using one of the above
methods, you can now include the files you need in your existing main.scss file
that was setup for inuitcss.

Simply link to it the same way you link to a core inuit file, and you're set!

## CSS directory structure

inuitcss follows a specific folder structure, which you should follow as well in your own CSS directory:

* `/settings`: Global variables, site-wide settings, config switches, etc.
* `/tools`: Site-wide mixins and functions.
* `/generic`: Low-specificity, far-reaching rulesets (e.g. resets).
* `/elements`: Unclassed HTML elements (e.g. `a {}`, `blockquote {}`, `address {}`).
* `/objects`: Objects, abstractions, and design patterns (e.g. `.o-layout {}`).
* `/components`: Discrete, complete chunks of UI (e.g. `.c-carousel {}`). This is the one layer that inuitcss doesn’t provide code for, as this is completely your terrain.
* `/utilities`: High-specificity, very explicit selectors. Overrides and helper
  classes (e.g. `.u-hidden {}`).

Following this structure allows you to intersperse inuitcss’ code with your own,
so that your `main.scss` file might look something like this:

```scss
// SETTINGS
@import "settings/settings.config";
@import "node_modules/inuitcss/settings/settings.core";
@import "node_modules/inuitcss-hex/settings/settings.global";
@import "settings/settings.colors";
etc...
```

Interlacing partials like this is one of the real strengths of inuitcss.

## Extending inuitcss

To extend inuitcss with your own code, simply create a partial in the `<section>.<file>` format, put it into the [appropriate directory](#css-directory-structure) and `@import` it in your `main.scss`.

But extending inuitcss does not only mean adding your own partials to the project. Due to inuitcss’ modular nature, you can also omit those partials of inuitcss you don't need. But be aware that there are a few interdependencies between various inuitcss partials. The only partial that is indispensable for the framework to work properly is `settings.core`, though. But we recommend using all partials from the `/settings`, `/tools` and `/generic` layer.
