# **Installation**

Cosycat is written in Clojure/Clojurescript - a nested Lisp dialect implemented on top of Java/Javascript. From the outside, Cosycat is just a Java application, which means that in order to run it you will need the Java Virtual Machine (JVM).

## **Java**

* Chances are high that you already have Java installed in your system. If not, you can either install the JRE (Java Runtime Environment) or the JDK (Java Development Kit).

* In Ubuntu, depending on which package you want you can do the following (select either jre or jdk).

'<sudo apt-get install default-jre/default-jdk>'

* For Mac you can use homebrew and do

<brew cask install java>

and you should be done.

## **External dependencies**

Before you can run the app executable you need to make sure the following external dependencies are installed and running on your system.

1. MongoDB

    Perhaps the most important dependency is the MongoDB database. The official online documentation has a nice section on how to           install MongoDB in different OSs. Once you have a working installation of MongoDB, make sure it is running before deploying Cosycat.     Most conveniently, you can run the MongoDB process in the background as a daemon (see Start mongod as a Daemon for instructions).       The mongod process will listen on specific TCP port, which defaults to 27017 but can be changed to any other value using the --port     optional argument.

2. Corpus Query Engines

    In order to provide Cosycat with search capabilities you to point it to a server running an instance of a corpus query engine.           Cosycat relies on HTTP to access corpus resources through a corpus query engine. Which means that your corpus query engine has to be     deployable as a server application and has to know how to provide results on response to HTTP GET requests. In some cases - such as     BlackLab -, a server implementation is already provided (see here). For the rest, it is normally easy to wrap a query engine in a       HTTP server provided the engine can be interacted with from a powerful enough programming language. For instance, an example of a       very simple server wrapper for the CQP engine can be found here (note, however, that it is still very alpha).

    As of Cosycat's current version, only the BlackLab server is supported. However adding support for other query engines is trivial       and we will happily offer help or, perhaps, implement it ourselves if you let us know about the details (by, for instance, opening       an issue to this repository). See further down for documentation on how to implement support for a new query engine.

## **Configuration**

In order to run Cosycat you need to point it to the corpora you want to make available and to the the database connection (in case you are running MongoDB on a non-default port). Additionally, there are other optional variables that can be set or customize. All configuration should go into a file in edn format such as the following (documentation for each variable is shown in place as comments).

<{:dynamic-resource-path "app-resources/"            ;where to store dynamic resources (logs, etc...)
 :avatar-path "img/avatars/"                        ;where to store generated avatars
 :tagset-paths ["/dir/with/tagsets" "another/path"] ;paths with tagset json files
 :database-url "mongodb://127.0.0.1:27017/cosycat"  ;mongodb URL (do not change unless you run mongod on a different port)
 :pass "pass"                                       ;admin password
 :port 3000                                         ;port to serve the website on
 :session-expires 900                               ;in minutes>
 :corpora [... see below ...]}

### **Corpus configuration**

There are several formats for specifying corpora.

1. Corpora full format: Specifies corpus, endpoint type and the corpus options needed by that type.

<[{:corpus "brown-tei"
  :type :blacklab-server
  :args {:server "my-server.com:8080"
  :web-service "blacklab-server-1.4-SNAPSHOT"}}]>

2. Corpora short format. Require all corpora available at a given URL (composed of http://server/webservice).
<[{:type :blacklab-server
  :server "my-server.com:8080"
  :web-service "blacklab-server-1.4-SNAPSHOT"}]>

3. Include only specific corpora from a given domain (TODO)
<[{:type :blacklab-server
  :server "my-server.com:8080"
  :web-service "blacklab-server-1.4-SNAPSHOT"
  :args {:corpora ["brown-tei"]}}]>

## **Running the app**

Once you have resolved the dependencies and created your configuration file you only need to grab the application from the release page.

Additionally you can choose to build the executable yourself. If you want to build the jar file yourself, you will need the handy Clojure project manager Leiningen (see link for further installation instructions). Once you have installed leiningen you need to fetch the sourcecode from this repository:

[Git Clone] (https://www.github.com/emanjavacas/cosycat.git)

Go to the project root directory:

<cd cosycat>

and call the uberjar action:

<lein uberjar>

This last command will download all dependencies and build the executable jar into cosycat/target/cosycat-VERSION-standalone.jar, which you can use to run the app.

In order to start the application, you only need the following command.

<java -Dconfig="path/to/config.edn" -jar cleebo-VERSION.jar start>

Afterwards you should be able to navigate through your browser to your server's URL plus the port specified in the config.edn file (or localhost:PORT if you are running the application locally) and see Cosycat's landing page.

### **Tagsets**

When doing annotations, it is common to predefine a set of annotation keys and values that have to be used for a given research question. For instance, if you want to annotate parts of speech (POS), you want to make sure the research team follows the same standard, such as the Penn Treebank tagset, or similar.

Furthermore, knowing the tagset allows the application to provide you with autocomplete functionalities - as shown in the picture below -, which can save your team a lot of typing time.

Cosycat allows you to input different tagsets using a simple tagset format. See the following JSON file for an example. You can specify as many JSON tagset files as you want. In order for Cosycat to use the tagsets, you only need to add directories with tagsets to your config file (see above).
