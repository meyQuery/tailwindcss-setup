# tailwindcss-setup
Learn how to get Tailwind CSS up and running in your project.

### First Things First
```
npm init
```

### Initial project directory structure
📁 project
- 📁 public
  - 📁 css
  - index.html
- 📁 src
  - 📁 css
- package.json

### Install Tailwind via npm
For most projects (and to take advantage of Tailwind's customization features), you'll want to install Tailwind and its peer-dependencies via npm.

```
npm install -D tailwindcss@latest postcss-cli@latest autoprefixer@latest
```

### Create your configuration file and add Tailwind as a PostCSS plugin
```
npx tailwindcss init -p
```

This will create a `postcss.config.js` file and a minimal`tailwind.config.js` file at the root of your project:

```
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

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
@tailwind base;
@tailwind components;
@tailwind utilities;
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

Now you can use the scripts, for example: `npm run build:css`.