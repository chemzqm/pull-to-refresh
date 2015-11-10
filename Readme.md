# Pull-to-refresh

  [![Build Status](https://secure.travis-ci.org/chemzqm/pull-to-refresh.svg)](http://travis-ci.org/chemzqm/pull-to-refresh)
  [![Coverage Status](https://coveralls.io/repos/chemzqm/pull-to-refresh/badge.svg?branch=master&service=github)](https://coveralls.io/github/chemzqm/pull-to-refresh?branch=master)

  A pull to refresh component for developers who loves elegence solution.

  Now works with webpack and browserify, it's supposed to works with [iscroll-component](https://github.com/chemzqm/iscroll)

  To make them works reansonable, they are decoupled in 1.0.0

  [demo](http://chemzqm.github.io/pull-to-refresh).
  [code of demo](https://github.com/chemzqm/pull-to-refresh/blob/gh-pages/index.js)

  Tip: Avoid to use transition when dragging.

## Features

* optional options for setting texts and timeout.
* call refresh as you need.
* simplified code and API.

## Installation

  Prefer to install with npm:

    $ npm install pull-to-refresh

  Install with [component(1)](http://component.io):

    $ component install chemzqm/pull-to-refresh

## Example
``` css
.scrollable {
  position: fixed;
  top: 50px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  overflow-y: scroll;
  -webkit-overflow-scrolling: touch;
}
```
``` html
<div id="demo" class="scrollable">
  <div>
    <ul>
      <li></li>
    </ul>
  </div>
</div>
```
Notice the scrollable have a single child for [iscroll-component](https://github.com/chemzqm/iscroll) to work

``` js
var el = document.getElementById('demo')
var Ptr = require('pull-to-refresh')
var is = Iscroll(el, { handlebar: true })
var ptr = new Ptr(el, function(cb) {
    ajax_and_prepend_dom( )//load your data and append them to the list
    cb() //You can use the callback or return a promise
  })
})
```
You can think iscroll just add nagetive scrollTop value to the scrollable.

## API

### Ptr(el, [option], callback)

* `callback` is called when loading start, the first argument which is a callback function should be called after the dom prepend to the list.
* `option` object could contain `PULL_TEXT` `RELEASE_TEXT` `LOADING_TEXT` and `timeout` for the request timeout in millisecond.

### .refresh()

Perform refresh (with animation scroll to top at first).

### .unbind()

Unbind all event listeners

## License

  The MIT License (MIT)
