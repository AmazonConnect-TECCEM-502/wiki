# Recordings

Recordings is the area of the project where the application generates an mp4 file 
of a recording, which contains:

1. Agent Screen Video.
2. Agent and Customer Audio.
3. Agent Keystrokes.
4. Call Rating.
5. Transcript (subtitles) of the Video.
6. Video Category.

Which are processed and stored in the database with their specific categories,
with the relevant information for their classification, with the purpose of 
reproducing them in the same app, for their future for the internal agents of 
the organization in case of be necessary.

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

## FrontEnd

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


## BackEnd

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


#### Luxon

`Luxon` is a library for working with dates and times in JavaScript.


`npm install --save luxon`


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
event driven interface

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

##  Usage

## FrontEnd

## Nota:  debe ser mas pantallazo y de los fecth que hacen en el frontend (mas visual debes de ser tecnico)

### Brief explanation
### API ENDPOINT
### System validations
### System Errors
### Methods

## BackEnd

- **Brief explanation**:



- **Routes**:

| Routes       | What the Route Does                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------- |
| /getCalls    | Get the all the calls videos from the S3 stored bucket and send the data contents as a result.          |
| /uploadCall  | Send the new video to the S3 Bucket to store it for processing later                                    |
| /postVideoBD | Send the new video to the database in RDS with the timestamp when it was created.                       |


- **System validations**:

	* **/getCalls**:

| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| accessKeyId    	| Wrong accessKeyId                                                                                       |
| secretAccessKey  	| Wrong secretAccessKey                                                                                   |
| region      		| Wrong region, in the region does not have the S3 Bucket or the region does not exists                   |
| Bucket		| Wrong bucket, name, the bucket may be in other region or the bucket  does not exists                    |
| Key 			| Wrong filename, the file may be in other bucket or the file does not exists                             |


	* **/uploadCall**:

| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| accessKeyId    	| Wrong accessKeyId                                                                                       |
| secretAccessKey  	| Wrong secretAccessKey                                                                                   |
| region      		| Wrong region, in the region does not have the S3 Bucket or the region does not exists                   |
| Bucket		| Wrong bucket, name, the bucket may be in other region or the bucket  does not exists                    |
| Key 			| Wrong filename, the file may be in other bucket or the file does not exists                             |

	
	* **/postVideoBD**:

| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| File    		| The file was not created, or something happened when saving the database                                |
| Agent_id  		| Wrong/Empty Agent_id, or something happened when saving the database                                    |
| Date     		| Wrong timestamp, The date was not correctly captured when the file was created                          |



- **System Status/Errors**:
	
	* **/getCalls**:

	* **/uploadCall**:
	
	* **/postVideoBD**:

- **Methods**:

## Embedded

### Brief explanation
### Routes
### System validations
### System Errors
### Methods
### Permissions

# 


## Initialization

## Where to go from here

##
