---
layout: post
title:      "State vs Props in React"
date:       2020-07-29 10:27:26 -0400
permalink:  state_vs_props_in_react
---

The soul of React and its power comes from components. According to the React documentation, components "let you split the UI into independent, reusable pieces, and think about each piece in isolation." In another sense, components are like the building blocks of a web application which translate data to HTML. For example, the building blocks (components) can be the navigation bar, buttons, text, or anything displaying or handling information and data. In React, these components are placed on a virtual DOM, and the component will re-render in order to match the data to the real DOM, which is the interface that the user sees. The way that the data is handled is mainly through the component's State and/or Props. 

### State

A component's state is a Javascript object that holds the information about the component and controls the component's behavior. When a component is first mounted, it is also set default values and an initial state which is created inside of that component. A component's state is mutable, meaning the attributes are changed or updated over time typically by user interactions with the component. When state is updated it will re-render, and so the children components' props can be updated with the new state as well, if specified.

For example, in creating a counter, we set the initial state object with a key of count and a value of 0. We can set initial state with or without a constructor, however, we won't have access to props if setting state without a constructor. 

```
constructor(props) {
  super(props);
  this.state = {
    count: 0,
  };
}
```

```
state = {
   count: 0
}
```

### Props

A component's props, short for properties, is also a Javascript object that holds information about the component. They are received from a parent component or from above and are immutable. Props are not handled or changed inside its component, and can change only when the state of its parent component is changed first. Props can be set an initial value with defaultProps, but this is done to avoid an error, such as in the case of a missing prop or if a prop was not passed down from the parent for some reason.

### State vs Props

State and props share similarities in that they are both plain Javascript objects that hold information about the component. However, state is mutable and should be used if the component's attributes need to be changed over time. State is local to that component, but can be passed down to children components as props.

If attributes of a component don't need to be changed, then those attributes should be passed as props. Props are immutable, and are passed down from a parent component and handled from above or the parent, whereas a component's state is handled inside of that component.

![This diagram shows how props come from a parent component, whereas state is handled internally.
](https://www.techdiagonal.com/wp-content/uploads/2019/09/react-props-blog-image-design-2.jpg)

#### Changing props and state

|  | props | state |
| -------- | -------- | -------- |
| Can get initial value from parent Component?     | Yes | Yes |
| Can be changed by parent Component?     | Yes    | No   |
| Can set default values inside Component?*     | Yes    | Yes   |
| Can change inside Component?     | No    | Yes   |
| Can set initial value for child Components?     | Yes    | Yes   |
| Can change in child Components?     | Yes    | No   

* Note that both props and state initial values received from parents override default values defined inside a Component.

This chart shows the difference in how props and state are changed in a component and helped understand even more of the differences.


### When to Use

One thing to note is deciding when to use either state or props in components, and this goes into when to make your component a Stateless or State Component. Stateless components only receive props, have no state and are usually only responsible for one thing such as displaying props. A stateful component can be passed props and can manage state, keeping track of the info itself. This handles the interactivity between the user or client side and the server side, changing or handling the data and responses from the client side. The more state components are used, the more complex an app becomes and so stateless components should be used more often while the logic stays in the State Components. 

Sources:

[https://github.com/uberVU/react-guide/blob/master/props-vs-state.md
](https://github.com/uberVU/react-guide/blob/master/props-vs-state.md)

[https://lucybain.com/blog/2016/react-state-vs-pros/](https://lucybain.com/blog/2016/react-state-vs-pros/)

[REACT JS TUTORIAL #4 - State vs Props & Application Data](https://www.youtube.com/watch?v=qh3dYM6Keuw)
