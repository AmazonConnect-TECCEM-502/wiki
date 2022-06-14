# Agent reports

Agent reports is the area of the project where users of the application can see metrics relevant to their performance. Depending on the user's role, they are permitted to see the metrics of a certain subset of agents or only personal KPIs. These reports are developed using Amazon Quicksight, embed to the application's frontend and gather data using a direct connection to the AWS RDS Database.

# Database Schema

To represent the business logic of the application, a database model that features the necessary attributes of each entity was created. Hence, the schema of the datbase is represented as follows:

<img src="https://raw.githubusercontent.com/AmazonConnect-TECCEM-502/AmazonConnectDB/main/Database%20ER%20Diagram.jpg"
     alt="ER Diagram"/>

## Implemented entities

### User
Description:
An agent that is currently working for the organiation and has a role in the call center. Can be either an agent, manager or the system administrator.
- User ID
- First Name
- Last Name
- Email
- User type
- Cognito UUID
- Manager ID (References itself)

### Client
Description:
A client that acquired a service at any point of time.
- Client ID
- First Name
- Last Name
- Email
- Phone

### Product
Description:
A product that is offerable to the client.
- Name
- SKU
- Description
- Price
- Stock

### Call
Description:
An abstraction of a call performed between a User and a Client. Statistics are stored for future KPI's processing.
- Call ID
- Agent ID
- Client ID
- Creation Timestamp
- Video URL (The recording that corresponds to the agent's view during a call)
- Transcription URL (Formatted text that describes the conversation)
- Rating (Value from 0 to 5 that describes the quality of service)

### Problem
Description:
The specific problem that the client states at the beginning of the call interpreted by the agent.
- Problem ID
- Problem Description
- Submitted By (The agent that registered the problem)
- Cretion Timestamp

### Problem category
Description:
The category of a problem 

### Solution
Description:
A concise description and root cause of the problem and the method used to solve it.
- Solution ID 
- Description (Plaintext of the steps followed) 
- Problem ID
- Approved By (The agent's manager)
- Date of approval
- Date of creation

### Order
Description:
An order issued by the client at the time of the call. 
- Order ID
- Client ID
- Product ID
- Date of Purchase
- Total

# RDS Database

RDS AWS service was used to host a relational SQL Sever database that allows the connection between the back-end and the database host. Due to the volume of data used in the test environment (less than a GiB), we implemented a t3.micro with a storage capacity of 20 GiB with only 1 GiB of RAM and 2 vCPUs. However, in a production environment the specifications of the database should be assessed according to business need. This is an advantage of using this specific cloud service due to the elasticity in deployment of hardware capacity. Seasonal restores of the database were performed to mitigate risks of unavailability such as unexpected disruptive SQL transactions such as ALTER, TRUNCATE, DROP, etc.

To connect to the database, an ACL has to be configured to set permit rules to allow outbound connections to the database, namely, specify the IP of the back-end server and the port number for SQL operations (3306).


## Filling the database with test data

To fill the database with test data easily, a Visual Basic for Applications script was developed to automate the process. The data is placed as tables in an excel file and the generic script traverses through all the sheet and its columns to build the SQL insert operation using a cursor. It uses MySQL ODBC 8.0 Unicode Driver. To replicate its usage, the parameters of the connections must be modified to the desired database and the excel file sheet names must match the table name on the target database.
* [ **DummyDataImport.bas**: ](https://github.com/AmazonConnect-TECCEM-502/AmazonConnectDB/blob/main/Dummy%20Data/DummyDataImport.bas)

# Amazon Quicksight

Amazon Quicksight was the service chosen to deliver the agents reports because of its versatility and easiness to update. When we needed to make changes to a specific dashboard, we just needed to publish it again and the front end would show it immediately. The direct connection to the database was easily approached using the predefined RDS connection, however a connection with MySQL could also have been possible. 

## Manager Dashboard

The manager dashboard provides information regarding the agents mapped to a specific person. It is divided into an overview of the manager's indicators in relation to solutions, problems, and sales, whereas the performance tab gives visibility to the work of all the agents under a specific person. There's also the possibility to filter to see the information of an explicit agent.

Available metrics:

* Manager's Overview
    * Solution's approved
    * Solutions pending approval
    * Sales by day
    * Problems by category
    * Products by orders sold
    * Common problem words
* Agent's Performance
    * Total calls attended
    * Total problems submitted
    * Total solutions submitted
    * Average Call Rating
    * Average Rating by Agent
    * Calls by agent
    * Frequency of calls per Week

## Agent Dashboard

The agent dashboard is the way for an agent to know its performance related to rating, calls, problems, and frequency. It helps them to see if they are approaching their objectives in case they have a specific quota to achieve. The dashboard is a one-pager with all the relevant KPIs for an agent's performance.

Available metrics:

* Agent Performance
    * Total calls attended
    * Total problems submitted
    * Total solutions submitted
    * Total solutions approved
    * Average Rating
    * Frequency of calls per Week

## Parameters

To maintain encapsulation and data privacy among all managers, the dashboard is filtered automatically on start by using the user id from the local storage. The `iframe ` source gets the user id appended at the end so that it is filtered as shown in the example.

Agent Dashboard: `samplequicksightlink.com#p.agent={user_id}`

Manager Dashboard: `samplequicksightlink.com#p.manager={user_id}`

## Dashboard embedding

To connect the Quicksight dashboards with the frontend using an `iframe`, the domain needs to be allow listed directly through the *Manage Quicksight* section on the tool. The link gets added into the *Domains and Embedding* section. It's important to point out all domains need to be secured with HTTPS or else they fail the security policy and won't be allow listed. The domain approved for this case is https://app.tecmex-connect.link. 

