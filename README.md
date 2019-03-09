# my-dev-log
A log of my experiences as a software engineer from March 7, 2019

## Angular

- Root component - The first component that is rendered by Angular as the root of the component tree that makes up the application. It is also called the bootstrap component.
- Easy way to describe what a component is? A composable unit of the app.
- Decorators are proposed for a future version of JavaScript, but the Angular team really wanted to use them, and they have been included in TypeScript.
- Angular **does not scan** the folders for components. The components have to be declared explicitly as part of a module. Creating files is not enough.
- We can also define the template inline with a normal string or multi-line string.
- Components can be rendered by using the selector as an element (```<app></app>```), an attribute (```<div app>```) or as a class (```<div class="app"></div>```). Id selectors and pseudo-selectors are not supported.
- Data binding can be explained to someone as the communication between the Business Logic and the Template of the component. String interpolation, property binding and event binding are three types of one-way data binding because the data is flowing only in one direction. When we combine both the property binding and event binding, it is called two-way data binding. Two-way data binding is not used by React.
- String Interpolation ({{ expression }}) - Any expression that can be resolved back to a string can be used in string interpolation to output the data. Block expressions and multi-line expressions are not supported.
- Property binding - We can bind to all element properties in the DOM using property binding.
- Event binding - We can bind to all the events available with an HTML element using event binding.
- How do you know to which Properties or Events of HTML Elements you may bind? You can basically bind to all Properties and Events - a good idea is to console.log()  the element you're interested in to see which properties and events it offers.
- ```<ng-template>``` is an angular element for rendering HTML. It is never displayed directly. It can be displayed using structural directive, ViewContainerRef etc.
- 