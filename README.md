# my-dev-log
A loosely-updated log of my experiences as a software engineer.

## Java
### SAX Parsing
- SAX (Simple API for XML) is an event-driven online algorithm for parsing XML documents, with an API developed by the XML-DEV mailing list.
- SAX provides a mechanism for reading data from an XML document that is an alternative to that provided by the Document Object Model (DOM). Where the DOM operates on the document as a whole — building the full abstract syntax tree of an XML document for convenience of the user. SAX parsers operate on each piece of the XML document sequentially, issuing parsing events while making a single pass[clarification needed] through the input stream.
- A SAX parser only needs to report each parsing event as it happens, and normally discards almost all of that information once reported (it does, however, keep some things, for example a list of all elements that have not been closed yet, in order to catch later errors such as end-tags in the wrong order). Thus, the minimum memory required for a SAX parser is proportional to the maximum depth of the XML file (i.e., of the XML tree) and the maximum data involved in a single XML event (such as the name and attributes of a single start-tag, or the content of a processing instruction, etc.). This much memory is usually considered negligible.
- Xerces is the most widely used XML parser in the Java ecosystem. Almost every library or framework written in Java uses Xerces in some capacity (transitively, if not directly).
### Apache Solr
- solrj is the java client api to interact with solr. Also, solrj has changed the way you interact with solr based on solrj version.
- SolrJ is an API that makes it easy for Java applications to talk to Solr. SolrJ hides a lot of the details of connecting to Solr and allows your application to interact with Solr with simple high-level methods.
- The center of SolrJ is the org.apache.solr.client.solrj package, which contains just five main classes. Begin by creating a SolrClient, which represents the Solr instance you want to use. Then send SolrRequests or SolrQuerys and get back SolrResponses.
- SolrClient is abstract, so to connect to a remote Solr instance, you’ll actually create an instance of either HttpSolrClient, or CloudSolrClient. Both communicate with Solr via HTTP, the difference is that HttpSolrClient is configured using an explicit Solr URL, while CloudSolrClient is configured using the zkHost String for a SolrCloud cluster.
- SolrJ has an embedded jetty dependency for running solr in web server and jetty is a web server. Also, this jetty version may conflict with the jetty version bundled with dropwizard microservices framework.
- The %2C translates to a comma (,). I saw this while searching for a sentence with a comma in it and on the url, instead of showing a comma, it had %2C.

## Javascript
### Angular
- Yes, that is most likely why the author uses take(1) operator. It's job is to pass one value to an observable and then unsubscribe from the source. But depending on the service it may not be required. 
- For example in Angular the HttpClient service completes the stream by itself after sending the final HttpResponse event value so you don't need to neither use take nor unsubscribe explicitly.
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

## Postgres
- JSONB is a powerful tool, but it comes at some cost because you need to adapt the way you query and handle the data. And it’s not rare to load the entire jsonb object into memory, transform it using your preferred programming language, and then saving it back to the database. But, you just created another problem: performance bottlenecks and resource waste.
- Dumps can be output in script or archive file formats. Script dumps are plain-text files containing the SQL commands required to reconstruct the database to the state it was in at the time it was saved. To restore from such a script, feed it to psql(1). Script files can be used to reconstruct the database even on other machines and other architectures; with some modifications even on other SQL database products. The alternative archive file formats must be used with pg_restore(1) to rebuild the database. They allow pg_restore to be selective about what is restored, or even to reorder the items prior to being restored. The archive file formats are designed to be portable across architectures.

## Python
- ASGI (Asynchronous Server Gateway Interface) is a spiritual successor to WSGI, intended to provide a standard interface between async-capable Python web servers, frameworks, and applications.
- Where WSGI provided a standard for synchronous Python apps, ASGI provides one for both asynchronous and synchronous apps, with a WSGI backwards-compatibility implementation and multiple servers and application frameworks.
- The ```__init__.py``` files are required to make Python treat the directories as containing packages; this is done to prevent directories with a common name, such as string, from unintentionally hiding valid modules that occur later on the module search path. In the simplest case, __init__.py can just be an empty file, but it can also execute initialization code for the package or set the __all__ variable, described later.

### Django
- You’ve started the Django development server, a lightweight Web server written purely in Python. We’ve included this with Django so you can develop things rapidly, without having to deal with configuring a production server – such as Apache – until you’re ready for production.
- By default, the runserver command starts the development server on the internal IP at port 8000.
- The development server automatically reloads Python code for each request as needed. You don’t need to restart the server for code changes to take effect. However, some actions like adding files **don’t trigger** a restart, so you’ll have to restart the server in these cases.
- What’s the difference between a project and an app? An app is a Web application that does something – e.g., a Weblog system, a database of public records or a small poll app. A project is a collection of configuration and apps for a particular website. A project can contain multiple apps. An app can be in multiple projects.
- The include() function allows referencing other URLconfs. Whenever Django encounters include(), it chops off whatever part of the URL matched up to that point and sends the remaining string to the included URLconf for further processing.