# Agent reports

Agent reports is the area of the project where users of the application can see metrics relevant to their performance. Depending on the user's role, they are permitted to see the metrics of a certain subset of agents or only personal KPIs. These reports are developed using Amazon Quicksight, embed to the application's frontend and gather data using a direct connection to the AWS RDS Database.

# RDS Database

**Este le va al anlic**
<img src="https://raw.githubusercontent.com/AmazonConnect-TECCEM-502/AmazonConnectDB/main/Database%20ER%20Diagram.jpg"
     alt="ER Diagram"/>

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

