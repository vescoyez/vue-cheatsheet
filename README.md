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

#### Events

Directives for events start with `v-on:` followed by the event and take the name of your mathod as value.

```html
<input type="text" v-on:input="yourMethod">
```



