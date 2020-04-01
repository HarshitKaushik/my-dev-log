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
- Option "spec" is deprecated: Use "skipTests" instead.
- There can be only one special method with the name "constructor" in a class. Having more than one occurrence of a constructor method in a class will throw a SyntaxError error. A constructor can use the super keyword to call the constructor of a parent class. If you do not specify a constructor method, a default constructor is used.
- We can use Angular Augury to visualize component tree, route tree and modules information.
- By default, all the properties of an Angular component are only accessible inside the component and not bindable from outside. That's why we use @Input().
- Angular enforces style encapsulation for a component by giving a unique attribute to each element in the component. By doing this, Angular emulates Shadow DOMs which aren't supported by all browsers.
- Permitting direct access to the DOM can make your application more vulnerable to XSS attacks. Carefully review any use of ElementRef in your code.
- Use this API as the last resort when direct access to DOM is needed. Use templating and data-binding provided by Angular instead. Alternatively you can take a look at Renderer2 which provides API that can safely be used even when direct access to native elements is not supported.
- Relying on direct DOM access creates tight coupling between your application and rendering layers which will make it impossible to separate the two and deploy your application into a web worker.
- We cannot have more than 1 structural directives on an element in the component.
- Angular is not limited to running in the browser. It can also run in a service worker from where it can serve the DOM.
- We can use @HostListener to listen to the events on the host element of the directive. A good way to make reactive functions.
- We can use @HostBinding to bind to any property of the host element of the directive. We can then dynamically change the value of this property.
- The value on the right only gets interpreted when using brackets. You can remove the brackets whenever you see quotes in quotes on the right: [anyStringProperty]="'hello'" can be changed to anyStringProperty = "hello"
- We can also have an input property in the directive with the same name as directive name and we can bind it from the host element. Angular knows that this is a property of a directive with the same name and binds the passed values to the property of the directive.
- the ```set attribute(propertyValue)``` should have the same name as the structural directive when building a structural directive. It will be called everytime the value of the expression of the directive changes.
- ViewContainerRef- Gives the reference to the view container of a structural directive.
- TemplateRef - Gives the reference to the template of a structural directive.
- We can abstract out the functionality into attribute/structural directives if needed.
- imports makes the exported declarations of other modules available in the current module
declarations are to make directives (including components and pipes) from the current module available to other directives in the current module. Selectors of directives, components or pipes are only matched against the HTML if they are declared or imported.
- providers are to make services and values known to DI. They are added to the root scope and they are injected to other services or directives that have them as dependency.
- A special case for providers are lazy loaded modules that get their own child injector. providers of a lazy loaded module are only provided to this lazy loaded module by default (not the whole application as it is with other modules).
- exports makes the components, directives, and pipes available in modules that add this module to imports.  exports can also be used to re-export modules such as CommonModule and FormsModule, which is often done in shared modules.
- Angular uses Hierarchial dependency injector. A service can be provided in multiple places.
- AppModule - Same instance of the service is available Application-wide.
- AppComponent - Same instance of the Service is available for all components (but not for other services).
- Any other component - Same instance of the service is available to the component and all its child components.
- EventEmitter - Use in directives and components to emit custom events synchronously or asynchronously, and register handlers for those events by subscribing to an instance.
```typescript
constructor(isAsync: boolean = false)
```
- Constructor of EventEmitter (above) - Creates an instance of this class that can deliver events synchronously or asynchronously.
- The slice() method returns a shallow copy of a portion of an array into a new array object selected from begin to end (end not included). The original array will not be modified.