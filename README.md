# nanocomponentcache
[![npm version][2]][3] [![build status][4]][5]
[![downloads][8]][9] [![js-standard-style][10]][11]

Cache Nanocomponents.

## Usage
### my-component.js
```js
var Component = require('choo/component')
var html = require('choo/html')

module.exports = class Article extends Component {
  static identity (article) {
    return `article-${article.id}`
  }

  createElement (article) {
    return html`
      <article>
        <h2>${article.title}</h2>
        <p>${article.body}</p>
      </article>
    `
  }

  update () {
    return false
  }
}
```

### example.js
```js
var myComponent = require('./my-component')
var Nanocache = require('nanocomponentcache')

var cache = new Nanocache()
cache(myComponent)
// => create a new instance of myComponent

cache(myComponent)
// => return cached instance of myComponent
```

## API
### `cache = Nanocache()`
Create a new Nanocache instance.

### `cache.render(Nanocomponent)`
Render a Nanocomponent instance. It checks a static `identity` method that
returns an id. If the id is not registered in the cache, it creates a new
instance and caches it. If the id already exists, it returns the cached
instance.

### `cache.prune()`
Remove all components from the cache that don't currently have a DOM node
attached.

## Installation
```sh
$ npm install nanocomponentcache
```

## See Also
- [choojs/nanocomponent](https://github.com/choojs/nanocomponent)

## License
[Apache-2.0](./LICENSE)

[0]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/nanocomponentcache.svg?style=flat-square
[3]: https://npmjs.org/package/nanocomponentcache
[4]: https://img.shields.io/travis/yoshuawuyts/nanocomponentcache/master.svg?style=flat-square
[5]: https://travis-ci.org/yoshuawuyts/nanocomponentcache
[6]: https://img.shields.io/codecov/c/github/yoshuawuyts/nanocomponentcache/master.svg?style=flat-square
[7]: https://codecov.io/github/yoshuawuyts/nanocomponentcache
[8]: http://img.shields.io/npm/dm/nanocomponentcache.svg?style=flat-square
[9]: https://npmjs.org/package/nanocomponentcache
[10]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[11]: https://github.com/feross/standard
