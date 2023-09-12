# Single Page Applications with Vue
01. What is the entrypoint of an application?

  > The entrypoing of an application is the file that is loaded first when the application is started.  In Vue, it is the Main.js.

02. What is the difference between a vue `component` and `page`?

  > The difference between a vue component and page is that a component is a reusuable piece of code that is used to add functionality to the Vue Page.  The Vue Page is a self-contained unit of code that can be used to create a web application.  The main differenceis that a vue Page is responsiblefor its own routing and state management, while a vue component is responsible for its own presentation.

03. What is ***Component-Based Architecture***?

  > Component based architechture is a software building framework that allows developers to build components that contain specific functionality. These components can be stored in a component library and dropped into an application without modification of other components.

04. What are the three tags that make up a Vue component?

  > The three tags that make up a Vue component are template, script, and style

05. What are ***lifecycle hooks***? What are lifecycle hooks used for?

  > Lifecyle hooks are functions that are called at specific points in the lifecycle of a Vue Component.  They are used to perform tasks such as initializing the component, updating the component, and destroying the component. The 7 lifstyle hooks are:
> created, mounted, updated, beforeDestroy, destroyed, activated, deactivated.

06. Which component in Vue does the vue-router use to mount pages onto?

  > The Vue-Router uses the <router-view></router-view> component to mount pages.

07. What is the difference between the `AppState` and the state object within a component?

  > The AppState is the global state of the application, while the state object withing a component is the local state of that component.  The AppState is shared by all the components in the application, while the state object within a component is only accessible to that component.

08. What is the responsibility of `Services` in our Vue projects?

  > The responsibility of Services in our Vue projects is to handle the business logic in our projects.  It is responsible for providing data and functionality to the components.

09. What are ***props*** and how are they used? Provide an example

  > Props are used to pass data from a parent component to the child component. Props is short for properties.

10. What is the Vue method used to create watchable objects such as `state` or `AppState`?

  > The vue method used to create watchable objects such as state of AppState is computed properties. 
