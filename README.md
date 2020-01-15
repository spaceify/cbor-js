This is an up-to-date fork of the paroga/cbor-js by Patrick Gansterer. In early 2020, we were searching for a Javascript CBOR library, and found the excellent paroga/cbor-js, which sadly had not been updated for several years. Because we really needed a CBOR library in our projects, we decided to fork the repository and bring it up-to-date.

Goals of this fork:

- Merge all open pull requests of the original paroga/cbor-js (DONE)
- Resolve open issues of the original paroga/cbor-js (PARTLY DONE)
- Optimize for speed (TBD)
- Add more tests and benchamrking (TBD)
- Add support for tagging (TBD)
- Publish on npm (TBD)
 
cbor-js
=======

The Concise Binary Object Representation (CBOR) data format ([RFC 7049](http://tools.ietf.org/html/rfc7049)) implemented in pure JavaScript.

[![Build Status](https://api.travis-ci.org/paroga/cbor-js.svg)](https://travis-ci.org/paroga/cbor-js)
[![Coverage Status](https://coveralls.io/repos/paroga/cbor-js/badge.svg?branch=master)](https://coveralls.io/r/paroga/cbor-js?branch=master)
[![Dependency status](https://david-dm.org/paroga/cbor-js/status.svg)](https://david-dm.org/paroga/cbor-js#info=dependencies&view=table)
[![Dev Dependency Status](https://david-dm.org/paroga/cbor-js/dev-status.svg)](https://david-dm.org/paroga/cbor-js#info=devDependencies&view=table)
[![Selenium Test Status](https://saucelabs.com/buildstatus/paroga-cbor-js)](https://saucelabs.com/u/paroga-cbor-js)

[![Selenium Test Status](https://saucelabs.com/browser-matrix/paroga-cbor-js.svg)](https://saucelabs.com/u/paroga-cbor-js)

API
---

The `CBOR`-object provides the following two functions:

CBOR.**decode**(*data*)
> Take the ArrayBuffer object *data* and return it decoded as a JavaScript object.

CBOR.**encode**(*data*)
> Take the JavaScript object *data* and return it encoded as a ArrayBuffer object.

Usage
-----

Include `cbor.js` in your or HTML page:
```html
<script src="path/to/cbor.js" type="text/javascript"></script>
```

Then you can use it via the `CBOR`-object in your code:
```javascript
var initial = { Hello: "World" };
var encoded = CBOR.encode(initial);
var decoded = CBOR.decode(encoded);
```
After running this example `initial` and `decoded` represent the same value.

### Combination with WebSocket

The API was designed to play well with the `WebSocket` object in the browser:
```javascript
var websocket = new WebSocket(url);
websocket.binaryType = "arraybuffer";
...
websocket.onmessage = function(event) {
  var message = CBOR.decode(event.data);
};
...
websocket.send(CBOR.encode(message));
```
