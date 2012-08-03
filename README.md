## jquery.haircut.js

** **

We've got plenty of long filenames in the LayerVault file dashboard. We needed
a way to condense them to fit into the interface while still displaying important
parts (like the file extension). Thus, Haircut was born.

Haircut will ellipsize a string of text to fit inside of its parent container without
overflowing or breaking to another line.

You can see a video of it in action here: [Haircut in Action](https://vimeo.com/user7743505/review/46901981/e833d7d78d).

## Setup

First, include haircut on the page. Bonus points for rolling it into your asset pipeline.

```javascript
<script type="text/javascript" src="/jquery.haircut.js"></script>
```

Next, select the items on the page you want to haircut.

```javascript
$(function () {
  $('.Filename').haircut();
});
```

Next, you will need to call the method `stringResize` whenever your layout changes. This
has been abstracted out for now so that users can use things like the Underscore [throttle](http://underscorejs.org/#throttle)
and [debounce](http://underscorejs.org/#debounce) methods. It's highly recommended that you use these if you've got a heavy page.

```javascript
$(window).resize(function () {
  $('.Filename').stringResize();
});
```

## Configuration

Haircut has a few configuration parameters that will help with tweaking performance and deciding
which part of the string get ellipsized. Set the options like so:

```javascript
  $('.Filename').haircut({
    //Clips text when the page resizes
    bindToResize      : true,

    //Only clips text that's in the viewport
    bindToScroll      : true,

    //The more haircut items on the page, the more it jitters during animation.
    // Adding padding reduces jitter but gives you less usable space.
    jitterPadding     : 30,

    // The placement of the ellipsis. Can be "beginning", "middle" or "end"
    // Defaults to "middle"
    placement         : "middle"
  });
```

## Authors

Written by Allan Grinshtein and Kelly Sutton for LayerVault. Licensed under the MIT License.