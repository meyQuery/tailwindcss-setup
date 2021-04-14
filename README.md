# tailwindcss-setup
Learn how to get Tailwind CSS up and running in your project.

### Install Tailwind via npm
For most projects (and to take advantage of Tailwind's customization features), you'll want to install Tailwind and its peer-dependencies via npm.

```
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

### Add Tailwind as a PostCSS plugin
Add `tailwindcss` and `autoprefixer` to your PostCSS configuration. Most of the time this is a `postcss.config.js` file at the root of your project, but it could also be a `.postcssrc` file, or `postcss` key in your `package.json` file.

```
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

### Create your configuration file
‍‍‍```
npx tailwindcss init
```

This will create a minimal `tailwind.config.js` file at the root of your project:

```
// tailwind.config.js
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

### Include Tailwind in your CSS

```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

### Building your CSS
When building for production, be sure to configure the `purge` option to remove any unused classes for the smallest file size:

```
// tailwind.config.js
module.exports = {
  purge: ['public/*.html'],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

### Update package.json scripts
```
.
.
.
"scripts": {
  "watch:css": "postcss ./src/css/**/*.css -o ./public/css/style.css --watch",
  "build:css": "postcss ./src/css/style.css -o ./public/css/style.css",
  "production:css": "NODE_ENV=production postcss ./src/css/style.css -o ./public/css/style.css"
},
.
.
.
```