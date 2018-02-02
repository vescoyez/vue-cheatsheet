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

## Syntax

### Variables

In the JS variables are defined in the `data` object

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

To access a variable inside a **method**, refer to `this`

```javascript
this.yourVariable = 'new value';
```

### Methods

In the JS methods are defined in the `methods` object

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

### Directives

#### Event Directive

Directives for events start with `v-on:` followed by the event and take the name of your mathod (without curly braces) as the value.

```html
<input type="text" v-on:input="yourMethod">
```

To access the data of your event in your method, use the object `target` from the event

```javascript
yourMethod: function(e) {
  this.name = e.target.value;
}
```

#### Bind Directive

For dinamic attributes, use the `v-bind:` followed by the attribute you want to bind and take the variable (without curly braces) as the value.

```html
<a v-bind:href="yourVariable">My link</a>
```

#### Once Directive

If you want the content of the element only render once and not changes if a variable get updated, you can use the directive `v-once`

```html
<h1 v-once>{{ yourVariable }}</h1>
```

#### HTML Directive

To output some HTML in a element, use the directive `v-html` with the your variable as the value.

```html
<!-- yourVariable = '<a href="http://google.com">Google</a>' -->
<p v-html="yourVariable"></p>
```
