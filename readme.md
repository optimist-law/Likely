![Likely logo](logo.png)

The social sharing buttons that aren’t shabby

## Take a look

See Likely in action on its [homepage](http://ilyabirman.net/projects/likely/).

[![Likely screenshot](http://i.imgur.com/ipqE5Tu.png)](http://ilyabirman.net/projects/likely/)

## Get

[Download the repository code](https://github.com/ilyabirman/Likely/archive/master.zip) and move `release/likely.js` and
`release/likely.css` to the desired directory.

Or use npm or Bower:

```sh
$ npm install ilyabirman-likely --save
$ bower install ilyabirman-likely --save
```

Also you can use Likely from CDN:

https://unpkg.com/ilyabirman-likely@2/release/likely.css
<br>
https://unpkg.com/ilyabirman-likely@2/release/likely.js

## Setup

Link the files `likely.css` and `likely.js` from the compiled sources.

If downloaded directly:
```html
<!-- Head -->
<link href="path/to/likely.css" rel="stylesheet">
<!-- End of body -->
<script src="path/to/likely.js" type="text/javascript"></script>
```

If installed with npm:

```html
<!-- Head -->
<link href="node_modules/ilyabirman-likely/release/likely.css"
      rel="stylesheet">
<!-- End of body -->
<script src="node_modules/ilyabirman-likely/release/likely.js"
        type="text/javascript"></script>
```

If installed with Bower:

```html
<!-- Head -->
<link href="bower_components/Likely/release/likely.css"
      rel="stylesheet">
<!-- End of body -->
<script src="bower_components/Likely/release/likely.js"
        type="text/javascript"></script>
```

Then, create a `div` with the class `likely` and list necessary social networks in child `div`s:

```html
<div class="likely">
    <div class="facebook">Share</div>
    <div class="twitter">Tweet</div>
    <div class="vkontakte">Share</div>
    <div class="pinterest">Pin</div>
    <div class="odnoklassniki">Like</div>
    <div class="telegram">Send</div>
    <div class="linkedin">Share</div>
    <div class="whatsapp">Send</div>
    <div class="viber">Send</div>
    <div class="reddit">Share</div>
</div>
```
Likely supports following social networks:

* `facebook` – Facebook
* `twitter` – Twitter
* `vkontakte` – VK
* `pinterest` – Pinterest
* `odnoklassniki` – Odnoklassniki
* `telegram` – Telegram
* `linkedin` – LinkedIn
* `whatsapp` – WhatsApp
* `viber` – Viber
* `reddit` – Reddit

If you need several Likely widgets on the page, just create another `div` with the class `likely` and list the social networks in it.

### Using as a CommonJS module

Likely can be used as a CommonJS module, so you can use it within webpack or browserify build systems.

First, install Likely using npm:

```sh
$ npm install ilyabirman-likely --save
```

Then, use it as CommonJS module somewhere in your program:

```js
var likely = require('ilyabirman-likely');

// Finds all the widgets in the DOM and initializes them
likely.initiate();
```

## Options

You can configure Likely by specifying `data-*` attributes on a button group or on a button.

### Common options

These options can be specified on the `div` with the `likely` class (current page URL and title will be used as a fallback).

* `data-url` – URL to share and load counters for (⚠ specify the full URL with the protocol – like in `https://ilyabirman.com` – because some social networks don’t recognize the partial one)


* `data-title` – Page title

* `data-counters` – pass "no" to disable counters (enabled by default)

```html
<div class="likely" data-url="https://github.com/ilyabirman/Likely">
    <!-- ... -->
</div>
```

### Twitter

You can set `data-via` attribute to mention a specific user in the tweet:

```html
<div class="twitter" data-via="ilyabirman">Tweet</div>
```

With `data-via="ilyabirman"`, the tweet text will include “via @ilyabirman”. Read more about the `via` parameter [in the Twitter documentation](https://dev.twitter.com/web/tweet-button#component-via).

### Telegram

You can set `data-text` attribute to define a text of the message.

```html
<div class="telegram" data-text="Check this out">Send</div>
```

### Pinterest

You can set `data-media` attribute to override a default image and substitute a different one in the Pin Create form.
The attribute should be an image URL:

```html
<div class="pinterest" data-media="https://placekitten.com/200/400">Pin</div>
```

Read more about the `media` parameter in the [in the Pinterest documentation](https://developers.pinterest.com/docs/widgets/pin-it/#source-settings).


### VK

You can set `data-image` and `data-description` attributes to set up an image and a description accordingly:

```html
<div class="vkontakte" data-image="https://placekitten.com/200/400" data-description="Check this out">Share</div>
```

### Viber

You can set `data-comment` attribute to specify some text that's going to be added to a shared link (on a separate line).

```html
<div class="viber" data-comment="Check this out">Send</div>
```

### Reinitialize configuration on change data attributes

If you need to dynamically change the widget's configuration for sharing use, you can re-initialize the widget and invoke the configuration update logic on the *Likely* instance using the `init` method.


1. Likely widget in html template

```html
<div class="likely" data-url="https://google.com">
    <div class="twitter">Tweet</div>
    <div class="facebook">Share</div>
    <div class="vkontakte">Share</div>
    <div class="odnoklassniki">Like</div>
    <div class="pinterest">Pin</div>
    <div class="telegram">Send</div>
    <div class="linkedin">Share</div>
    <div class="whatsapp">Send</div>
    <div class="viber">Send</div>
</div>
```

2. Attributes for button elements are updated.

3. Logic for update configuration using *Likely* as an example

```javascript
// find in dom likely
const likelyWidget = document.querySelector(".likely");

// find instance of likely 
const likelyInstance = likelyWidget.likely;

// Call inner method for update options from data attributes
likelyInstance.init();
```

### Accessibility Settings

To make buttons accessible for keyboard navigation and screen readers add `tabindex`, `role` and `aria-label` attributes:

```html
<div class="likely">
    <div class="facebook" tabindex="0" role="link" aria-label="Share on Facebook">Share</div>
    <div class="twitter" tabindex="0" role="link" aria-label="Tweet on Twitter">Tweet</div>
    <div class="vkontakte" tabindex="0" role="link" aria-label="Share on Vkontakte">Share</div>
    <div class="pinterest" tabindex="0" role="link" aria-label="Pin on Pinterest">Pin</div>
    <div class="odnoklassniki" tabindex="0" role="link" aria-label="Like on Odnoklassniki">Like</div>
    <div class="telegram" tabindex="0" role="link" aria-label="Send on Telegram">Send</div>
    <div class="linkedin" tabindex="0" role="link" aria-label="Share on LinkedIn">Share</div>
    <div class="whatsapp" tabindex="0" role="link" aria-label="Send on WhatsApp">Send</div>
    <div class="viber" tabindex="0" role="link" aria-label="Send on Viber">Send</div>
    <div class="reddit" tabindex="0" role="link" aria-label="Share on Reddit">Share</div>
</div>
```

## Supported browsers

We support IE 10+, Safari 9+ and the latest versions of Chrome, Firefox and Edge. Likely could work in the older versions too, but we don’t do anything specific to maintain its compatibility with them and don’t test it there.

# Development
Please use the [Github commit style](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53).
Before pushing make sure the tests are green and the linter does not complain. 
```bash
npm test
npm run-script check-codestyle
```
Also please add your own tests if you are submitting a feature.
