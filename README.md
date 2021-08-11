# How to run the QA app with the OAuth Java Server
This tool makes GET calls to the Onshape API involving Onshape documents, using the Java Client. It converts the operationId's of endpoints, into actual method calls in the java client. 

## Prerequisites
The following tools are required to run the API generator:
* Onshape Newton Build
* [Java 8 JDK](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven 3.5.2+](https://maven.apache.org/)
* Installed the "api-project" branch of the QA app
* Credentials to an OAuth application on the Demo-c Onshape appstore

First we need to set up RabbitMQ, so the Java Server and QA app will be able to establis a connection

## Running the RabbitMQ Server
Once you have installed the neston build,
1. cd into into the `newton` directory
1. Execute `source builedenv.bash`
1. Execute `startRabbitMQServer`

Now the RabbitMQ Server is running. You can double check by going [here](http://localhost:15672/). Next, we will start the Java server. 

## Running the oauth-java-server

Once you have installed the `oauth-java-server` application, 
1. Open the java app in an IDE. 
2. Run `AppQaServer.main()`

In the future, will be nice to run this from the command line. This is a Maven project, so will be possible to execute it this way.

## Running the QA app
Once you have installed the QA app,
1. cd into the `app-qa` directory

Now the 
