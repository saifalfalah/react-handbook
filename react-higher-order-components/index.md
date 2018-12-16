---
title: React Higher Order Components
date: 2018-12-12T07:00:00+02:00
description: "Find out what Higher Order Components are and how they are useful when programming a React application"
tags: react
---

You might be familiar with Higher Order Functions in JavaScript. Those are functions that accept functions as arguments, and/or return functions.

Two examples of those functions are `Array.map()` or `Array.filter()`.

In React, we extend this concept to components, and so we have a **Higher Order Component (HOC)** when the component accepts a component as input and returns a component as its output.

In general, higher order components allow you to create code that's composable and reusable, and also more encapsulated.

We can use a HOC to add methods or properties to the state of a component, or a Redux store for example.

You might want to use Higher Order Components when you want to enhance an existing component, operate on the state or props, or its rendered markup.

There is a convention of prepending a Higher Order Component with the `with` string (it's a convention, so it's not mandatory), so if you have a `Button` component, its HOC counterpart should be called `withButton`.

Let's create one.

The simplest example ever of a HOC is one that simply returns the component unaltered:

```js
const withButton = (Button) => () => <Button />
```

Let's make this a little bit more useful and add a property to that button, in addition to all the props it already came with, the color:

```js
const withButton = (Element) => (props) => <Button {...props} color="red" />
```

We use this HOC in a component JSX:

```js
const Button = () => {
  return (
    <button>test</button>
  )
}

const WrappedButton = withButton(Button)
```

and we can finally render the WrappedButton component in our app JSX:

```js
function App() {
  return (
    <div className="App">
      <h1>Hello</h1>
      <WrappedButton />
    </div>
  )
}
```

This is a very simple example but hopefully you can get the gist of HOCs before applying those concepts to more complex scenarios.