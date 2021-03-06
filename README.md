[gulp](http://gulpjs.com)-typograf
==================================
[![NPM version](https://img.shields.io/npm/v/gulp-typograf.svg)](https://www.npmjs.com/package/gulp-typograf)
[![NPM downloads](https://img.shields.io/npm/dm/gulp-typograf.svg)](https://www.npmjs.com/package/gulp-typograf)
[![Build Status](https://img.shields.io/travis/typograf/gulp-typograf.svg)](https://travis-ci.org/typograf/gulp-typograf)
[![Dependency Status](https://img.shields.io/david/typograf/gulp-typograf.svg)](https://david-dm.org/typograf/gulp-typograf) [![devDependency Status](https://img.shields.io/david/dev/typograf/gulp-typograf.svg)](https://david-dm.org/typograf/gulp-typograf#info=devDependencies)


Prepare texts with [Typograf](https://github.com/typograf/typograf) using Gulp.

## Install

```
npm install gulp-typograf --save-dev
```

## Usage
```js
'use strict';

const typograf = require('gulp-typograf');

gulp.task('typograf', function() {
    gulp.src('./src/*.html')
        .pipe(typograf({ locale: ['ru', 'en-US'] }))
        .pipe(gulp.dest('./public/'));
});

```

## With additional options
```js
.pipe(typograf({
    locale: ['ru', 'en-US'],
    htmlEntity: { type: 'digit' }, // Type of HTML entities: 'digit' - &#160;, 'name' - &nbsp;, 'default' - UTF-8
    disableRule: ['ru/optalign/*'],
    enableRule: ['ru/money/ruble'],
    rules: [ // Own rules
        {
            name: 'common/other/typographicalEmoticon',
            handler: function(text, settings) {
                return text.replace(/:-\)/, ':—)');
        },
        {
            name: 'common/other/trimLeft'
            handler: function(text, settings) {
                return text.trimLeft();
            }
        }
    ]
}))
```

## Links
- [Typograf](https://github.com/typograf/typograf)
- [grunt-typograf](https://github.com/typograf/grunt-typograf)
