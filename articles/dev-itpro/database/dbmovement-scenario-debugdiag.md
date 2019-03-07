---
# required metadata

title: Debugging a copy of the production database
description: This topic explains a debugging and diagnostics scenario for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 03/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3

---

# Debugging a copy of the production database

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that can be used as part of data application lifecycle management (DataALM). This tutorial shows how to debug specific data and transactions from a recent copy of production data.

In this tutorial, you will learn how to:

> [!div class="checklist"]
> * Refresh the user acceptance testing (UAT) environment.
> * Whitelist your developer environment IP address.
> * Update your developer environment to connect to the UAT database.
> * Place a breakpoint and start debugging the data.

As an example of this scenario, a customer who has already gone live with Microsoft Dynamics 365 for Finance and Operations wants to debug a recent copy of production transactions from his or her development environment. In this way, the customer will be able to debug specific transactions which are stuck or develop new features and reports by using realistic datasets.

## Prerequisites

To do a refresh operation, you must have your production environment deployed, or you must have a minimum of two standard UAT environments. To complete this tutorial, you must have a developer environment deployed.

[!Important]
- It is highly recommended to use a DevTest environment for debugging that will run the same code and business logic as is available in your UAT environment.  If you use multiple branches in version control we recommend that this DevTest environment used for debugging recent UAT or Production transactions is connected to the same branch you build packages for UAT and later Production.  This will eliminate any need for you to run a Database Sync between your DevTest environment and UAT database as the schema will be compatible.  Historically this is known as a Hotfix/Support environment as it is outside of your normal code promotion path.

## Refresh the UAT environment 

This refresh operation will overwrite the UAT environment with the latest copy of the production database. To complete this step, follow the instructions in [Refresh for training purposes](dbmovement-scenario-general-refresh.md).

## Whitelist your IP address
By default, all Sandbox Standard Acceptance Test environments use Azure SQL as their database platform.  These databases are protected by firewalls which restrict access to the Application Object Server (AOS) from which it was originally intended.  

An exception can be made for you to connect your developer environment (cloud-hosted or Microsoft managed) directly to the UAT database. To do this you will need to obtain your IP Address on the developer VM.

From the sandbox AOS VM, open SQL Server Management Studio (SSMS) and connect to the database using the information available from the Environment Details page in Lifecycle Services (LCS).  Locate the username record for **axdbadmin** and note the Azure SQL Server and Azure SQL Database in the format of {sqlServer\sqlDatabase}. 

Using SSMS, enter the SQL Server, username, and password.  On the **Connection Properties** tab, explicitly enter the database name from the axdbadmin record in LCS.  

Once connected, open a query against the database and enter your IP address in to the below T-SQL command:
```
-- Create database-level firewall setting for IP a.b.c.d 
EXECUTE sp_set_database_firewall_rule N'Debugging rule for DevTest environment', 'a.b.c.d', 'a.b.c.d'; 
```
Transition back to your developer environment.  Open SSMS and attempt to connect with the same axdbadmin credential against the UAT database.  Verify that you can connect, before proceding with the next steps.

> [!Note]
> Each time a refresh is performed, the firewall whitelist is reset.  You will need to add your DevTest environments back to this database when needed in the future.

## Update a OneBox DevTest environment to connect to the UAT database
In your developer environment, we will now update the web.config to change the database connection.  This will allow you to run your local code and binaries configured against the database from UAT.  

Navigate to your Services Drive (commonly this is the J or K drive) \ AoSService\WebRoot directory.  Find the file called web.config and *make a backup of this file*.  Open the web.config file in NotePad or an editor of your preference, and locate the following configurations:
- DataAccess.Database
- DataAccess.DBServer
- DataAccess.SqlPwd
- DataAccess.SqlUser

Update these to use the values from the UAT Environment Details page in LCS:
```
    <add key="DataAccess.Database" value="<example_axdb_fromAzure>" />
    <add key="DataAccess.DbServer" value="<example_axdb_server.database.windows.net>" />
    <add key="DataAccess.SqlPwd" value="<axdbadmin_password_from_LCS>" />
    <add key="DataAccess.SqlUser" value="axdbadmin" />
```
Save the file, and execute an IISRESET if you are operating a cloud hosted environment.  If you are operating on a Microsoft Managed developer machine with limited permissions, ensure that Visual Studio is closed.  

Finally, open a browser and visit the URL of your DevTest environment and validate that you are pulling the data from the UAT database.

## Debug transactions in the DevTest environment
Now that your environment is properly reconfigured, you can open Visual Studio and place a breakpoint in the application code that best meets your needs.  Note that while you are debugging in the DevTest environment, the users in the UAT environment are not impacted.  

## Best practices 
Below are common best practices that ensure your debugging experience is quick, reliable, and doesn't disrupt other users in your organization:
1. Ensure that the version of the code and binaries in the DevTest environment exactly match UAT.  This can be accomplished by connecting the DevTest environment to the same branch you build packages from for deployment, or a 'HotfixSupport' branch that is kept up to date with the latest customizations that are released.
2. Do not execute a Database Sync from Visual Studio.  This will impact the availability of schema in the UAT database, and could adversely impact users in the UAT environment.

## Known issues

