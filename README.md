# my-dev-log
A loosely-updated log of my experiences as a software engineer from April 01, 2020

# 01 April 2020
## Java
### Apache Solr
- solrj is the java client api to interact with solr. Also, solrj has changed the way you interact with solr based on solrj version.
- SolrJ is an API that makes it easy for Java applications to talk to Solr. SolrJ hides a lot of the details of connecting to Solr and allows your application to interact with Solr with simple high-level methods.
- The center of SolrJ is the org.apache.solr.client.solrj package, which contains just five main classes. Begin by creating a SolrClient, which represents the Solr instance you want to use. Then send SolrRequests or SolrQuerys and get back SolrResponses.
- SolrClient is abstract, so to connect to a remote Solr instance, you’ll actually create an instance of either HttpSolrClient, or CloudSolrClient. Both communicate with Solr via HTTP, the difference is that HttpSolrClient is configured using an explicit Solr URL, while CloudSolrClient is configured using the zkHost String for a SolrCloud cluster.
- SolrJ has an embedded jetty dependency for running solr in web server and jetty is a web server. Also, this jetty version may conflict with the jetty version bundled with dropwizard microservices framework.

# 02 April 2020
## Java 
### Apache Solr
- The %2C translates to a comma (,). I saw this while searching for a sentence with a comma in it and on the url, instead of showing a comma, it had %2C.

# 06 April 2020
