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

Directives for events start with `v-on:` followed by any DOM event and your method (without curly braces) as the value.

```html
<input type="text" v-on:input="yourMethod">
```

To access the data of your event in your method, use the object `target` on the event object.

```javascript
yourMethod: function(e) {
  this.name = e.target.value;
}
```

You can also pass arguments to your method.

```html
<input type="text" v-on:input="yourMethod(argument)">
```

If you need to use both custom argument and the event object, you the Vue variable `$event` for the event object.

```html
<input type="text" v-on:input="yourMethod($event, argument)">
```

```javascript
yourMethod: function(e, argument) {
  this.name = e.target.value;
  this.age = argument;
}
```

##### Modifiers

Vue provides some modifiers on events to quickly access some fonctionality. To use them add a `.` after the DOM event followed by the modifier.

```
<button v-on:click.stop="">Stop click propagation</button>
```

The modifiers:
- stop: e.stopPropagation
- prevent: e.preventDefault

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
