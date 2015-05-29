# gulp-spellcheck [![Build Status](https://travis-ci.org/akoenig/gulp-spellcheck.svg?branch=master)](https://travis-ci.org/akoenig/gulp-spellcheck)

> A gulp plugin for spell-checking with [GNU Aspell](http://aspell.net/).

## Note

HTML spell checking with private dictionary specified at project root in file .aspell.en.pws.
File is not created by default, if user wants custom rules he should create one.

### Dictionary specification( .aspell.en.pws)
```javascript
personal_ws-1.1 en
Maxeler
AppGallery
```

## Usage

First of all you have to make sure that you have [GNU Aspell](http://aspell.net/) installed:
    
    $ # Debian-based
    $ sudo apt-get install aspell-en

    $ # CentOS
    $ sudo yum install aspell-en

If `aspell` is available install `gulp-spellcheck` as a development dependency in your project.

```shell
npm install --save-dev maxeler/gulp-spellcheck
```

Then, add it to your `gulpfile.js`:

```javascript
var frep = require('gulp-frep');
var spellcheck = require('gulp-spellcheck');

gulp.task('spellcheck', function () {

    var patterns = [
    {
        pattern: /({{([^}}]+)}})/ig,
        replacement: ''
    }];


    var a = gulp.src('./src/**/*.html')
        .pipe(frep(patterns))
        .pipe(spellcheck());
});
```

## API

### spellcheck (options)

#### options

##### language
Type: `String`
Default: undefined

ISO 639 or ISO 3166 language code (e.g. de). Please make sure that you have the respective aspell language pack installed (e.g. `sudo apt-get install aspell-de`).

##### replacement
Type: `String`
Default: '%s (suggestions: %s)'

The string that will replace the wrong word whereas the first placeholder is the wrong word and the second placeholder a list of suggestions.

## Changelog

### Version 0.2.0 (20150528)

- Ignore list: private dictionary in project root location (.aspell.en.pws)

### Version 0.1.2 (20140331)

- Added functionality for disabling 'pipe mode'.

### Version 0.1.1 (20140331)

- Fixed vinyl file access.

### Version 0.1.0 (20140331)

- Initial Release.

## Author

Copyright 2014, [André König](http://iam.andrekoenig.info) (andre.koenig@posteo.de)
