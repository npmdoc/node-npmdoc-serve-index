# npmdoc-serve-index

#### api documentation for  [serve-index (v1.8.0)](https://github.com/expressjs/serve-index)  [![npm package](https://img.shields.io/npm/v/npmdoc-serve-index.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-serve-index) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-serve-index.svg)](https://travis-ci.org/npmdoc/node-npmdoc-serve-index)

#### Serve directory listings

[![NPM](https://nodei.co/npm/serve-index.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/serve-index)

- [https://npmdoc.github.io/node-npmdoc-serve-index/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-serve-index/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-serve-index/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Douglas Christopher Wilson"
    },
    "bugs": {
        "url": "https://github.com/expressjs/serve-index/issues"
    },
    "dependencies": {
        "accepts": "~1.3.3",
        "batch": "0.5.3",
        "debug": "~2.2.0",
        "escape-html": "~1.0.3",
        "http-errors": "~1.5.0",
        "mime-types": "~2.1.11",
        "parseurl": "~1.3.1"
    },
    "description": "Serve directory listings",
    "devDependencies": {
        "after": "0.8.1",
        "istanbul": "0.4.3",
        "mocha": "2.5.3",
        "supertest": "1.1.0"
    },
    "directories": {},
    "dist": {
        "shasum": "7c5d96c13fb131101f93c1c5774f8516a1e78d3b",
        "tarball": "https://registry.npmjs.org/serve-index/-/serve-index-1.8.0.tgz"
    },
    "engines": {
        "node": ">= 0.8.0"
    },
    "files": [
        "public/",
        "LICENSE",
        "HISTORY.md",
        "index.js"
    ],
    "gitHead": "357452911dce2d17fd90aea7c1b5e69781b7f464",
    "homepage": "https://github.com/expressjs/serve-index",
    "license": "MIT",
    "maintainers": [
        {
            "name": "dougwilson"
        }
    ],
    "name": "serve-index",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/expressjs/serve-index.git"
    },
    "scripts": {
        "test": "mocha --reporter spec --bail --check-leaks test/",
        "test-ci": "istanbul cover node_modules/mocha/bin/_mocha --report lcovonly -- --reporter spec --check-leaks test/",
        "test-cov": "istanbul cover node_modules/mocha/bin/_mocha -- --reporter dot --check-leaks test/"
    },
    "version": "1.8.0"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
