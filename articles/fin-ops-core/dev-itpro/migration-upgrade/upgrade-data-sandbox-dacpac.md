---
# required metadata

title: Upgrade from AX 2012 - Dacpac process to upgrade data in Sandbox Tiers 2-5 environments
description: This topic explains how to achieve data upgrade in Sandbox utilizing the dacpac file format from Microsoft Dynamics AX 2012 to Finance and Operations in a sandbox environment. 
author: laneswenka
manager: AnnBe
ms.date: 09/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 20
---

# Upgrade from AX 2012 - Data upgrade in sandbox environments

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This overview will help customers who may no longer have Remote Desktop protocol (RDP) access to their Sandbox Tiers 2-5 environments on their upgrade journey from Microsoft Dynamics AX 2012 to Finance and Operations.  Utilizing a new dacpac based file format, and the Database Movement Toolkit, customers can bring their AX 2012 schema and data in to an existing empty database in a Sandbox.

**We strongly recommend** that you run the data upgrade process in a development environment before you run it in a shared sandbox environment, because this approach will help reduce the overall time that is required for a successful data upgrade. For more information, see [Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade](prepare-data-upgrade.md).

In this process guide, you will learn how to:

> [!div class="checklist"]
> * Open firewall access to your Sandbox environment database.
> * Clear the Sandbox database of all objects.
> * Publish the schema from your AX 2012 database in to the Sandbox database.
> * Transfer the data from the source database to the target.
> * Apply the Data Upgrade package from Lifecycle Services.
> * Copy the database in to Production for mock go live validation and actual go live.

## Open firewall access to your Sandbox environment database
By default, all Sandbox Standard Acceptance Test environments use Microsoft Azure SQL Database as their database platform. The databases for these environments are protected by firewalls that restrict access to the Application Object Server (AOS) with which it was originally deployed.

However, access can be granted to your source system using your public IP address.  This can be enabled in different manners, depending on your environment type and RDP access.  In either case, connecting to the database will require specifying the server and the database explicitly.  The information that is available from the environment details page in Microsoft Dynamics Lifecycle Services (LCS) will provide this information. 

Find the username record for **axdbadmin**, and note the SQL server and database in the format **{sqlServer\\sqlDatabase}** such as 'spartan-nam-opsprod365433.database.windowsnet\DBOpsProd365_SandboxUAT_d2145fe' where the server value for SSMS would be 'spartan-nam-opsprod365433.database.windowsnet' and the database value would be 'DBOpsProd365_SandboxUAT_d2145fe'.  The database must be specified using the **Connection Properties** button in the SSMS connection dialog screen.  Use the axdbadmin username and password.

### Microsoft managed environments with RDP access available
If you have RDP access to your Sandbox, logon to the Sandbox AOS VM and open Microsoft SQL Server Management Studio (SSMS). In SSMS, enter the SQL Server, username, and password. On the **Connection Properties** tab, explicitly enter the database name from the **axdbadmin** record in LCS.

After you're connected, open a query against the database, and enter your IP address in the following Transact-SQL (T-SQL) command.

```sql
-- Create database-level firewall setting for IP a.b.c.d 
EXECUTE sp_set_database_firewall_rule N'AX 2012 Upgrade via RDP', 'a.b.c.d', 'a.b.c.d'; 
```

Back in your source environment, open SSMS, and try to connect by using the same **axdbadmin** credentials against the UAT database. Verify that you can connect before you continue with the next steps.

Note that these rules are deleted whenever you perform a database refresh, or database import from Lifecycle Services.

### Microsoft managed environments without RDP access
If you no longer have RDP access to your Sandbox, you can instead add your IP address to the **allowlist** in a self-service fashion from Lifecycle Services (LCS).  Visit your Sandbox enviornment details page in LCS, and under the **Maintain** -> **Enable access** dialog add your source environment's IP address.  This will expire after a number of hours.

Before the entry expires, connect to the Sandbox database by entering the SQL Server, username, and password. On the **Connection Properties** tab, explicitly enter the database name from the **axdbadmin** record in LCS.

After you're connected, open a query against the database, and enter your IP address in the following Transact-SQL (T-SQL) command.

```sql
-- Create database-level firewall setting for IP a.b.c.d 
EXECUTE sp_set_database_firewall_rule N'AX 2012 Upgrade without RDP', 'a.b.c.d', 'a.b.c.d'; 
```
This will create a second entry in the firewall rules that will not expire.  Note that these rules are deleted whenever you perform a database refresh, or database import from Lifecycle Services.

### Self-service environments
Unfortunately Self-service type Sandbox environments are not supported for AX 2012 upgrade scenarios as they do not support Data Upgrade packages at this time.  Microsoft is working to add this support, and will update this article at a later date with more details.

## Clear sandbox database of all objects
In this step, we will clean out the sandbox database that has Finance and Operations schema.  This will provide a blank or empty database from which you can bring your source AX 2012 schema and later the data as well.  In the event the data upgrade fails, you can always come back to this step and start fresh.

Using SQL Server Management Studio (SSMS), connect to your Sandbox database as you had in prior steps.  Right-click on the database name and select **Tasks** -> **Generate scripts**.  Click Next to advance beyond the Introduction screen, and then on the Choose Objects screen click on the 'Select specific database objects' option.  

Check the boxes next to:
* Tables
* Views
* Stored procedures
* User-defined functions
* Schemas
* Full text catalogs
* User-defined table types

On the Set Scripting Options screen, click on the **Advanced** button and change the value of the 'Script DROP and CREATE' to 'Script DROP' value.  Click OK and then choose the 'Save to new query window' option.  Click next through the summary and then a new query window will open with all of the scripts in the correct order to drop the objects from the database.  

When ready to proceed, execute this script directly against the AXDB database of your Sandbox environment.  It will take some time to complete, on average 15-20 minutes.

## Publish the schema from AX 2012 to the sandbox database
Now that the database is empty, we can bring your non-upgraded 2012 schema.  In this step, you will want to get the latest version of the [Database Movement toolkit](../database/database-movement-toolkit.md) downloaded to your source environment.  

Assuming you have unzipped the toolkit to C:\dbmovement-toolkit\ , go to this folder location using the Command Prompt application or Powershell. 

Run the AX2012SchemaPublish.ps1 script with the following parameters:
* SourceServerName - this can be localhost or wherever your source AX 2012 database is hosted
* AX2012DBName - this is the name of your AX 2012 database
* TargetServerName - this is the server value of your sandbox database server, retrieved in prior steps
* TargetDBName - this is the name of your AXDB, retrieved in prior steps

During execution, the script will make use of SqlPackage.exe to extract only the database and schema definitions from your 2012 database as 2012DBSource.dacpac in the working directory.  Next, it will publish this to your Sandbox environment using the Profile.publish.xml publishing profile included in the toolkit.  This publishing profile will skip over several object types such as SQL Views, SQL Users, Statistics, and other objects which are not required for the upgrade.

When finished, verify that you can see the tables in the Sandbox database via SSMS and confirm that they are indeed empty and have no data.

