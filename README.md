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

### style binding
```html
<h1 :style="{color: color}"></h1>

data: {
  color: "red"
}
```
#### style bindings - objects
```html
<h1 :style="styleObject"></h1>

data: {
  styleObject: {
    color: "red",
    fontSize: "13px"
  }
}
```
#### style bindings - arrays
```html
<h1 :style="[styleObject, styleObject2]"></h1>

data: {
  styleObject: {
    color: "red",
    fontSize: "13px"
  },
  styleObject2: {
    margin: "5px",
    padding: "10px"
  }
}
```

### Class Bindings
```html
<div :class="{ active: activeClass }"></div>

data: {
  activeClass: true
}
```
#### class bindings - objects
```html
<div :class="classObject"></div> //results to:  <div class="active"></div>

data: {
  classObjects: {
    active: true;
    'text-danger': false
  }
}
```
#### class bindings - arrays
```html
<div :class="[activeClass, errorClass]"></div> //results to:  <div class="active text-danger"></div>

data: {
  activeClass: "active",
  errorClass: "text-danger"
}
```
#### class bindings - conditionals
```html
<div :class="[isActive ? activeClass : '']"></div> // results to <div class="active"></div>
data: {
  isActive: true,
  activeClass: "active"
}
```

### Computed Properties
Computed properties are cached, meaning the result is saved until its dependencies change. So when quantity changes, the cache will be cleared and the **next time you access the value of inStock , it will return a fresh result, and cache that result.

With that in mind, it’s more efficient to use a computed property rather than a method for an expensive operation that you don’t want to re-run every time you access it.

It is also important to remember that you should not be mutating your data model from within a computed property. You are merely computing values based on other values. Keep these functions pure.