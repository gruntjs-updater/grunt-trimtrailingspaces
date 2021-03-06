# grunt-trimtrailingspaces

> Trim trailing spaces from each line of the selected files

[![Build Status](https://img.shields.io/travis/paazmaya/grunt-trimtrailingspaces.svg?style=flat-square)](https://travis-ci.org/paazmaya/grunt-trimtrailingspaces)
[![Code Climate](https://img.shields.io/codeclimate/github/paazmaya/grunt-trimtrailingspaces.svg?style=flat-square)](https://codeclimate.com/github/paazmaya/grunt-trimtrailingspaces)
[![Dependency Status](https://img.shields.io/gemnasium/paazmaya/grunt-trimtrailingspaces.svg?style=flat-square)](https://gemnasium.com/paazmaya/grunt-trimtrailingspaces)
[![Built with Grunt](http://img.shields.io/badge/Grunt-0.4-blue.svg?style=flat-square)](http://gruntjs.com/)
[![Analytics](https://ga-beacon.appspot.com/UA-2643697-15/grunt-trimtrailingspaces/index?flat)](https://github.com/igrigorik/ga-beacon)


## Getting Started

This plugin requires [Grunt](http://gruntjs.com/) `~0.4` and [Node.js](https://nodejs.org/en/)
version to be minimum of `4.2.0`, which is the Long Term Support (LTS) version.

Add this to your project's `Gruntfile.js` configuration:

```js
grunt.loadNpmTasks('grunt-trimtrailingspaces');
```

Then add `grunt-trimtrailingspaces` to your "package.json" dependencies. This can be done with:

```js
npm install grunt-trimtrailingspaces --save-dev
```

Or by manually editing the `package.json` file by adding the following line inside `devDependencies` object:

```js
  "grunt-trimtrailingspaces": "^2.0.0"
```

Later on it would be possible to install the plugin with the command `npm install`

It can be updated with the command `npm update`, in case there is a newer version in the
[`npm` registry](https://www.npmjs.com/).

The name to use in your own task definitions is `trimtrailingspaces`.


## Documentation

Add an entry to your `Gruntfile.js`, within the `initConfig` object, which will define the
files of which will the trailing spaces to be removed.

By using the `src` property for selecting files to be processed, they are replaced by the ones processed.

By setting the `failIfTrimmed` option to true, the grunt task will fail after
trimming all files if any whitespace was removed.  This is very useful for
running trimtrailingspaces as a pre-commit task (in combination with
[grunt-githooks](https://github.com/rhumaric/grunt-githooks)), because it will
prevent the commit from going through which would not include the trimming
changes.

The examples below are using the [built-in custom filter property](http://gruntjs.com/configuring-tasks#custom-filter-function).

```js
  ...

  trimtrailingspaces: {
    main: {
      src: ['public_html/js/**/*.js'],
      options: {
        filter: 'isFile',
        encoding: 'utf8',
        failIfTrimmed: false
      }
    }
  }

  ...
```

It is possible to save the processed files to a different location by using the `files` property, as shown below.
The destination (key) should be a directory path in which the src files (array value) are stored.
No trailing slash needed.

Please note that this method will create a flat directory of the result.

```js
  ...

  trimtrailingspaces: {
    main: {
      files: {
        'public_html/js/trimmed': ['public_html/js/**/*.js']
      },
      filter: 'isFile',
      encoding: 'utf8'
    }
  }

  ...
```

For further information on how files are matched, please see the
documentation of the [`minimatch`](https://github.com/isaacs/minimatch) package,
as it is used underneath Grunt.

To run it:

```js
grunt trimtrailingspaces
```

## Contributing

[Please refer to a GitHub blog post on how to create somewhat perfect pull request.](https://github.com/blog/1943-how-to-write-the-perfect-pull-request "How to write the perfect pull request")

In lieu of a formal styleguide, take care to maintain the existing
coding style. Add unit tests for any new or changed functionality.
Lint and test your code using [Grunt](http://gruntjs.com/).

## Version history

* `v2.1.0` (2016-02-15)
  - Minimum Node.js version supported is `4.2.0` (LTS)
  - Update dependencies
* `v2.0.0` (2015-10-20)
  - Support Node.js 4+ only
  - Slightly better output messaging
* `v1.1.0` (2014-11-29)
  - Source copied to destination even when no trimming occurred
* `v1.0.0` (2014-11-10)
  - Touch file only if it needs to be trimmed
  - More efficient file handling with single regular expression check
* `v0.4.0` (2013-12-20)
  - Fail if trimmed option and use case added
* `v0.3.2` (2013-11-07)
  - Documentation for `filter` in examples
* `v0.3.1` (2013-08-28)
  - Dependency update to Node.js `0.10` from `0.8`
* `v0.3.0` (2013-07-31)
  - Added tests and made it possible to save processed files to other location
* `v0.2.1` (2013-07-25)
  - Removed `string.js` dependency and use `grunt.file` API
* `v0.2.0` (2013-07-11)
  - Support for Grunt `src` files array
* `v0.1.0` (2013-07-05)
  - Initial release

## License

Copyright (c) [Juga Paazmaya](http://www.paazmaya.fi) <paazmaya@yahoo.com>

Licensed under the [MIT license](LICENSE).

