# Azure Bot Framework - Rich Media Cards and Conversation Logger

### This guide will help you get going with sending the user a greeting card. You will also learn how to integrate custom middleware to log conversations to a Cosmos database.

When you've completed this tutorial, you should expect to see this:
<br/><img src="../screens/new_qna_maker_serviwce.jpg" /><br/><br/>

### What is Cosmos DB?

Azure Cosmos DB was built from the ground up with global distribution and horizontal scale at its core. It offers turnkey global distribution across any number of Azure regions by transparently scaling and replicating your data wherever your users are. Elastically scale your writes and reads all around the globe, and pay only for what you need.

Azure Cosmos DB provides native support for NoSQL and OSS APIs including MongoDB, Cassandra, Gremlin and SQL. Today, we'll be using the SQL document API since it will be very familiar to anyone that has experience with TSQL.

<br />

## Section 1: Create the Cosmos DB account in Azure Portal

1. Browse to [https://portal.azure.com](https://portal.azure.com) and log in

1. Click the __Create Resource__ button in the top left corner and search for `Cosmos DB` and click on the first result

1. Click the __Create__ button at the bottom
<br/><img src="../screens/new_cosmos_account.jpg" />

1. Select the same __Resource Group__ that contain your other bot services

1. Enter a unique value for the __Account Name__
	
1. Select __Core (SQL)__ for the API type

1. Select a __Location__ for the master or leave the default

1. Leave __Geo-Redundancy__ disabled for now, we won't be using it for this tutorial but you can enable this at any time so feel free to experiment with it at a later time

1. Click the __Review + create__ button to validate your settings, then click the __Create__ button

1. It will take a few minutes for your new Cosmos account to completely deploy so just keep an eye on the progress
<br/><img src="../screens/deployment_in_progress.jpg" width="50%" />

1. Once your deployment finishes, click on the __Go to Resource__ button or search for the name of the Cosmos account in the search bar
<br/><img src="../screens/deployment_succeeded.jpg" width="50%" />

1. You should now be on the Quick Start page of your new Cosmos DB account - click on the __Keys__ section

1. On the __Read-write Keys__ tab, copy the URI and one of the keys (doesn't really matter which one) to somewhere temporarily
<br/><img src="../screens/cosmos_account_keys.jpg" />

<br/>

## Section 2: Add in `ConversationLogger` Middleware

1. Start here...