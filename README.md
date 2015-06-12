create-temp-file
================

[![Build Status](https://travis-ci.org/ArtskydJ/create-temp-file.svg)](https://travis-ci.org/ArtskydJ/create-temp-file)
[![Dependency Status](https://david-dm.org/artskydj/create-temp-file.svg)](https://david-dm.org/artskydj/create-temp-file)
[![devDependency Status](https://david-dm.org/artskydj/create-temp-file/dev-status.svg)](https://david-dm.org/artskydj/create-temp-file#info=devDependencies)

Creates a temporary file, returns a write stream, a path, and cleanup functions

# example

```js
var createTempFile = require('create-temp-file')

var tempFile = createTempFile()
process.stdin
	.pipe(tempFile)
	.on('finish', function () {
		tempFile.cleanup()
	})
```

# api

```js
var createTempFile = require('create-temp-file')
```

### `var ws = createTempFile()`

Returns a [write stream](https://nodejs.org/api/fs.html#fs_class_fs_writestream) to the new temporary file with the following properties:
- `path` is the absolute path to the temporary file.
- `cleanup([cb])` is a function that will delete the temporary file. Like [`fs.unlink`](https://nodejs.org/api/fs.html#fs_fs_unlink_path_callback). If `cb` is not provided, errors will be swallowed.
- `cleanupSync()` is a function that deletes the temporary file synchronously. Like [`fs.unlinkSync(path)`](https://nodejs.org/api/fs.html#fs_fs_unlinksync_path).

# install

With [npm](https://npmjs.com/) do:

```
npm install create-temp-file
```

# license

[VOL](http://veryopenlicense.com/)
