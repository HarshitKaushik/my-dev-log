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
- Now you can initialize the physical space on your hard-disk to allocate databases. To do this, create a default postgres database on the command line in case it didn't happen automatically.
```bash
initdb '/usr/local/var/postgres'
```
- You could also implement a script to start the server each time you boot up the machine, but I like to have control over when to start and stop my database server to avoid complications.


## Python
- ASGI (Asynchronous Server Gateway Interface) is a spiritual successor to WSGI, intended to provide a standard interface between async-capable Python web servers, frameworks, and applications.
- Where WSGI provided a standard for synchronous Python apps, ASGI provides one for both asynchronous and synchronous apps, with a WSGI backwards-compatibility implementation and multiple servers and application frameworks.
- The ```__init__.py``` files are required to make Python treat the directories as containing packages; this is done to prevent directories with a common name, such as string, from unintentionally hiding valid modules that occur later on the module search path. In the simplest case, ```__init__.py``` can just be an empty file, but it can also execute initialization code for the package or set the ```__all__``` variable, described later.
- A PKL file is a file created by pickle, a Python module that enables objects to be serialized to files on disk and deserialized back into the program at runtime. It contains a byte stream that represents the objects.
- In python, the ```with``` keyword is used when working with unmanaged resources (like file streams). It is similar to the using statement in VB.NET and C#. It allows you to ensure that a resource is "cleaned up" when the code that uses it finishes running, even if exceptions are thrown. It provides 'syntactic sugar' for try/finally blocks.
- If you are running your module (the source file) as the main program the interpreter will assign the hard-coded string ```__main__``` to the ```__name__``` variable.
- In Python, the 'null' object is the singleton ```None```.
- Although popular languages like Java and PHP have in-built switch statement, you may be surprised to know that Python language doesn’t have one. As such, you may be tempted to use a series of if-else-if blocks, using an if condition for each case of your switch statement.
### Psycopg
- Psycopg is the most popular PostgreSQL database adapter for the Python programming language. Its main features are the complete implementation of the Python DB API 2.0 specification and the thread safety (several threads can share the same connection). It was **designed for heavily multi-threaded applications** that create and destroy lots of cursors and make a large number of concurrent “INSERT”s or “UPDATE”s.

### Django
- You’ve started the Django development server, a lightweight Web server written purely in Python. We’ve included this with Django so you can develop things rapidly, without having to deal with configuring a production server – such as Apache – until you’re ready for production.
- By default, the runserver command starts the development server on the internal IP at port 8000.
- The development server automatically reloads Python code for each request as needed. You don’t need to restart the server for code changes to take effect. However, some actions like adding files **don’t trigger** a restart, so you’ll have to restart the server in these cases.
- What’s the difference between a project and an app? An app is a Web application that does something – e.g., a Weblog system, a database of public records or a small poll app. A project is a collection of configuration and apps for a particular website. A project can contain multiple apps. An app can be in multiple projects.
- The include() function allows referencing other URLconfs. Whenever Django encounters include(), it chops off whatever part of the URL matched up to that point and sends the remaining string to the included URLconf for further processing.
- The idea behind include() is to make it easy to plug-and-play URLs.
- The path() function is passed four arguments, two required: route and view, and two optional: kwargs, and name. At this point, it’s worth reviewing what these arguments are for.
- ```route``` is a string that contains a URL pattern. When processing a request, Django starts at the first pattern in urlpatterns and makes its way down the list, comparing the requested URL against each pattern until it finds one that matches. **Patterns don’t search GET and POST parameters, or the domain name.**
- When Django finds a matching pattern, it calls the specified view function with an HttpRequest object as the first argument and any “captured” values from the route as keyword arguments.
- path() argument: kwargs - Arbitrary keyword arguments can be passed in a dictionary to the target view.
- path() argument: name - Naming your URL lets you refer to it unambiguously from elsewhere in Django, especially from within templates. **This powerful feature allows you to make global changes to the URL patterns of your project while only touching a single file.**
- By default, the configuration uses SQLite. If you’re new to databases, or you’re just interested in trying Django, this is the easiest choice. SQLite is included in Python, so you won’t need to install anything else to support your database. When starting your first real project, however, you may want to use a more scalable database like PostgreSQL, to avoid database-switching headaches down the road.
- By default, INSTALLED_APPS contains the following apps, all of which come with Django:
1. django.contrib.admin – The admin site. You’ll use it shortly.
2. django.contrib.auth – An authentication system.
3. django.contrib.contenttypes – A framework for content types.
4. django.contrib.sessions – A session framework.
5. django.contrib.messages – A messaging framework.
6. django.contrib.staticfiles – A framework for managing static files.
- For the minimalists - Like we said above, the default applications are included for the common case, but not everybody needs them. If you don’t need any or all of them, feel free to comment-out or delete the appropriate line(s) from INSTALLED_APPS before running migrate. The migrate command will only run migrations for apps in INSTALLED_APPS.
- Each model is represented by a class that subclasses ```django.db.models.Model```. Each model has a number of class variables, each of which represents a database field in the model.
- Django apps are “pluggable”: You can use an app in multiple projects, and you can distribute apps, because they don’t have to be tied to a given Django installation.
- When you run ```makemigrations```, you’re telling Django that you’ve made some changes to your models (in this case, you’ve made new ones) and that you’d like the changes to be stored as a migration.
- Serializers allow complex data such as querysets and model instances to be converted to native Python datatypes that can then be easily rendered into JSON, XML or other content types. Serializers also provide deserialization, allowing parsed data to be converted back into complex types, after first validating the incoming data.
- You need to call ```is_valid``` during deserialization process before writing data to DB. ```is_valid``` perform validation of input data and confirm that this data contain all required fields and all fields have correct types. If validation process succeded ```is_valid``` set ```validated_data``` dictionary which is used for creating or updating data in DB. Otherwise, serializer's property errors will contain information about errors in input data, and you can send this information as HTTP response in your view.
- If the model field has ```blank=True```, then ```required``` is set to ```False``` on the form field. Otherwise, ```required=True```.
- Sometimes even ```Manager.raw()``` isn’t quite enough: you might need to perform queries that don’t map cleanly to models, or directly execute UPDATE, INSERT, or DELETE queries.
- ```RunScript``` -  The runscript command lets you run an arbitrary set of python commands within the Django context. This file must implement a run() function. This is what gets called when you run the script. You can import any models or other parts of your django project to use in these scripts.
```bash
python manage.py runscript ${scriptName}
```
- **Note: You can put a script inside a scripts folder in any of your apps too.**

### Flask
- “Micro” does not mean that your whole web application has to fit into a single Python file (although it certainly can), **nor does it mean that Flask is lacking in functionality**. The “micro” in microframework means Flask aims to keep the core simple but extensible. Flask won’t make many decisions for you, such as what database to use. Those decisions that it does make, such as what templating engine to use, are easy to change. Everything else is up to you, so that Flask can be everything you need and nothing you don’t.
- Flask is a micro web framework written in Python. It is classified as a microframework because it does not require particular tools or libraries. It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions. However, Flask supports extensions that can add application features as if they were implemented in Flask itself. Extensions exist for object-relational mappers, form validation, upload handling, various open authentication technologies and several common framework related tools.

### Pandas
- ```pandas.DataFrame.shape``` - Return a tuple representing the dimensionality of the DataFrame.

### MLflow
- An MLflow Model is a standard format for packaging machine learning models that can be used in a variety of downstream tools—for example, real-time serving through a REST API or batch inference on Apache Spark. The format defines a convention that lets you save a model in different “flavors” that can be understood by different downstream tools.
- Flavors are the key concept that makes MLflow Models powerful: they are a convention that deployment tools can use to understand the model, which makes it possible to write tools that work with models from any ML library without having to integrate each tool with each library. MLflow defines several “standard” flavors that all of its built-in deployment tools support, such as a “Python function” flavor that describes how to run the model as a Python function. However, libraries can also define and use other flavors. For example, MLflow’s mlflow.sklearn library allows loading models back as a scikit-learn Pipeline object for use in code that is aware of scikit-learn, or as a generic Python function for use in tools that just need to apply the model (for example, the mlflow sagemaker tool for deploying models to Amazon SageMaker).