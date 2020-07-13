---
layout: post
title:      "React/Redux Project - Burgers"
date:       2020-07-13 15:50:22 +0000
permalink:  react_redux_project_-_burgers
---


For my final project at Flatiron School, I made a simple app to track favorite burgers from restaurants using Rails API as a backend and React JS/Redux for the frontend. For future projects I'd like to connect to an external API such as the Yelp Fusion API, and add a Google feature but as of now that's a bit of a stretch goal.

Although React/Redux improves efficiency and developer experience when making frontend Javascript projects, the most difficult part of learning them for me is how things flow in the app, and how everything connects to one another. One major problem I came across in learning web development is not only the terminology and logic, but visualizing where things go and what decisions to make. Visualizing the flow was important for Redux, in terms of understanding actions, store, dispatch, reducers, etc.

The [react documentation](https://redux.js.org/introduction/getting-started) states that Redux is a predictable state container for JS apps, and allows you to write apps that behave consistently, run in different environments and are easier to test. The main parts of Redux are the components, containers, actions and reducers which are separated into folders in the apps.

![Redux Flow Chart](https://res.cloudinary.com/practicaldev/image/fetch/s--VtRaY29J--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/fewc8ez6r2e2agah717y.png)

For React-Redux flow:

#### Components

Components are what the users see on the screen in the browser and what they can interact with. For example, this can be a nav bar or a button, like a regular React component. In Redux, components don't access or change state. State is stored globally in an object, in a single store and can only be changed through an action and dispatch function. Info is stored in an app within containers.

#### Containers

Container files are where you put the components in, and with `mapDispatchToProps` and `mapStatetoProps`, link the component's props to the action and dispatchers to change state. 

#### Actions

In the action files, we create functions that dispatch an action. In my app, since it was connected to a backend API, these held the fetch requests that got back or modified data in the API.

#### Dispatch

Dispatches are functions that are between actions and reducers, sending info over to the application. Dispatch always sends the info over tot he reducer.

#### Reducers

Reducers are functions that receive the data info from the actions as a type and payload, and then modifies the state based on that data given. The reducers don't change state, but creates a new state that is based off of the old state. Once state is changed, the container modifies the specific component with `mapStateToProps`. 

There is much more to cover with Redux, but I learned that it allows for a lot more control over how data is handled and gives a better file structure that's easier to follow and debug. There's still a lot for me to learn, but at a high-level I think I'm getting the hang of it more.
