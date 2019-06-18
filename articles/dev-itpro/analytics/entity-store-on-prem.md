---
# required metadata

title: PowerBI.com integration with on-premises environments
description: This topic provides information about how to enable Entity Store for on-premises deployments.
author: MilindaV
manager: AnnBe
ms.date: 06/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: EntityStoreOnPrem
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 27661
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2019-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# PowerBI.com integration with on-premises environments

[!include [banner](../includes/banner.md)]

Cloud version on Dynamics 365 for Finance and Operations (F&O) provides several features that enable deeper integration with PowerBI. Some of these capabilities are not yet implemented on Dynamics 365 for Finance and Operations on-premises deployments. With the availability of Entity store in on-premises deployments, customers can leverage PowerBI.com for reporting and analytics with F&O data. 
This document outlines the Analytics capabilities available in on-premises deployments with Platform update 26 and later.

| Feature/capability                                                     | Cloud     | On-premises (Platform update 26 or later)                                                         |
|------------------------------------------------------------------------|-----------|---------------------------------------------------------------------------------------------------|
| Analytical workspaces                                                  | Available | **Not yet implemented** <br> Customers can use the reports built on Entity store with PowerBI.com.                                                                               |
| Pin reports, tiles, and dashboards from PowerBI.com into the client    | Available | **Not yet implemented**                                                                               |
| Author and distribute PowerBI reports with Finance and Operations data | Available | **Available** <br> Customers can modify ready-made reports and create new reports by using Entity store on-premises. |
| Extract Finance and Operations data into data warehouses               | Available | **Available**                                                                                        |

## Enable Entity Store on-premises 
This topic supplements the topic, [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-pu12.md). The section numbers in this topic, correspond to the sections in that topic.

## [3. Plan your users and service accounts](../deployment/setup-deploy-on-premises-pu12.md#3-.-plan-your-users-and-service-accounts)

| User account               | Type     | Purpose                                                                                                                                              | User name       |
|----------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| AOS SQL AXDW DB Admin user | SQL user | Finance and Operations uses this user to populate the AXDW database. The user is optional and must be created only if you want Entity Store support. | axdwadmin       |
| AOS SQL AXDW FB Admin user | SQL user | Finance and Operations uses this user to populate the AXDW database. The user is optional and must be created only if you want Entity Store support. | axdwruntimeuser |

## [14. Configure the databases](../deployment/setup-deploy-on-premises-pu12.md#14.-configure-the-databases)
Configure the Entity Store database (Optional)
1.	If you want to create database to use for Entity Store then  first you need to make changes in ConfigTemplate.xml. Under DbServer – Security, set generateUser flags of axdwadmin and axdwruntimeuser to true. By doing this, scripts in step 2 will create those 2 users. You will be prompted with request to set passwords for those users.
2.	Execute the following scripts.

.\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName EntityStore
.\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName EntityStore

The Initialize-Database.ps1 script will do the following:
•	Create an empty database named AXDW. This database is used for Entity Store.
•	Create a new user that has SQL authentication enabled (axdwadmin   ) and ask for a password for the user.
•	Create a new user that has SQL authentication enabled (axdwruntimeuser) and ask for a password for the user.
•	Grant  axdwadmin and axdwruntimeuser db_owner permissions on the database.
The Configure-Database.ps1 script will do the following:
•	Set the specified database file and log settings.
•	GRANT VIEW SERVER STATE TO axdwadmin.
•	GRANT VIEW SERVER STATE TO axdwruntimeuser.









15. Encrypt credentials
3.	Create the Credentials.json file, as shown here. AosDWAuth     category is optional and being used only if Entity Store is enabled.
{
    "AosPrincipal": {
        "AccountPassword": "<encryptedDomainUserPassword>"
    },
    "AosSqlAuth": {
        "SqlUser": "<encryptedSqlUser>",
        "SqlPwd": "<encryptedSqlPassword>"
    },
    "AosDWAuth": {
        "DWUser": "<encryptedDWUser>",
        "DWPwd": "<encryptedDWPassword>",
        "DWRuntimeUser": "<encryptedDWRuntimeUser>",
        "DWRuntimePwd": "<encryptedDWRuntimePassword>"
    }
}

•	AccountPassowrd is the encrypted domain user password for the AOS domain user (contoso\axserviceuser)
•	SqlUser is the encrypted SQL user (axdbadmin) that has access to the Finance and Operations database (AXDB), and SqlPwd is the encrypted SQL password.
•	DWUser is the encrypted SQL user (axdwadmin) that has access to the Entity Store database (AXDW), and DWPwd is the encrypted SQL password that is entered during running of Initialize-Database.ps1 script.
•	DWRuntimeUser is the encrypted SQL user (axdwruntimeuser) that has access to the Entity Store database (AXDW), and DWRuntimePwd is the encrypted SQL password that is entered during running of Initialize-Database.ps1 script.



Additional Information
Entity Store is enabled from PU26
Creating Entity Store database and users is optional. While configuring deployment in LCS, user can leave Entity Store customizations empty.
If Entity Store should be enabled on environment, then following needs to be done:
•	AXDW database created using scripts in step 14.
•	axdwadmin and axdwruntimeuser users created with appropriate privileges using scripts in step 14. Users are defined in following files: ConfigTemplate.xml and DatabaseTopologyDefinition.xml   .
•	Credentials.json created as described in step 15. Usernames and passwords for axdwadmin and axdwruntimeuser should be defined as in step 14 and encrypted.
•	Entity Store SQL Server name and Entity Store Database name values filled in during deployment in LCS. 
o	Database name is the one created in step 14 and it is defined in DatabaseTopologyDefinition.xml. Default name is AXDW.
o	SQL Server name is the fully qualified domain name of the Microsoft SQL Server or Always on listener, e.g. “sqlinstance.onprem.contoso.com”. It is the server on which AXDW is created.
Enabling Entity Store is currently possible only during initial deployment. If it needs to  be enabled on existing environment, then that environment needs to be deleted and deployed again using platform update that supports entity store.

Authoring and distributing reports with Entity store on-premises
Entity store is an Operational data warehouse included with F&O. Entity store enables Power users and Business Analysts to author reports using simplified and enriched data from F&O. Entity store contains Aggregate measurements – which are simplified star schemas. For more on authoring reports with entity store, see the article here: https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/author-distribute-power-bi-reports
Please note following additional steps specific to on-premises deployments below
•	Use of Life cycle services (LCS) to deploy PowerBI reports to production or sandbox environments is not required in on-premises environments. Since administrators can point PowerBI.com datasets to respective Entity store databases in on-premise environments, there is no need to use functionality offered by LCS. You may need to configure on-premises gateway to enable PowerBI.com to access data on premises. See documentation on gateway here: https://powerbi.microsoft.com/en-us/gateway/
•	While cloud based F&O environments support only reports authored with DirectQuery option, on-premises Entity store supports both DirectQuery as well as Import mode reports.
•	Analytical workspaces are not yet implemented in on-premises deployments. Instead of viewing reports in Analytical workspaces, same reports can be deployed to PowerBI.com environments can be used with users who have access to PowerBI.com. Your users may need appropriate licenses to access reports in PowerBI.com.
