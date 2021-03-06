# iframe-postbox
> A postmessage library inspire by [Postmate](https://github.com/dollarshaveclub/postmate)

Use [`window.postMessage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) method to communication in iframe

## Install

npm install

`$ npm i --save iframe-postbox`

browser import

`<script src="node_modules/iframe-postbox/postbox.js></script>`

## Usage

parent.com

```js
var handshake = new Postbox({
  container: document.getElementById('some-div'), // Element to inject iframe into
  url: 'http://child.com/page.html'
});

handshake.then(function(child) {
  child.get('name').then(function(value) {
    alert(value)
  };

  child.on('some-event', function(data) {
    console.log(data)
  };
};
```

child.com/page.html

```js
var handshake = new Postbox.Client({
  name: 'iframe child'
});

handshake.emit('some-event', 'Hello world')
```

## API

See https://huang-x-h.github.io/iframe-postbox/api/index.html

## Browser support

`postbox.js` support `IE9+/Chrome/Safari/Firefox`, `Promise` polyfill

`postbox.jquery.js` supoort `IE8+/Chrome/Safari/Firefox`, base on `jquery` (use `Deferred` instead of 'Promise')
