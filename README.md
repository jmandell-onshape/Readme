# Running the QA app with the OAuth Java Server
This tool makes GET calls to the Onshape API involving Onshape documents, using [this]() Java Client. Uses the tags and operationId's of endpoints and converts these into Classes and methods of the java client. 

## Prerequisites
The following tools are required to run the API generator:
* Onshape Newton Build
* [Java 8 JDK](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven 3.5.2+](https://maven.apache.org/)
* [api-project branch of the QA app](https://github.com/onshape/app-qa/tree/api-project ) 
* Credentials to an OAuth application on the Demo-c Onshape appstore

First we need to set up RabbitMQ, so the Java Server and QA app will be able to establish a connection

## Running the RabbitMQ Server
Once you have installed the newton build,
1. cd into into the `newton` directory
1. Execute `source builedenv.bash`
1. Execute `startRabbitMQServer`

Now the RabbitMQ Server is running. You can double check by going [here](http://localhost:15672/). Next, we will start the Java server. 

## Running the oauth-java-server

Once you have installed the `oauth-java-server` application, 
1. Open the java app in an IDE. 
2. Run `AppQaServer.main()`

The app should now be able to listen for messages. 

## Running the QA app
Once you have installed the QA app,
1. cd into the `app-qa` directory
2. Execute `make start`
3. Obtain your OAuth app's client id and secret. Replace the corresponding sections in the curl command below with your client id and secret, then execute the command. 

```curl
curl -X POST 'https://localhost.dev.onshape.com:5443/appkeys' -d '{"clientId": "<client_id>", "clientSecret": "<client_secret>"}' -H 'Content-Type: application/json' 
```

4. Open the QA app in an Onshape Document
5. Type `/api/paths` in the QA app text field, click Send.
6. Now you are free to make your GET calls to the Onshape API, by typing in the call in the text field. You do not need to type the base url since all calls are made with demo-c. Here is what an example call may look like:
```
/api/assemblies/d/3494996efc14cbf22c0b348f/w/e0f178d13c5b98d94a824279/e/6177f782b5155c4dc9115237/featurespecs
```

Note: many of the endpoints may not work becuase of inconsistencies between the Java client and the API spec. Some calls that do work include `getFeatureSpecs` and `getCurrentMicroversion`. 


