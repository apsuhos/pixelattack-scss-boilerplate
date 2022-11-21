# Pixelattack SCSS boilerplate

SCSS boilerplate

## Installation

NPM:

```
npm i @pixelattack/pixelattack-scss-boilerplate --save-dev
```

`main.scss` is the main, or manifest file. This file is responsible for @using all other files. This is the file that compiles into a corresponding CSS file.

You need to copy this file from the directory that your package manager installed it into, and move it to the root of your scss/ directory.

Next, you’ll need to update all of the @use in that file to point at the new locations of each partial.

If you use a task runner like gulp you can also add the included paths:

```
export const styles = () => {
  return gulp.src('main.scss')
    .pipe(sass({
        outputStyle: 'expanded',
        precision: 2,
        includePaths: [
          ../node_modules/@pixelattack/pixelattack-scss-boilerplate,
          ../another/one
        ],
    }).on('error', sass.logError))
    .pipe(gulp.dest('dist/'))
}
```

To load a module with configuration, write @use \<url\> with (\<variable\>: \<value\>, \<variable\>: \<value\>). The configured values will override the variables’ default values.

E.g.

```
// SETTINGS
@use './settings/config' with (
  $config: (
    env: dev
  )
);
@use './settings/colors' with (
  $color-primary-060: #000,
  $color-primary-080: #fff
);
@use './settings/core';
@use './settings/globals' with (
  $global-radius: 4px
);
```

You should probably use your own components too. The `buttons.scss` and `notifications.scss` can be used as guides.

```
// COMPONENTS
// @use './components/buttons';
// @use './components/notifications';
@use './assets/scss/components/card;
```

This library uses some custom breakpoints. Add this configuration in the `main.scss` file. This is going to be refactored in the future so that only the default breakpoints of `sass-mq` are included.

```
// TOOLS
@use './tools/mq' with (
  $mq-breakpoints: (
    mobile: 320px,
    l-mobile: 540px,
    tablet: 740px,
    l-tablet: 960px,
    desktop: 1200px,
    l-desktop: 1440px,
    wide: 1680px,
    l-wide: 1820px
  ),
  $mq-show-breakpoints: (
    mobile,
    l-mobile,
    tablet,
    l-tablet,
    desktop,
    l-desktop,
    wide,
    l-wide
  )
);
```
