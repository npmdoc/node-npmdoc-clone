# api documentation for  [clone (v2.1.1)](https://github.com/pvorb/node-clone#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-clone.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-clone) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-clone.svg)](https://travis-ci.org/npmdoc/node-npmdoc-clone)
#### deep cloning of objects and arrays

[![NPM](https://nodei.co/npm/clone.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/clone)

[![apidoc](https://npmdoc.github.io/node-npmdoc-clone/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-clone/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-clone/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-clone/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Paul Vorbach",
        "url": "http://paul.vorba.ch/"
    },
    "bugs": {
        "url": "https://github.com/pvorb/node-clone/issues"
    },
    "contributors": [
        {
            "name": "Blake Miner",
            "url": "http://www.blakeminer.com/"
        },
        {
            "name": "Tian You",
            "url": "http://blog.axqd.net/"
        },
        {
            "name": "George Stagas",
            "url": "http://stagas.com/"
        },
        {
            "name": "Tobiasz Cudnik",
            "url": "https://github.com/TobiaszCudnik"
        },
        {
            "name": "Pavel Lang",
            "url": "https://github.com/langpavel"
        },
        {
            "name": "Dan MacTough",
            "url": "http://yabfog.com/"
        },
        {
            "name": "w1nk",
            "url": "https://github.com/w1nk"
        },
        {
            "name": "Hugh Kennedy",
            "url": "http://twitter.com/hughskennedy"
        },
        {
            "name": "Dustin Diaz",
            "url": "http://dustindiaz.com"
        },
        {
            "name": "Ilya Shaisultanov",
            "url": "https://github.com/diversario"
        },
        {
            "name": "Nathan MacInnes",
            "url": "http://macinn.es/"
        },
        {
            "name": "Benjamin E. Coe",
            "url": "https://twitter.com/benjamincoe"
        },
        {
            "name": "Nathan Zadoks",
            "url": "https://github.com/nathan7"
        },
        {
            "name": "Róbert Oroszi",
            "url": "https://github.com/oroce"
        },
        {
            "name": "Aurélio A. Heckert",
            "url": "http://softwarelivre.org/aurium"
        },
        {
            "name": "Guy Ellis",
            "url": "http://www.guyellisrocks.com/"
        },
        {
            "name": "fscherwi",
            "url": "https://fscherwi.github.io"
        },
        {
            "name": "rictic",
            "url": "https://github.com/rictic"
        },
        {
            "name": "Martin Jurča",
            "url": "https://github.com/jurca"
        },
        {
            "name": "Misery Lee",
            "url": "https://github.com/miserylee"
        },
        {
            "name": "Clemens Wolff",
            "url": "https://github.com/c-w"
        }
    ],
    "dependencies": {},
    "description": "deep cloning of objects and arrays",
    "devDependencies": {
        "nodeunit": "~0.9.0"
    },
    "directories": {},
    "dist": {
        "shasum": "d217d1e961118e3ac9a4b8bba3285553bf647cdb",
        "tarball": "https://registry.npmjs.org/clone/-/clone-2.1.1.tgz"
    },
    "engines": {
        "node": ">=0.8"
    },
    "gitHead": "a321fd85bb79f787fb33ba5f9a44d2ad480832ef",
    "homepage": "https://github.com/pvorb/node-clone#readme",
    "license": "MIT",
    "main": "clone.js",
    "maintainers": [
        {
            "name": "pvorb"
        }
    ],
    "name": "clone",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/pvorb/node-clone.git"
    },
    "scripts": {
        "test": "nodeunit test.js"
    },
    "tags": [
        "clone",
        "object",
        "array",
        "function",
        "date"
    ],
    "version": "2.1.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module clone](#apidoc.module.clone)
1.  [function <span class="apidocSignatureSpan"></span>clone (parent, circular, depth, prototype, includeNonEnumerable)](#apidoc.element.clone.clone)
1.  [function <span class="apidocSignatureSpan">clone.</span>__getRegExpFlags (re)](#apidoc.element.clone.__getRegExpFlags)
1.  [function <span class="apidocSignatureSpan">clone.</span>__isArray (o)](#apidoc.element.clone.__isArray)
1.  [function <span class="apidocSignatureSpan">clone.</span>__isDate (o)](#apidoc.element.clone.__isDate)
1.  [function <span class="apidocSignatureSpan">clone.</span>__isRegExp (o)](#apidoc.element.clone.__isRegExp)
1.  [function <span class="apidocSignatureSpan">clone.</span>__objToStr (o)](#apidoc.element.clone.__objToStr)
1.  [function <span class="apidocSignatureSpan">clone.</span>clonePrototype (parent)](#apidoc.element.clone.clonePrototype)
1.  [function <span class="apidocSignatureSpan">clone.</span>toString ()](#apidoc.element.clone.toString)



# <a name="apidoc.module.clone"></a>[module clone](#apidoc.module.clone)

#### <a name="apidoc.element.clone.clone"></a>[function <span class="apidocSignatureSpan"></span>clone (parent, circular, depth, prototype, includeNonEnumerable)](#apidoc.element.clone.clone)
- description and source-code
```javascript
function clone(parent, circular, depth, prototype, includeNonEnumerable) {
  if (typeof circular === 'object') {
    depth = circular.depth;
    prototype = circular.prototype;
    includeNonEnumerable = circular.includeNonEnumerable;
    circular = circular.circular;
  }
  // maintain two arrays for circular references, where corresponding parents
  // and children have the same index
  var allParents = [];
  var allChildren = [];

  var useBuffer = typeof Buffer != 'undefined';

  if (typeof circular == 'undefined')
    circular = true;

  if (typeof depth == 'undefined')
    depth = Infinity;

  // recurse this function so we don't reset allParents and allChildren
  function _clone(parent, depth) {
    // cloning null always returns null
    if (parent === null)
      return null;

    if (depth === 0)
      return parent;

    var child;
    var proto;
    if (typeof parent != 'object') {
      return parent;
    }

    if (_instanceof(parent, nativeMap)) {
      child = new nativeMap();
    } else if (_instanceof(parent, nativeSet)) {
      child = new nativeSet();
    } else if (_instanceof(parent, nativePromise)) {
      child = new nativePromise(function (resolve, reject) {
        parent.then(function(value) {
          resolve(_clone(value, depth - 1));
        }, function(err) {
          reject(_clone(err, depth - 1));
        });
      });
    } else if (clone.__isArray(parent)) {
      child = [];
    } else if (clone.__isRegExp(parent)) {
      child = new RegExp(parent.source, __getRegExpFlags(parent));
      if (parent.lastIndex) child.lastIndex = parent.lastIndex;
    } else if (clone.__isDate(parent)) {
      child = new Date(parent.getTime());
    } else if (useBuffer && Buffer.isBuffer(parent)) {
      child = new Buffer(parent.length);
      parent.copy(child);
      return child;
    } else if (_instanceof(parent, Error)) {
      child = Object.create(parent);
    } else {
      if (typeof prototype == 'undefined') {
        proto = Object.getPrototypeOf(parent);
        child = Object.create(proto);
      }
      else {
        child = Object.create(prototype);
        proto = prototype;
      }
    }

    if (circular) {
      var index = allParents.indexOf(parent);

      if (index != -1) {
        return allChildren[index];
      }
      allParents.push(parent);
      allChildren.push(child);
    }

    if (_instanceof(parent, nativeMap)) {
      parent.forEach(function(value, key) {
        var keyChild = _clone(key, depth - 1);
        var valueChild = _clone(value, depth - 1);
        child.set(keyChild, valueChild);
      });
    }
    if (_instanceof(parent, nativeSet)) {
      parent.forEach(function(value) {
        var entryChild = _clone(value, depth - 1);
        child.add(entryChild);
      });
    }

    for (var i in parent) {
      var attrs;
      if (proto) {
        attrs = Object.getOwnPropertyDescriptor(proto, i);
      }

      if (attrs && attrs.set == null) {
        continue;
      }
      child[i] = _clone(parent[i], depth - 1);
    }

    if (Object.getOwnPropertySymbols) {
      var symbols = Object.getOwnPropertySymbols(parent);
      for (var i = 0; i < symbols.length; i++) {
        // Don't need to worry about cloning a symbol because it is a primitive,
        // like a number or string.
        var symbol = symbols[i];
        var descriptor = Object.getOwnPropertyDescriptor(parent, symbol);
        if (descriptor && !descriptor.enumerable && !includeNonEnumerable) {
          continue;
        }
        child[symbol] = _clone(parent[symbol], depth - 1);
        if (!descriptor.enumerable) {
          Object.defineProperty(child, symbol, {
            enumerable: false
          });
        }
      }
    }

    if (includeNonEnumerable) {
      var allPropertyNames = Object.getOwnPropertyNames(parent);
      for (var i = 0; i < allPropertyNames.length; i++) {
        var propertyName = allPropertyNames[i];
        var descriptor = Object.getOwnPropertyDescriptor(parent, propertyName);
        if (descriptor && descriptor.enumerable) {
          continue; ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.clone.__getRegExpFlags"></a>[function <span class="apidocSignatureSpan">clone.</span>__getRegExpFlags (re)](#apidoc.element.clone.__getRegExpFlags)
- description and source-code
```javascript
function __getRegExpFlags(re) {
  var flags = '';
  if (re.global) flags += 'g';
  if (re.ignoreCase) flags += 'i';
  if (re.multiline) flags += 'm';
  return flags;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.clone.__isArray"></a>[function <span class="apidocSignatureSpan">clone.</span>__isArray (o)](#apidoc.element.clone.__isArray)
- description and source-code
```javascript
function __isArray(o) {
  return typeof o === 'object' && __objToStr(o) === '[object Array]';
}
```
- example usage
```shell
...
  child = new nativePromise(function (resolve, reject) {
    parent.then(function(value) {
      resolve(_clone(value, depth - 1));
    }, function(err) {
      reject(_clone(err, depth - 1));
    });
  });
} else if (clone.__isArray(parent)) {
  child = [];
} else if (clone.__isRegExp(parent)) {
  child = new RegExp(parent.source, __getRegExpFlags(parent));
  if (parent.lastIndex) child.lastIndex = parent.lastIndex;
} else if (clone.__isDate(parent)) {
  child = new Date(parent.getTime());
} else if (useBuffer && Buffer.isBuffer(parent)) {
...
```

#### <a name="apidoc.element.clone.__isDate"></a>[function <span class="apidocSignatureSpan">clone.</span>__isDate (o)](#apidoc.element.clone.__isDate)
- description and source-code
```javascript
function __isDate(o) {
  return typeof o === 'object' && __objToStr(o) === '[object Date]';
}
```
- example usage
```shell
...
    });
  });
} else if (clone.__isArray(parent)) {
  child = [];
} else if (clone.__isRegExp(parent)) {
  child = new RegExp(parent.source, __getRegExpFlags(parent));
  if (parent.lastIndex) child.lastIndex = parent.lastIndex;
} else if (clone.__isDate(parent)) {
  child = new Date(parent.getTime());
} else if (useBuffer && Buffer.isBuffer(parent)) {
  child = new Buffer(parent.length);
  parent.copy(child);
  return child;
} else if (_instanceof(parent, Error)) {
  child = Object.create(parent);
...
```

#### <a name="apidoc.element.clone.__isRegExp"></a>[function <span class="apidocSignatureSpan">clone.</span>__isRegExp (o)](#apidoc.element.clone.__isRegExp)
- description and source-code
```javascript
function __isRegExp(o) {
  return typeof o === 'object' && __objToStr(o) === '[object RegExp]';
}
```
- example usage
```shell
...
      resolve(_clone(value, depth - 1));
    }, function(err) {
      reject(_clone(err, depth - 1));
    });
  });
} else if (clone.__isArray(parent)) {
  child = [];
} else if (clone.__isRegExp(parent)) {
  child = new RegExp(parent.source, __getRegExpFlags(parent));
  if (parent.lastIndex) child.lastIndex = parent.lastIndex;
} else if (clone.__isDate(parent)) {
  child = new Date(parent.getTime());
} else if (useBuffer && Buffer.isBuffer(parent)) {
  child = new Buffer(parent.length);
  parent.copy(child);
...
```

#### <a name="apidoc.element.clone.__objToStr"></a>[function <span class="apidocSignatureSpan">clone.</span>__objToStr (o)](#apidoc.element.clone.__objToStr)
- description and source-code
```javascript
function __objToStr(o) {
  return Object.prototype.toString.call(o);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.clone.clonePrototype"></a>[function <span class="apidocSignatureSpan">clone.</span>clonePrototype (parent)](#apidoc.element.clone.clonePrototype)
- description and source-code
```javascript
function clonePrototype(parent) {
  if (parent === null)
    return null;

  var c = function () {};
  c.prototype = parent;
  return new c();
}
```
- example usage
```shell
...
    defaults to infinity)
  * 'prototype' -- sets the prototype to be used when cloning an object.
    (optional, defaults to parent prototype).
  * 'includeNonEnumerable' -- set to 'true' if the non-enumerable properties
    should be cloned as well. Non-enumerable properties on the prototype chain
    will be ignored. (optional, defaults to 'false')

'clone.clonePrototype(obj)'

  * 'obj' -- the object that you want to clone

Does a prototype clone as
[described by Oran Looney](http://oranlooney.com/functional-javascript/).
...
```

#### <a name="apidoc.element.clone.toString"></a>[function <span class="apidocSignatureSpan">clone.</span>toString ()](#apidoc.element.clone.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
