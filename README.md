# my-dev-log
A loosely-updated log of my experiences as a software engineer from October 20, 2020.

## Java
- 
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

## Postgres
- JSONB is a powerful tool, but it comes at some cost because you need to adapt the way you query and handle the data. And it’s not rare to load the entire jsonb object into memory, transform it using your preferred programming language, and then saving it back to the database. But, you just created another problem: performance bottlenecks and resource waste.