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
