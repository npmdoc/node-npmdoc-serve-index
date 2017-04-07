# api documentation for  [serve-index (v1.8.0)](https://github.com/expressjs/serve-index)  [![npm package](https://img.shields.io/npm/v/npmdoc-serve-index.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-serve-index) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-serve-index.svg)](https://travis-ci.org/npmdoc/node-npmdoc-serve-index)
#### Serve directory listings

[![NPM](https://nodei.co/npm/serve-index.png?downloads=true)](https://www.npmjs.com/package/serve-index)

[![apidoc](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-serve-index_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-serve-index/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-serve-index/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Douglas Christopher Wilson",
        "email": "doug@somethingdoug.com"
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
            "name": "dougwilson",
            "email": "doug@somethingdoug.com"
        }
    ],
    "name": "serve-index",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module serve-index](#apidoc.module.serve-index)
1.  [function <span class="apidocSignatureSpan">serve-index.</span>html (req, res, files, next, dir, showUp, icons, path, view, template, stylesheet)](#apidoc.element.serve-index.html)
1.  [function <span class="apidocSignatureSpan">serve-index.</span>json (req, res, files)](#apidoc.element.serve-index.json)
1.  [function <span class="apidocSignatureSpan">serve-index.</span>plain (req, res, files)](#apidoc.element.serve-index.plain)



# <a name="apidoc.module.serve-index"></a>[module serve-index](#apidoc.module.serve-index)

#### <a name="apidoc.element.serve-index.html"></a>[function <span class="apidocSignatureSpan">serve-index.</span>html (req, res, files, next, dir, showUp, icons, path, view, template, stylesheet)](#apidoc.element.serve-index.html)
- description and source-code
```javascript
function _html(req, res, files, next, dir, showUp, icons, path, view, template, stylesheet) {
  var render = typeof template !== 'function'
    ? createHtmlRender(template)
    : template

  if (showUp) {
    files.unshift('..');
  }

  // stat all files
  stat(path, files, function (err, stats) {
    if (err) return next(err);

    // combine the stats into the file list
    var fileList = files.map(function (file, i) {
      return { name: file, stat: stats[i] };
    });

    // sort file list
    fileList.sort(fileSort);

    // read stylesheet
    fs.readFile(stylesheet, 'utf8', function (err, style) {
      if (err) return next(err);

      // create locals for rendering
      var locals = {
        directory: dir,
        displayIcons: Boolean(icons),
        fileList: fileList,
        path: path,
        style: style,
        viewName: view
      };

      // render html
      render(locals, function (err, body) {
        if (err) return next(err);

        var buf = new Buffer(body, 'utf8');
        res.setHeader('Content-Type', 'text/html; charset=utf-8');
        res.setHeader('Content-Length', buf.length);
        res.end(buf);
      });
    });
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.serve-index.json"></a>[function <span class="apidocSignatureSpan">serve-index.</span>json (req, res, files)](#apidoc.element.serve-index.json)
- description and source-code
```javascript
function _json(req, res, files) {
  var body = JSON.stringify(files);
  var buf = new Buffer(body, 'utf8');

  res.setHeader('Content-Type', 'application/json; charset=utf-8');
  res.setHeader('Content-Length', buf.length);
  res.end(buf);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.serve-index.plain"></a>[function <span class="apidocSignatureSpan">serve-index.</span>plain (req, res, files)](#apidoc.element.serve-index.plain)
- description and source-code
```javascript
function _plain(req, res, files) {
  var body = files.join('\n') + '\n';
  var buf = new Buffer(body, 'utf8');

  res.setHeader('Content-Type', 'text/plain; charset=utf-8');
  res.setHeader('Content-Length', buf.length);
  res.end(buf);
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
