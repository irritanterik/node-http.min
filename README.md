# Minimal HTTP library
[![Build status][travis-image]][travis-url] [![Coverage Status][coverage-image]][coverage-url] [![js-standard-style][standard-image]][standard-url] [![Dependencies][david-image]][david-url] [![devDependencies][david-dev-image]][david-dev-url]

Minimal simple API for HTTP with promises.  
Supports common methods GET, POST, PUT, PATCH, DELETE and JSON parsing.  
Under 100 SLOC.  

## Install

    npm install --save http.min

## Examples

### GET
```javascript
var http = require('http.min')
http.get('https://httpbin.org/get').then(function (result) {
  console.log('Code: ' + result.response.statusCode)
  console.log('Response: ' + result.data)
})
```

### POST
```javascript
var http = require('http.min')
http.post('https://httpbin.org/post', {data: 'hello'}).then(function (result) {
  console.log('Code: ' + result.response.statusCode)
  console.log('Response: ' + result.data)
})
```

Form urlencoded. Second `data` parameter is a string instead of an object.

```javascript
var http = require('http.min')
http.post('https://httpbin.org/post', 'data=hello').then(function (result) {
  console.log('Code: ' + result.response.statusCode)
  console.log('Response: ' + result.data)
})
```

### JSON
```javascript
var http = require('http.min')
http.json('https://httpbin.org/get').then(function (data) {
  console.log('Response:', data.url)
})
```

### Advanced
It accepts [http.request options][node-http-options]
```javascript
var http = require('http.min')
var options = {
  protocol: 'https:',
  hostname: 'httpbin.org',
  path: '/get',
  headers: {
    'User-Agent': 'Node.js http.min'
  }
}
http.json(options).then(function (data) {
  console.log('Response:', data)
})
```

## License
ISC


[travis-image]: https://img.shields.io/travis/matjaz/node-http.min/master.svg?style=flat
[travis-url]: https://travis-ci.org/matjaz/node-http.min
[coverage-image]: https://img.shields.io/coveralls/matjaz/node-http.min/master.svg?style=flat
[coverage-url]: https://coveralls.io/r/matjaz/node-http.min
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg
[standard-url]: http://standardjs.com
[david-image]: https://img.shields.io/david/matjaz/node-http.min.svg?style=flat
[david-url]: https://david-dm.org/matjaz/node-http.min
[david-dev-image]: https://img.shields.io/david/dev/matjaz/node-http.min.svg?style=flat
[david-dev-url]: https://david-dm.org/matjaz/node-http.min#info=devDependencies
[node-http-options]: https://nodejs.org/api/http.html#http_http_request_options_callback
