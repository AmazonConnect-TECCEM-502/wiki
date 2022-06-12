# Sales

Sales is the area of the project where the application shows the recommended products to be sold, which contains:

1. Agent Product screen.
2. Agent Product Categories screen.
3. Agent Product List screen.
4. Agent confirmation of new customer product acquisition.
5. Administrator Product creation screen.
6. Administrator Product insertion to database.

Which are shown to the Agent for having a reference during call for the selling of new products to the agent,
which products can be created if necessary when there are new stock and/or some integration of a product

#

## Few Notes Before Start

This application was divided into various repositories in order to generate the 
functionalities of each area in a more orderly, clean and concise way, as well
as to have order in the code sections that will be presented on this wiki.

# 

## Getting Started

In order to use the Sales sections available in the repositories, 
you must download and use the following libraries and configurations in 
order to correctly use the functionality of the area.

Note: For the following commands, you could use `yarn add`,or its equivalent if necessary.

## FrontEnd

#### React

The `react` package contains only the functionality necessary to define
React components. It is typically used together with a React renderer 
like react-dom for the web, or react-native for the native environments.

`npm install react`


#### React-Icons

Include popular icons in your React projects easily with `react-icons`, 
which utilizes ES6 imports that allows you to include only the icons that your project is using.

`npm install react-icons --save`


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


#### Sequelize

`Sequelize` is a promise-based Node.js ORM tool for Postgres, 
MySQL, MariaDB, SQLite, DB2 and Microsoft SQL Server. 
It features solid transaction support, relations, 
eager and lazy loading, read replication and more.


`npm install sequelize`


#### Joi

`Joi` is the most powerful schema description language and data validator for JavaScript.

`npm install joi`

#

# Documentation

## [ FrontEnd ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

## Nota:  debe ser mas pantallazo y de los fecth que hacen en el frontend (mas visual debes de ser tecnico)

**Brief explanation**:

In this section, the visualization of the project on the web page is created,
call initialization with controls and buttons needed to start, end, stop and other methods that are neccesary for the call, 
while services from AWS are consumed as well as the routes that generate
the necessary services to comply with the functionalities of the area previously seen.

**Components**:

The components are used in the creation of the visual elements of the sales card and extraction of the products information. 
These components are: 


* **ProductCard.js**:
 
* **ProductImage.js**:

* **ProductList.js**:

* **ProductsCategoryList.js**:

* **SalesMasterCard.js**:

* **ConfirmCard.js**:

This component allows the user to confirm if the agent really wants to add the product to the actual client.

* **NewProduct.js**:

**API ENDPOINT**:

**System validations**:

**System Errors**:


## BackEnd

**Brief explanation**:

For this section, you will find the routes, processes and models that are necessary for the processing, 
handling and storage of the videos; which are used as services in the Frontend sections and in AWS services
in order to carry out the functionalities of the previously seen.

**Components**:

**Controllers**:

the controllers that are used in the creation of routes, data insertions and objects are the following:

* SalesController.ts

This controller initializes the service routes that are used to find the available product options
to be recommended to the Client divided in the correspondant categories as well as the insertion of new
products made by the Administrator


**Models**:

The models that are used to generate new rows of information in the database are the following:

* **SQL**: Product.ts

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Product_id: ID of the product.

	2. Product_sku: Stock-keeping unit of the product.

	3. Product_name: Name of the product.

	4. Product_description:  Description of the video.

	5. Price: Price of the product.

	6. Stock: Stock available for the product

* **SQL**: Product_category.ts

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Category_id: ID for the product category.

	2. Category_name: Name of the product category.

	3. Category_description: Description of the product category.

* **SQL**: Order.ts

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Order_id: ID of the correspondant order.

	2. Total: Total cost of the order.



	
* **NOSQL**: 

The NoSQL model supports us in formatting the storage information relevant to the 
state of the call and sending it to AWS DynamoDB to create the necessary table for this model.
	

**Routes**:

| Routes                                           | What the Route Does                                                                                         |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| /getProductCategories                            | Get the all the product categories available in the database in RDS.                                        |
| /getProduct/:product_id                          | Get the specified product available in the database in RDS according to the given product id.               |
| /getOwnedProducts/:client_id/:category_id        | Get the owned products by the Client in the database in RDS according to the given client and category ids. |
| /getOwnedProducts/:client_id                     | Get the owned products by the Client in the database in RDS according to the given client id.               |
| /getNotOwnedProducts/:client_id/:category_id     | Get the not owned products by the Client in the database RDS according to the given client and category ids.|
| /getRecommendedProducts/:client_id/:category_id  | Get the recommended products for the Client (based in best options) in the database RDS according to the given client and category ids.|
| /orderHistory/:client_id                         | Get the order history of the obtained products by the Client in the database RDS given its id .             |
| /buyProduct                                      | Post the selling of a product in the database RDS to a specific Client.                                     |
| /createProduct                                   | Post the creation of a new product given its related data in the database RDS.                              |
| /validateSku/:product_sku                        | Get the correspondant product_sku to validate that it exists in the database RDS.                           |
| /updateProduct                                   | Post the update of an existent product with the data specified in the database RDS.                         |



**System validations**:

* **/getProduct**:

| Field      | Validation                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------- |
| product_id | Must be an existent numerical ID in the database RDS.                                                   |

* **/getOwnedProdcuts**:

| Field       | Validation                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| category_id | Must be an existent numerical ID in the database RDS.                                                   |
| client_id   | Must be an existent numerical ID in the database RDS.                                                   |

* **/getProductsNotOwned**:

| Field       | Validation                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| category_id | Must be an existent numerical ID in the database RDS.                                                   |
| client_id   | Must be an existent numerical ID in the database RDS.                                                   |

* **/getRecommendedProducts**:

| Field       | Validation                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| category_id | Must be an existent numerical ID in the database RDS.                                                   |
| client_id   | Must be an existent numerical ID in the database RDS.                                                   |

* **/orderHistory**:

| Field       | Validation                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| client_id   | Must be an existent numerical ID in the database RDS.                                                   |

* **/buyProduct**:

| Field       | Validation                                                                                              |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| product_id  | Must be an existent numerical ID in the database RDS.                                                   |
| client_id   | Must be an existent numerical ID in the database RDS.                                                   |

* **/createProduct**:

| Field               | Validation                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| product_sku         | Must be a number.                                                                                       |
| product_name        | Must be a string.                                                                                       |
| product_description | Must be a string.                                                                                       |
| price               | Must be a number.                                                                                       |
| stock               | Must be a number.                                                                                       |

* **/validateSku**:

| Field               | Validation                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| product_sku         | Must be an exisiting numerical ID in the database RDS.                                                  |
| product_id          | Must be an existent numerical ID in the database RDS.                                                   |

* **/updateProduct**:

| Field               | Validation                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| product_name        | Must be an string.                                                                                      |
| product_id          | Must be an exisiting numerical ID in the database RDS.                                                  |
| product_description | Must be a string.                                                                                       |
| price               | Must be a number.                                                                                       |
| stock               | Must be a number.                                                                                       |
| category_id         | Must be an exisiting numerical ID in the database RDS.                                                  |


**System Status/Errors**:
	
* **/getProduct**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | product                                    | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/getOwnedProdcuts**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | products[0]                                | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/getProductsNotOwned**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | products[0]                                | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/getRecommendedProducts**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | products[0]                                | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/orderHistory**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | orders                                     | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/buyProduct**:

| Code                  	        | Message            			                                    | HTTP Response |
| --------------------------------- | ----------------------------------------------------------------  | ------------- |
| Success                   	    | `${product.product_name} added to client ${req.body.client_id}`   | 200           |
| Internal error of server          | message: error.message 		                                    | 500           |
| External error of server          | message: "External error"                                         | 501           |

* **/createProduct**:

| Code                  	        | Message            			                                    | HTTP Response |
| --------------------------------- | ----------------------------------------------------------------  | ------------- |
| Success                   	    | message: "A product with this sku already exists"                 | 200           |
| Internal error of server          | message: error.message 		                                    | 500           |
| External error of server          | message: "External error"                                         | 501           |

* **/validateSku**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | {product: product,category: catprod[0][0]} | 200           |
| Error to find the product         | message: error.message 		             | 400           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |

* **/updateProduct**:

| Code                  	        | Message            			             | HTTP Response |
| --------------------------------- | -----------------------------------------  | ------------- |
| Success                   	    | "Product updated"                          | 200           |
| Internal error of server          | message: error.message 		             | 500           |
| External error of server          | message: "External error" 	          	 | 501           |


## AWS Services

**Brief explanation**:

On the other hand, in order to be able to store, edit and use the videos with all 
the previously seen functionalities, some services from AWS Connect were needed to 
be able to generate the transcript, rating, object storage formats that will be the 
previous data relevant to the video. plus the same recording of the call, among other 
services necessary for the functionality of the area.

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