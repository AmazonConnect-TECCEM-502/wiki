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

## [ FrontEnd ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

#### React

The `react` package contains only the functionality necessary to define
React components. It is typically used together with a React renderer 
like react-dom for the web, or react-native for the native environments.

`npm install react`


#### React-Icons

Include popular icons in your React projects easily with `react-icons`, 
which utilizes ES6 imports that allows you to include only the icons that your project is using.

`npm install react-icons --save`


## [ BackEnd ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

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

* [ **ProductsCategoryList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/ProductsCategoryList.js)

This component allows the agent to visualize all the existing categories of the available porducts, in order to display the products corresponding to a certain category.

**Categories List**

![Category List Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/CategoryList.PNG)


* [ **ProductList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/ProductList.js)

This component allows the agent to visualize a list of the available products that belong to the category chosen in the previous component.

**Product List**

![Product List Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ProductList.PNG)


* [ **ProductCard.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/ProductCard.js)

This component allows the agent to visualize the details of the selected product, like name, image, price and description of the product. This component also allows the agent to add the product to the client with the Add button, and go back to the prodcut list. 

**Product Example**
 
* [ **ProductImage.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/ProductImage.js)

This component allows to assign an image to each product, extracting it from the S3 bucket according to the product's name. 

**Product Image**

![Product Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/ProductImage.PNG)


* [ **SalesMasterCard.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/SalesMasterCard.js)

This component is the one that gives functionnality to the rest of the components. It get the recommended products for the client according to the problem, allows to assign the porduct to the client and allows the transition between the different components. 

* [ **ConfirmCard.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/SalesCard/ConfirmCard.js)

This component allows the user to confirm if the agent really wants to add the product to the actual client, displaying a pop-up window. 

**Confirm Product**

![Confirmation Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/Confirmation.PNG)

* [ **NewProduct.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/NewProduct.js)

This component allows the admin to create a new product, by getting the product's name, SKU, category, description, price, stock and image. 

**Creation of a new product**

![Confirmation Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/CreateProduct.PNG)

* [ **UpdateProduct.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/UpdateProduct.js)

This component allows the admin to update one of the existing products with the SKU of the corresponding product.

**Update Product**

![Confirmation Image](https://github.com/AmazonConnect-TECCEM-502/wiki/blob/main/Wiki%20Images/UpdateProduct.PNG)

## [ BackEnd ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

**Brief explanation**:

For this section, you will find the routes, processes and models that are necessary for the processing, 
handling and storage of the videos; which are used as services in the Frontend sections and in AWS services
in order to carry out the functionalities of the previously seen.

**Components**:

**Controllers**:

the controllers that are used in the creation of routes, data insertions and objects are the following:

* [ SalesController.ts ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/controllers/SalesController.ts)

This controller initializes the service routes that are used to find the available product options
to be recommended to the Client divided in the correspondant categories as well as the insertion of new
products made by the Administrator


**Models**:

The models that are used to generate new rows of information in the database are the following:

* [ **SQL**: Product.ts ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/product.ts)

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

* [ **SQL**: Product_category.ts ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/product_category.ts)

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Category_id: ID for the product category.

	2. Category_name: Name of the product category.

	3. Category_description: Description of the product category.

* [ **SQL**: Order.ts ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/order.ts)

This model supports us to generate the compatible model with the relevant 
information between the database implemented in AWS RDS, with the information
generated in the application, in order to maintain consistency and order of the data.

The data needed for this model are:


	1. Order_id: ID of the correspondant order.

	2. Total: Total cost of the order.
	
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

On the other hand, in order to be able to store, edit and use the product's images for the sales functionnalities, we used the following AWS services: 

**Buckets**:

* images-texmex-users-2-0 /sales: Bucket that stores all the porduct's images that are used in the porduct card.


**Lambdas**:

* images-texmex-users-2-0: Lambda function that allows us to get the image from the Bucket. 

# 