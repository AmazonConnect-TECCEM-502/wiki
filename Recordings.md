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

## [FrontEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

#### React

The `react` package contains only the functionality necessary to define
React components. It is typically used together with a React renderer 
like react-dom for the web, or react-native for the native environments.

`npm install react`


#### React-Media-Recorder

`React-media-recorder` is a fully typed react component with render prop, 
or a react hook, that can be used to:

* Record audio/video

* Record screen


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


## [Embedded](https://github.com/AmazonConnect-TECCEM-502/AmazonConnect-Embedded)

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

# Documentation

## [FrontEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

**Brief explanation**:

In this section, the visualization of the project on the web page is created,
call initialization with controls and buttons needed to start, end, stop and other methods that are neccesary for the call, 
while services from AWS are consumed as well as the routes that generate
the necessary services to comply with the functionalities of the area previously seen.

**Components**:

The components that are used in the creation of the visual elements that are present in the web app, 
fetch and extraction of the video url for its processing and the capture of keystrokes within the application.
This are the following:


* **Recodings.js**:  [ **Recodings.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/Recordings/Recording.js)

This component allows us to record the screen, audio of the agent as well as the audio of the client, 
in order to produce an mp4 format with the information collected and upload it to an AWS s3 bucket and 
the database.

**Idle**

![Recording Idle Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/RecodingIdle.jpeg)

**Running**

![Recording Running Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/RecordingRecordingScreen.PNG)



* **KeystrokeText.js**:

This component that creates the visual elements for the keystrokes section in the web app

**Keystrokes Sample**

![Keystrokes Sample Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/Keystrokes.jpg)


**Keystrokes Running**

![Keystrokes Running Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/FullKeystrokes.jpeg)

* **KeystrokeRecording.js**:

The component supports us in detecting the keys that are used when the agent starts 
typing within the web application




## [BackEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

**Brief explanation**:

For this section, you will find the routes, processes and models that are necessary for the processing, 
handling and storage of the videos; which are used as services in the Frontend sections and in AWS services
in order to carry out the functionalities of the previously seen.

**Components**:

**Controllers**:

the controllers that are used in the creation of routes, data insertions and objects are the following:

* CallController.ts

This controller initializes the service routes that are used to find and post videos to the S3 bucket;
As well as the creation and updating of videos with the duration, original URL, URL with transcription,
qualification, among other relevant data of the video.


**Models**:

The models that are used to generate new rows of information in the database are the following:

* **SQL**: Call.ts

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Duration: Duration of the call video.

	2. Video_url: Link from the S3 object that has the video stored.

	3. Transcription_url: Link from the S3 object that has the video with thesubtitle stored.

	4. Rating:  Number of the rating of the video.

	5. Processed: Timestamp of the video when is created.


	
* **NOSQL**: CallStatus.ts

The NoSQL model supports us in formatting the storage information relevant to the 
state of the call and sending it to AWS DynamoDB to create the necessary table for this model.
	

**Routes**:

| Routes       | What the Route Does                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------- |
| /getCalls    | Get the all the calls videos from the S3 stored bucket and send the data contents as a result.          |
| /uploadCall  | Send the new video to the S3 Bucket to store it for processing later                                    |
| /postVideoBD | Send the new video to the database in RDS with the timestamp when it was created.                       |
| /updateCall  | Send the new video to the database in RDS with the timestamp when it was created.                       |


**System validations**:

* **/getCalls**:

| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| accessKeyId    	| Must be a valid AWS accessKeyId token                                                                   |
| secretAccessKey  	| Must be a valid AWS secretAccessKey token                                                               |
| region      		| Wrong region, the region does not have the S3 Bucket or the region does not exists                      |
| Bucket		| Wrong bucket, name, the bucket may be in other region or the bucket  does not exists                    |
| Key 			| Wrong filename, the file may be in other bucket or the file does not exists                             |



* **/uploadCall**:


| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| accessKeyId    	| Must be a valid AWS  accessKeyId token                                                                  |
| secretAccessKey  	| Must be a valid AWS  secretAccessKey token                                                              |
| region      		| Wrong region, in the region does not have the S3 Bucket or the region does not exists                   |
| Bucket		| Wrong bucket, name, the bucket may be in other region or the bucket  does not exists                    |
| Key 			| Wrong filename, the file may be in other bucket or the file does not exists                             |


	
* **/postVideoBD**:


| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| File    		| The file was not created, or something happened when saving the database                                |
| Agent_id  		| Wrong/Empty Agent_id, or something happened when saving the database                                    |



* **/updateCall**:


| Field     		| Validation                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------- |
| URL    		| The URL from the file was not created, or something happened when update to the database                |
| Date     		| Wrong timestamp, The date was not correctly captured when the file was created                          |



**System Status/Errors**:
	
* **/getCalls**:

| Code                  	    | Message            			 | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success               	    | data.Contents (List of S3 objects)         | 200           |
| Error to find the list of objects | error: err.message 			 | 500           |
| Failed  			    | error: err.message 		     	 | 500           |


* **/uploadCall**:

| Code                  	    | Message            			 | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success               	    | message: data         			 | 201           |
| Error PutObject on S3 bucket      | error: err.message 			 | 500           |
| Failed  			    | error: err.message 		     	 | 500           |
	
* **/postVideoBD**:


| Code                  	    | Message            			 | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success               	    |  message: "Se subio a la BD"               | 201           |
| Failed   			    |  error: err.message 		     	 | 500           |


* **/updateCall**:

| Code                  	    | Message            			 | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success               	    |                                            | 200           |
| NotFound			    |  		     	                         | 404           |


## [Embedded](https://github.com/AmazonConnect-TECCEM-502/AmazonConnect-Embedded)

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


* **Credentials**:

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

**Brief explanation**:

On the other hand, in order to be able to store, edit and use the videos with all 
the previously seen functionalities, some services from AWS Connect were needed to 
be able to generate the transcript, rating, object storage formats that will be the 
previous data relevant to the video. plus the same recording of the call, among other 
services necessary for the functionality of the area.

**Components**:

The components that are used in the creation of the transcript rating of the video
and the storage of the original recordings and data already mentioned are the following:

**Buckets**:

* gpo502-desarrollo-software-react-bucket: Main bucket where the recordings are saved as objects for editing and creation of the transcript and rating.
* post-process-subtitles: Bucket where subtitles of the recordings are stored.
* post-process-text: Bucket where text of the recordings are stored.
* post-process-videos: Second main bucket where the process recordings with the transcription are saved as object for use it in the application.
* ratings-comprehend: Bucket where rating of the recordings are stored in a txt file.


**Lambdas**:

* subtitles-generator: Lambda where the recordings is process to get the transcript of the subtitles and then stored into a S3 bucket. Add a trigger, which will be s3. So, any object that is uploaded into our input folder in the s3 bucket will trigger the Lambda function
* subtitles-video-merge: Lambda where the subtitles and the original video are merge to get the process video and then stored into a S3 bucket.
* subtitles-types-converter: Lambda that activates with the trigger when the uploading of th srt file is finish  to the corresponding bucket and extracts it and using regular expressions and string handling converts it from srt to txt and saves it to another bucket. 
* sentimental-lamdba: Lamdba that process the recording with the transcript and the text ofthe subtitles to get the rating of the video and the stored into a S3 bucket.
* getPresignedS3URL: Lamdba tha generates presigned url of the original video when recordings is ended in the web app.





# 