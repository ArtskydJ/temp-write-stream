create-temp-file
================

> A tiny node module that creates a temporary file, returns a write stream, a path, and cleanup functions

[![Build Status](https://travis-ci.org/ArtskydJ/create-temp-file.svg)](https://travis-ci.org/ArtskydJ/create-temp-file)

# example

```js
var createFile = require('create-temp-file')()

var ws = createFile()
process.stdin.pipe(ws)

process.on('exit', ws.cleanupSync)
```

# api

```js
var CreateTempFile = require('create-temp-file')
```

## `var createFile = CreateTempFile([pathGenerator])`

`pathGenerator` is a function that returns a path. Defaults to [`tempfile`](https://github.com/sindresorhus/tempfile).

## `var ws = createFile([opts])`

`opts` is an object that is passed into `pathGenerator`. By default, you can pass in an extension; e.g. `'.png'`.

`ws` is a [write stream](https://nodejs.org/api/fs.html#fs_class_fs_writestream) to the new temporary file with the following properties:

- `ws.path` is the absolute path to the temporary file. E.g. `'/tmp/b285e724-226c-11e5-9981-82bd40254040.png'`
- `ws.cleanup([cb])` deletes the temporary file. Like [`fs.unlink`](https://nodejs.org/api/fs.html#fs_fs_unlink_path_callback).
- `ws.cleanupSync` deletes the temporary file synchronously. Like [`fs.unlinkSync`](https://nodejs.org/api/fs.html#fs_fs_unlinksync_path).

If an error occurs in `ws.cleanup()` or `ws.cleanupSync()`, the error will be emitted.

# install

With [npm](https://nodejs.org/en/download/) do:

    npm install create-temp-file

# license

[VOL](http://veryopenlicense.com/)
