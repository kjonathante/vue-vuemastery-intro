# Scaffolding Vue from scratch (without using Vue-CLI)

### source
https://www.freecodecamp.org/news/how-to-create-a-vue-js-app-using-single-file-components-without-the-cli-7e73e5b8244f/
```
npm install vue vue-loader vue-template-compiler webpack webpack-cli webpack-dev-server babel-loader @babel/core @babel/preset-env css-loader vue-style-loader html-webpack-plugin rimraf -D
```

### data binding
```html
<img v-bind:src="image" v-bind:alt="altText">
<img :src="image" :alt="altText" > // shorthand
```

There are Vue directives to conditionally render elements:
v-if
v-else-if
v-else
v-show