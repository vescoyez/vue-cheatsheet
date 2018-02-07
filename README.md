# Vue Cheatsheet

## Basic App

### HTML

```html
<div id="app">
  <p>{{ title }}</p>
</div>
```

### JS

```javascript
new Vue({
  el: '#app',
  data: {
    title: 'Hello World',
  }
});
```

## Variables

In the JS, variables are defined in the `data` object.

```javascript
new Vue({
  data: {
    yourVariable: 'Your Value'
  }
});
```

In the view, variables are written in `{{ }}`, like this:

```html
{{ yourVariable }}
```

To access a variable inside a **method**, refer to `this`.

```javascript
this.yourVariable = 'new value';
```

## Methods

In the JS methods are defined in the `methods` object.

```javascript
new Vue({
  methods: {
    yourMethod: function() {
      console.log('Define your method here');
    },
  }
});
```

In the view, methods are written in `{{ }}`, like this:

```html
{{ yourMethod() }}
```

## Computed properties

Computed rerender only when necessary. Avoiding using ressources when useless.

```javascript
new Vue({
  computed: {
    yourComputedProperty: function() {
      console.log('Define your method here');
    },
  }
});
```

In the view, methods are written in `{{ }}`, like this:

```html
{{ yourComputedProperty }}
```

## Watch

To watch a variable, use the `watch` object.

```javascript
new Vue({
  watch: {
    yourVariable: function(value) {
      console.log('Define your method here');
    },
  }
});
```

## Directives

### Event Directive

Directives for events start with `v-on:` or `@` followed by any DOM event and your method (without curly braces) as the value.

```html
<input type="text" v-on:input="yourMethod">
<!-- OR -->
<input type="text" @input="yourMethod">
```

To access the data of your event in your method, use the object `target` on the event object.

```javascript
yourMethod: function(e) {
  this.name = e.target.value;
}
```

You can also pass arguments to your method.

```html
<input type="text" @input="yourMethod(argument)">
```

If you need to use both custom argument and the event object, you the Vue variable `$event` for the event object.

```html
<input type="text" @input="yourMethod($event, argument)">
```

```javascript
yourMethod: function(e, argument) {
  this.name = e.target.value;
  this.age = argument;
}
```

#### Modifiers

Vue provides some modifiers on events to quickly access some fonctionality. To use them add a `.` after the DOM event followed by the modifier.

```
<button @click.stop>Stop click propagation</button>
```

[List of all event modifiers](https://vuejs.org/v2/guide/events.html#Event-Modifiers)

Vue also provides modifiers for key events allowing to access quickly a specific key on key events.

[List of all key modifiers](https://vuejs.org/v2/guide/events.html#Key-Modifiers)

### Bind Directive

For dinamic attributes, use the `v-bind:` or `:` followed by the attribute you want to bind and take the variable (without curly braces) as the value.

```html
<a v-bind:href="yourVariable">My link</a>
<!-- OR -->
<a :href="yourVariable">My link</a>
```

### Once Directive

If you want the content of the element only render once and not changes if a variable get updated, you can use the directive `v-once`.

```html
<h1 v-once>{{ yourVariable }}</h1>
```

### HTML Directive

To output some HTML in a element, use the directive `v-html` with the your variable as the value.

```html
<!-- yourVariable = '<a href="http://google.com">Google</a>' -->
<p v-html="yourVariable"></p>
```

### Two-way data binding directive

For two-way data binding, use the directive `v-model`.

```html
<input type="text" v-model="name">
<p>{{ name }}</p>
```

### Condition directive

To add condition to an element use `v-if`

```html
<div v-if="condition"></div>
```

You can add an `v-else` statement that will be the opposite of the previous `v-if` statement

```html
<div v-if="condition"></div>
<div v-else></div>
```

You can also use the `v-else-if` statement for more complex conditions

```html
<div v-if="condition"></div>
<div v-else-if="otherCondition"></div>
```

You can also use the HTML5 `template` element to use your condition statements. The adventage of `template` element is that it won't output any unecessary elements.

```html
<template v-if="condition">
  <h1>Title</h1>
  <p>Content</p>
</template>
```

### Show directive

If you want to hide an element and not remove it, use the `v-show` directive

```html
<div v-show="condition"></div>
```

### Loop directive

To output a list of elements, use `v-for`

```html
<!-- items = ['foo', 'bar', 'foobar'] -->
<ul>
  <li v-for="item in items">{{ item }}</li>
</ul>
```

For the index, refer it as a second element between parenthesis


```html
<ul>
  <li v-for="(item, index) in items">{{ index }} {{ item }}</li>
</ul>
```

As the `v-if` directive, you can also use the `v-for` directive on `template` element.

You can also loop over an object with `v-for`. The first argument will be the `value`, the second the `key` and the third one the `index`.

```html
<!-- person = {firstname: 'foo',lastname: 'bar',nationality: 'foobar'} -->
<ul>
  <li v-for="(value, key, index) in person">{{ key }}: {{ value }}</li>
</ul>
```

To loop n times, use:

```html
<ul>
  <li v-for="n in 10">{{ n }}</li>
</ul>
```

## Style

To style, use the *bind directive* `:class` or `:style`

It's possible to attached a simple string as a class

```html
<div :class="'red'"></div>
<!-- Will add red class -->
```

Or an object

```html
<div :class="{red: boolean}"></div>
<!-- Will add red class if boolean is true -->
```

Or any combination into an array


```html
<div :class="[myVariable, {red: boolean}]"></div>
```

## Ref

You can access any DOM element adding a `ref` attribute to the element

```html
<div ref="yourElement"></div>
```

Then you can access it in or out the Vue instance

```javascript
this.$refs.yourElement
```

## Lifecycle events

```javascript
new Vue({
  beforeCreate: function() {
  },
  created: function() {
  },
  beforeMount: function() {
  },
  mounted: function() {
  },
  beforeUpdate: function() {
  },
  updated: function() {
  },
  beforeDestroy: function() {
  },
  destroyed: function() {
  },
});
```

