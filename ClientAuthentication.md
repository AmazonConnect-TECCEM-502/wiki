# Client Authentication

Client authentication is the area of the project where we leverage the functionality of Amazon Connect's Voice ID in order to authenticate an end client within our system.

In general, we use the phone number of the customer to store his/her voice information and the rest of his information that are relevant to the system like his/her name, email, and acquired products.

#

## Few Notes Before Start

This application was divided into various repositories in order to generate the 
functionalities of each area in a more orderly, clean and concise way, as well
as to have order in the code sections that will be presented on this wiki.

# 

## Getting Started

In order to use the Recordings sections available in the repositories, 
you must download and use the following libraries and configurations in 
order to correctly use the functionality of the area.

Note: For the following commands, you could use `yarn add`,or its equivalent if necessary.

## [FrontEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

- toast
- axios
- react


#### React

The `react` package contains only the functionality necessary to define
React components. It is typically used together with a React renderer 
like react-dom for the web, or react-native for the native environments.

`npm install react`


#### React-Media-Recorder

`React-media-recorder` is a fully typed react component with render prop, 
or a react hook, that can be used to:

• Record audio/video

• Record screen


`npm i react-media-recorder`


#### React-Icons

Include popular icons in your React projects easily with `react-icons`, 
which utilizes ES6 imports that allows you to include only the icons that your project is using.

`npm install react-icons --save`

#### Axios

Promise based HTTP client for the browser and node.js

`npm install axios`


## [BackEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

#### Express

The `Express` module provides a small, robust tooling for HTTP servers,
making it a great solution for single page applications, websites, 
hybrids, or public HTTP APIs.


`$ npm install express`


#### AWS-SDK

The preferred way to install the `AWS SDK` for Node.js  is to use the 
npm package manager for Node.js. Simply type the following into a terminal window:


`npm install aws-sdk`


Then, include the TypeScript definitions for node for use 
in TypeScript projects and to support tools that can read .d.ts files. 


`npm install --save-dev @types/node`


#### Sequelize

`Sequelize` is a promise-based Node.js ORM tool for Postgres, 
MySQL, MariaDB, SQLite, DB2 and Microsoft SQL Server. 
It features solid transaction support, relations, 
eager and lazy loading, read replication and more.


`npm install sequelize`


#### Dynamodb

`Dynamodb` is a DynamoDB data mapper for node.js.
This module simplify data modeling and mapping to DynamoDB types,
data validation, advanced chainable apis for query and scan operations and more.


`npm install dynamodb`


#### Joi

`Joi` is the most powerful schema description language and data validator for JavaScript.

`npm install joi`


## Embedded

#### Amazon Connect Streams

The Amazon Connect Streams API (Streams) gives you the power to integrate your existing web applications 
with Amazon Connect. Streams lets you embed the Contact Control Panel (CCP) and Customer Profiles app UI 
into your page. It also enables you to handle agent and contact state events directly through an object oriented
event driven interface.

`npm install amazon-connect-streams`


#### Express

The `Express` module provides a small, robust tooling for HTTP servers,
making it a great solution for single page applications, websites, 
hybrids, or public HTTP APIs.


`$ npm install express`


#### FS

The `node:fs` module enables interacting with the file system in a way modeled on standard POSIX functions.


`npm install fs`


#### HTTP

`Http` is a simple, zero-configuration command-line static HTTP server. It is powerful enough for 
production usage, but it's simple and hackable enough to be used for testing, local development
and learning.


`npm install http`


#### HTTPS

`Https` is the HTTP protocol over TLS/SSL. In Node.js this is implemented as a separate module.

`npm install https`


#### Path

The `node:path` module provides utilities for working with file and directory paths.


`npm install --save path`



#

## Documentation

## [FrontEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

**Brief explanation**:

In this section, the agent's dashboard will display an element corresponding with the functionality of the Tecmex client automatic recognition. For this, it is required for the Voice ID service to be running, as well as the BackEnd server.

**Components**:

In the FrontEnd section, you will find the description and visuals including the client data card display, a forms to register a new client, and a verification question.

* [**ClientCard.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientCard.js)

This component shows the client's data if this is authenticated, describing the client's name, email, phone and products

![Client Card Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ClientCard.png)

* [**ClientForms.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientForms.js)

This component displays the forms to register a new client, asking for the same attributes that the ClientCard.js component shows

![Client Forms Image 1](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ClientForm1.png)
![Client Forms Image 2](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ClientForm2.png)

* [**ClientInfo.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientInfo.js)

This component storages and displays any data of the client as a row for the ClientCard.js component

* [**ClientName.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientName.js)

This component storages and displays the complete name of the client as a row for the ClientCard.js component

* [**ClientProvider.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientProvider.js)

This component manages all of the client's info with UseStates, creating a context for this components to use

* [**ClientQuestion.js**](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/ClientCard/ClientQuestion.js)

This component displays the verification question in the case of a not authenticated result

![Client Question Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ClientQuestion.png)

## [BackEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

**Brief explanation**:

For this section, you will find the routes, processes and models that are necessary for the customer authentication using Voice ID.

**Components**:

**Controllers**:

The controllers that are used in the creation of routes, data insertions and objects are the following:

* VIDUserController.ts

This controller initializes the service routes that are used to propagate authentication results given to customers by VoiceID to our dynamoDB storage, to register client information in our RDS Client table and retrieve this same information from RDS.


**Models**:

The models that are used to generate new rows of information in the database are the following:

* **SQL**: client.ts

This model specifies the attributes and their types for this table, which will store information of the customers.

The data needed for this model are:
  1. client_id: A number to use as primery key of the table.
  2. first_name: A string representing the customer's first name.
  3. last_name: A string representing the customer's last name.
  4. email: A string representing the customer's email.
  5. phone: A string representing the customer's phone number.


	
* **NOSQL**: callStatus.ts

The NoSQL model specifies the partition key of the dynamoDB table and the attributes to store. This table will store the authentication result of all customers who call, so that our system can access several authentication results, one for each customer, when there are multiple ongoing calls.
	
The data for this model are:
  1. phoneNumber: A string representing the customer's phone number (partition key).
  2. authenticationType: A string representing the authentication that voiceID returns in the beginning of a call (authenticated, not authenticated, inconclusive, not enrolled, opted out, error).


**Routes**:

| Routes          | What the Route Does                                                                                     |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| /sendAuthRes    | Store the authentication result that voiceID returned for a given customer in our dyanmoDB table        |
| /getAuthRes     | Retrieve the authentication result that voiceID returned for a given customer from our dynamoDB table   |
| /getUserData    | Perform query to retrieve the customer information stored in our RDS database                           |
| /sendClientData | Perform query to insert a new tuple into our Client table in our RDS database                	        |
| /reset          | Restore the state of the authentication of the client (to be used at the contact close)                 |


**System validations**:

* **/sendAuthRes**:

| Body Field     		 | Validation                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| phoneNumber    	 | Must be a string.                                                                                       |
| authenticationType | Must be a string, one of the possible authentication results.                                           |


* **/getAuthRes**:

| Field     		 | Validation                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| phoneNumber    	 | Must be a string.                                                                                       |

* **/getUserData**:

| Field     		 | Validation                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| phoneNumber    	 | Must be a string, one that exists in the Client table.                                                  |


* **/sendClientData**:

| Body Field     		 | Validation                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| first_name    	 | Must be a string.                                                                                       |
| last_name    	     | Must be a string.                                                                                       |
| email    	         | Must be a string.                                                                                       |
| phone    	         | Must be a string.                                                                                       |

* **/reset**:

| Body Field         | Validation                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| phoneNumber    	 | Must be a string.                                                                                       |


**System Status/Errors**:
	
* **/sendAuthRes**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success               	        | Request to store authentication received   | 200           |
| Internal Server Error             | Fatal error			                     | 500           |

* **/getAuthRes**:

| Code                  	        | Message            			                 | HTTP Response |
| --------------------------------- | ---------------------------------------------- | ------------- |
| Success               	        | callsStatus[0].Items[0] (a json with the info) | 200           |
| Internal Server Error             | Fatal error			                         | 500           |

* **/getUserData**:

| Code                  	        | Message            			                 | HTTP Response |
| --------------------------------- | ---------------------------------------------- | ------------- |
| Success               	        | data (a json with the info)                    | 200           |
| Internal Server Error             | message: error.message                         | 500           |
| External Error                    | External error                                 | 501           |

* **/sendClientData**:

| Code                  	        | Message            			                 | HTTP Response |
| --------------------------------- | ---------------------------------------------- | ------------- |
| Success               	        | Client insert succesful                        | 200           |
| Internal Server Error             | Fatal error                                    | 500           |


## Embedded

**Brief explanation**:

This section contains the route, processes and Amazon Connect Stream connection 
to generate the process of receiving, accepting and terminating incoming calls by 
the client, as well as the creation of the https server through the credentials and the express app.


**Components**:

**Index**:

The index file that is used for the implementation of the call service is the following:

* **Index.js**:

This index file supports us in generating the route for the HTML service, 
as well as the app express service and credentials to run it by creating a server 
and initializing the call through the port intended for it.

**HTML**:

The HTML files that are used in the creation of call are the following:

* **Index.html**:

This html file initializes the call service, where the instance of the call
is determined as well as various options that support us in visual elements, 
region selection, hearing, among others that customize the call service and the
needs of the functionality. .


**Credentials **:

In this section,two credentials are needed to get HTTPS certification, 
and run the call service in a secure way.This credentials are the following:

* **Certificate Request Key**:

A CSR or Certificate Signing Request is a block of encrypted text that is normally
generated on the server where the SSL certificate will be used, although it can also 
be generated externally like our case.

The CSR contains information that will finally be included in the SSL certificate, 
such as your name or that of the company, the address, the country of residence or the 
common name (domain for which the SSL is generated), in addition to these data it will 
also include a public key that will be included in your certificate as well.


* **RSA Private Key**:

RSA key is a private key based on RSA algorithm. Private Key is used for 
authentication and a symmetric key exchange during establishment of an SSL/TLS session.

It is a part of the public key infrastructure that is generally 
used in case of SSL certificates.

PEM encoded RSA private key is a format that stores an RSA private key, for use
with cryptographic systems such as SSL.



**Routes**:

| Routes       | What the Route Does                                                                                                        |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- |
| /            | Add the call to init() as an onload so it will only run and initialize the streams api when is loaded from the Index.html  |



## AWS Services

**Amazon Connect Contact Flows and VoiceID**

For the functionality of authenticating the client with his voice, we had to configure the Amazon Connect instance so that voiceID was enabled.

The configuration began by creating a Voice Domain, then we included the Set Voice ID contact block followed by the Set Contact Attribute contact block and the Check Voice ID contact block, all these so that the caller could be authenticated with his voice.

![Domain](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/voiceIDDomain.png)

![Contact flow](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/flow.png)


We created users with the agent role in Amazon Connect and assigned them to a basic queue so that they could receive the calls. Adding the CCP: Voice ID permission in the security profiles was key in order to allow the agents to enroll callers and view the authentication result the callers received.

![Agent permissions](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/voiceIDPermission.png)


**Lamdbas**:

We used a main lambda function and it is invoked in the Contact Flow. It's purpose is to simply perform a post request to our server so that the authentication of the current customer and his/her phone number get stored in our dynamoDB table.

INVOKE FLOW

**Dynamo**
We create a simple table programatically using Typescript in order to store de authentication status of all the callers of the contact center. Initially, we thought that storing the authentication result in the server was enough but we realized that to allow for multiple callers at a time, we needed a database.

The table has the following format:



# 