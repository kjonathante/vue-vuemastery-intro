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

### list rendering
```html
<li v-for="(detail,index) in details" :key="index">{{detail}}</li>
```

### Event Handling
```html
<button @click="addToCart">Add to cart</button>
<p @mouseover="updateProduct(variant.variantImage)">{{ variant.variantColor}}</p> // with arguments
```
The v-on directive is used to allow elements to listen for events
The shorthand for v-on is @