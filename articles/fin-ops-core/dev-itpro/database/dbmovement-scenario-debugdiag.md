---
# required metadata

title: Debug a copy of the production database
description: This topic explains a debugging and diagnostics scenario for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 06/15/2020
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

# Debug a copy of the production database

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that can be used as part of data application lifecycle management (DataALM). This tutorial shows how to debug specific data and transactions from a recent copy of production data.

In this tutorial, you will learn how to:

> [!div class="checklist"]
> * Refresh the user acceptance testing (UAT) environment.
> * Add the IP address of your developer environment to an approved list ("safe list").
> * Update your developer environment so that it connects to the UAT database.
> * Set a breakpoint, and start to debug the data.

As an example of this scenario, a customer who has already gone live wants to debug a recent copy of production transactions from his or her development environment. In this way, the customer will be able to debug specific transactions that are stuck, or develop new features and reports by using realistic datasets.

## Prerequisites

To do a refresh operation, you must have your production environment deployed, or you must have a minimum of two standard UAT environments. To complete this tutorial, you must have a developer environment deployed.

> [!IMPORTANT]
> For debugging, we highly recommend that you use a DevTest environment that runs the same code and business logic that are available in your UAT environment. If you use multiple branches in version control, we recommend that the DevTest environment that is used to debug recent UAT or production transactions be connected to the same branch that you use to build packages for UAT and, later, for production. In this way, you don't have to run a database synchronization between your DevTest environment and UAT database, because the schema will be compatible. Historically, this environment is known as a Hotfix/Support environment, because it's outside your usual code promotion path.

## Refresh the UAT environment 

This refresh operation overwrites the UAT environment with the latest copy of the production database. To complete this step, follow the instructions in [Refresh for training purposes](dbmovement-scenario-general-refresh.md).

## Add your IP address to a safe list

By default, all Sandbox Standard Acceptance Test environments use Microsoft Azure SQL Database as their database platform. The databases for these environments are protected by firewalls that restrict access to the Application Object Server (AOS) with which it was originally deployed.

However, an exception can be made so that you can connect your developer environment (cloud-hosted or Microsoft-managed) directly to the UAT database. To connect your developer environment directly to the UAT database, you must obtain your IP address on the developer virtual machine (VM).

On the sandbox AOS VM, open Microsoft SQL Server Management Studio (SSMS), and connect to the database by using the information that is available from the environment details page in Microsoft Dynamics Lifecycle Services (LCS). Find the username record for **axdbadmin**, and note the server and database in the format **{sqlServer\\sqlDatabase}**.

In SSMS, enter the SQL Server, username, and password. On the **Connection Properties** tab, explicitly enter the database name from the **axdbadmin** record in LCS.

After you're connected, open a query against the database, and enter your IP address in the following Transact-SQL (T-SQL) command.

```sql
-- Create database-level firewall setting for IP a.b.c.d 
EXECUTE sp_set_database_firewall_rule N'Debugging rule for DevTest environment', 'a.b.c.d', 'a.b.c.d'; 
```

Back in your developer environment, open SSMS, and try to connect by using the same **axdbadmin** credentials against the UAT database. Verify that you can connect before you continue with the next steps.

> [!NOTE]
> Every time that a refresh is done, the firewall safe list is reset. You must add your DevTest environments back to this database when they are required in the future.

## Update a OneBox DevTest environment to connect to the UAT database

In your developer environment, you must now update the web.config file to change the database connection. This step will let you run your local code and binaries that are configured against the database from UAT.

On your Services drive, go to the **AoSService\\WebRoot** directory. (Typically, the Services drive is drive J or K.) Find the file that is named web.config, and *make a backup of it*. Then open the **web.config** file in Notepad or another editor, and find the following configurations:

- DataAccess.Database
- DataAccess.DBServer
- DataAccess.SqlPwd
- DataAccess.SqlUser

Update these configurations so that they use the values from the environment details page for the UAT environment in LCS.

```xml
<add key="DataAccess.Database" value="<example_axdb_fromAzure>" />
<add key="DataAccess.DbServer" value="<example_axdb_server.database.windows.net>" />
<add key="DataAccess.SqlPwd" value="<axdbadmin_password_from_LCS>" />
<add key="DataAccess.SqlUser" value="axdbadmin" />
```
Save the file. If you're operating in a cloud-hosted environment, run IISRESET. If you're on a Microsoft-managed developer machine and have limited permissions, make sure that Microsoft Visual Studio is closed.

Finally, open a web browser, go to the URL of your DevTest environment, and verify that you're pulling data from the UAT database.

## Debug transactions in the DevTest environment

Now that your environment is correctly reconfigured, you can open Visual Studio and set a breakpoint in the application code that best meets your needs. Note that users in the UAT environment aren't affected while you debug in the DevTest environment.

## Best practices

Here are some common best practices that will help guarantee that your debugging experience is quick, reliable, and doesn't disrupt other users in your organization:

- Make sure that the version of the code and binaries in the DevTest environment exactly match the version in the UAT environment. Connect the DevTest environment to the same branch that you build packages for deployment from. Alternatively, connect it to a "HotfixSupport" branch that is kept up to date with the latest customizations that are released.
- Don't run a database synchronization from Visual Studio. Otherwise, you will affect the availability of the schema in the UAT database and might affect users in the UAT environment.
