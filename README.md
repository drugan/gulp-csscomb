## Notes

This fork uses a [custom CSS formatter](https://github.com/drugan/csscombx),
which in its turn is a fork of the latest version of [CSScomb](https://github.com/csscomb/csscomb.js).
The difference is that both packages are specifically intended to comply
with the [Drupal CMS coding standards](https://www.drupal.org/docs/develop/standards/css/csscomb-settings-for-drupal-css-formatting-and-sort-tool). The default configuration might be found in the **node_modules/csscombx/config/drupal.json** file.
For overriding default settings just copy some of the **node_modules/csscombx/config/\*.json** files,
put it into your project's root and rename the file to **.csscombx.json** (see the leading dot).
Then edit the file according your needs. Note that any of a project child folders
may have its own **.csscombx.json** file with different settings.

# [gulp](http://gulpjs.com)-csscomb &nbsp; [![Build Status](http://img.shields.io/travis/drugan/gulp-csscombx/master.svg?style=flat)](http://travis-ci.org/drugan/gulp-csscombx) [![Dependency Status](https://david-dm.org/drugan/gulp-csscombx.svg?style=flat)](https://david-dm.org/drugan/gulp-csscombx) [![Tips](https://img.shields.io/gratipay/drugan.svg?style=flat)](https://gratipay.com/drugan)

[<img src="https://rawgit.com/drugan/gulp-csscombx/master/csscomb.jpg" width="80" height="80" align="right">](http://csscomb.com)

> Format CSS coding style with [CSScomb](http://csscomb.com).

*If you have any difficulties with the output of this plugin, please use the
[custom CSS formatter tracker](https://github.com/drugan/csscombx/issues).*

## Installation

```sh
npm install gulp-csscombx --save-dev
```

## Example 1

```js
var gulp = require('gulp');
var csscombx = require('gulp-csscombx');

gulp.task('styles', function() {
  return gulp.src('src/styles/main.css')
    .pipe(csscombx())
    .pipe(gulp.dest('./build/css'));
});
```

## Example 2

```js
var gulp = require('gulp');
var $ = require('gulp-load-plugins')();

gulp.task('styles', function() {
  return gulp.src('src/styles/bootstrap.less')
    .pipe($.less({strictMath: true}))
    .pipe($.autoprefixer([
      'Android 2.3',
      'Android >= 4',
      'Chrome >= 20',
      'Firefox >= 24', // Firefox 24 is the latest ESR
      'Explorer >= 8',
      'iOS >= 6',
      'Opera >= 12',
      'Safari >= 6']))
    .pipe($.csscombx())
    .pipe(gulp.dest('./build/css'));
});
```

If there is `.csscombx.json` file present in the same folder as the source file(s),
or in the project root folder, `gulp-csscombx` will read config settings from it
instead of default config.

You can also specify a pre-defined configuration. Ex.: `csscombx('zen')`

## License

The MIT License (MIT) © Konstantin Tarkus ([@koistya](https://twitter.com/koistya))
