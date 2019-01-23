---
# required metadata

title: Database Movement Operations - 'Golden Configuration' Scenario
description: This topic explains a golden config promotion scenario for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 1/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: AX 7.0.0

---

# Tutorial: 'Golden configuration' promotion

[!include [banner](../includes/banner.md)]

Database Movement operations are a suite of self-service actions that can be used as part of Data Application Lifecycle Management ( also referred to as 'DataALM' ).  'Golden configuration' refers to a common practice among customers and partners in the Dynamics ecosystem whereby a developer environment is used as a configuration store.  This allows implementation projects to store finalized global and company-specific settings in a database that can later become a baseline for Conference Room Pilots, Mock Go Lives, and Go Lives.  This tutorial shows how to prepare a golden configuration database and hydrate a target UAT environment.

In this tutorial, you will learn how to:
>[!div class="checklist"]
> * Prepare the golden configuration database for Azure SQL
> * Execute the Import to the target UAT environment
> * Copy the UAT environment in to a Production environment

An example of this scenario is a customer who has not gone live with Microsoft Dynamics365 for Finance and Operations, and instead is in the process of preparing for a Conference Room Pilot, Mock Go Live, or Go Live.  This will support promoting a baseline 'golden' database from a developer environment to a UAT environment and eventually Production.

## Prerequisites
To complete this tutorial you must have a developer environment deployed with a database curated as a 'golden configuration' database.  You must also have at least one Standard User Acceptance Test (UAT) environment and optionally a Production environment deployed.

The developer environment must run the same *application version* of Finance and Operations as the target UAT environment.  In addition, the *platform version* of the developer environment must be earlier than or the same as the platform version in the target UAT environment.

## Before you begin

### Supported SQL Server collation

The only supported collation for Finance and Operations databases in the cloud is **SQL_Latin1_General_CP1_CI_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

### Document the values of encrypted fields

Encrypted and environment-specific values can't be imported into a new environment. After you've completed the import, you must re-enter some data from your source environment in your target environment.

Because of a technical limitation that is related to the certificate that is used for data encryption, values that are stored in encrypted fields in a database will be unreadable after that database is imported into a new environment. Therefore, after an import, you must manually delete and re-enter values that are stored in encrypted fields. New values that are entered in encrypted fields after an import will be readable. The following fields are affected. The field names are given in Table.Field format.

| Field name                                               | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by the Data Import/Export Framework (DIXF). |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since Microsoft Dynamics AX 7.0 (February 2016). It previously appeared in the **All worker actions** form (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMPTPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by AOS. It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                 | This field is used internally by AOS. It can be ignored. |

### If you're running Retail components, document encrypted and environment-specific values

The values on the following pages are either environment-specific or encrypted in the database. Therefore, all the imported values will be incorrect.

- Payments services (**Accounts receivable** &gt; **Payments setup** &gt; **Payments services**)
- Hardware profiles (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**)

## Create a copy of the source database

Because you must delete database users before you can export the source SQL Server database, you should create a copy of that database. You can then work with the copy instead of modifying the original database. The following script backs up the default AxDB database and then restores it to the same instance under a new name. To use this script, first verify that the path D:\\backups exists.

```
BACKUP DATABASE [AxDB] TO DISK = N'D:\Backups\axdb_golden.bak' WITH NOFORMAT, NOINIT,
NAME = N'AxDB_golden-Full Database Backup', SKIP, NOREWIND, NOUNLOAD, COMPRESSION, STATS = 10
GO
RESTORE DATABASE [AxDB_CopyForExport] FROM DISK = N'D:\Backups\axdb_golden.bak' WITH FILE = 1,
MOVE N'AXDBBuild_Data' TO N'F:\MSSQL_DATA\AxDB_CopyForExport.mdf',
MOVE N'AXDBBuild_Log' TO N'G:\MSSQL_LOGS\AxDB_CopyForExport_Log.ldf',
NOUNLOAD, STATS = 5
```

## Prepare the database

Run the following script against the AxDB\_CopyForExport database that you created in the previous section. This script makes the following changes:

- Set the **SysGlobalConfiguration** flag to inform Finance and Operations that the database is Azure-based.
- Remove a reference to tempDB in the XU\_DisableEnableNonClusteredIndexes procedure. References to tempDB aren't allowed in an Azure SQL database. The database synchronization process will re-create the reference later.
- Drop users, because Microsoft Windows users are forbidden in Azure SQL databases. Other users must be re-created later, so that they're correctly linked to the appropriate sign-in on the target server.
- Clear encrypted hardware profile merchand properties

A successful export and import of the database requires all these changes.

```
update sysglobalconfiguration
set value = 'SQLAZURE'
where name = 'BACKENDDB'

update sysglobalconfiguration
set value = 1
where name = 'TEMPTABLEINAXDB'

drop procedure XU_DisableEnableNonClusteredIndexes
drop procedure if exists SP_ConfigureTablesForChangeTracking
drop procedure if exists SP_ConfigureTablesForChangeTracking_V2
drop schema [NT AUTHORITY\NETWORK SERVICE]
drop user [NT AUTHORITY\NETWORK SERVICE]
drop user axdbadmin
drop user axdeployuser
drop user axmrruntimeuser
drop user axretaildatasyncuser
drop user axretailruntimeuser
drop user axdeployextuser
-- Clear encrypted hardware profile merchand properties
update dbo.RETAILHARDWAREPROFILE set SECUREMERCHANTPROPERTIES = null where SECUREMERCHANTPROPERTIES is not null
```

## Export the database from SQL Server

Open a **Command Prompt** window and run the following commands.

> [!IMPORTANT]
> The **140** folder reflects the current version, you are required to use the version that is available in your sandbox environment. This may require you to install the [latest version of Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) in your development environment.

```
cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin\
SqlPackage.exe /a:export /ssn:localhost /sdn:<database to export> /tf:D:\Exportedbacpac\my.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false
```

Here is an explanation of the parameters:

- **ssn (source server name)** – The name of the SQL Server to export from. For the purposes of this topic, the name should always be **localhost**.
- **sdn (source database name)** – The name of the database to export.
- **tf (target file)** – The path and name of the file to export to. The folder should already exist, but the export process will create the file.

## Import the database
Upload the .bacpac file created in the previous step to your LCS Project's Asset Library under the **Database backup** section.  Next, begin the import which will overwrite the target UAT environment's databases with the golden configuration database.

[!include [dbmovement-import](../includes/dbmovement-import.md)]

## Perform master data migration
Now that the UAT enviornment is hydradted with the golden configuration, you can begin the master data migration.  This can be done [using data entities](../data-entities/develop-entity-for-data-migration.md).  It is recommended to complete your data migration activities prior to copying the UAT environment to production as you will have access in UAT to the database to troubleshoot.

## Copy the Sandbox database to Production

When you're ready to perform a mock go live or actual go live you can copy the UAT environment in to Production.  This process is commonly referred to as 'Cutover' and is recommended to be exercised more than once before your actual go live.  This will allow you to get detailed time estimates on each step of the process, including the submit of a service request for **Sandbox to Production**. In this request, you ask that Microsoft run the copy action.

> [!NOTE]
> You can't use a request of the **Database refresh request** type, because the request involves copying to a production environment.

1. In LCS, on the Project home page, select **Service requests**.
2. On the **Service requests** page, select **Add**, and then select **Sandbox to Production**.
3. In the **Sandbox to Production** dialog box, follow these steps:

    1. In the **Environment name** field, select the production environment.
    2. Set the **Preferred downtime start date** and **Preferred downtime end date** fields. The end date must be at least one hour after the start date. To help guarantee that resources are available to run the request, submit your request at least 24 hours before your preferred downtime window.
    3. Select the check boxes at the bottom to agree to the terms.

## Reconfigure environment specific settings
After the refresh is complete, use the **Sign off** button in LCS to close out of the operation.  We then can begin the process to configure the environment specific settings.

Start by logging in to the environment using the adminsitrator's account which can be found on the **Environment details** page in LCS.  Some common areas of reconfiguration are below, you may require additional based on your setup and ISV solutions that are installed:
* System administration -> Setup -> **Batch groups**. Add the various AOS to the batch server groups you require.
* System administration -> Setup -> **Entity Store**. Refresh the various entities that you require for PowerBI reporting.
* System administration -> Setup -> **System parameters**. Reconnect the environment to the LCS Help Configuration for Task Guides.
* System administration -> Setup -> Email -> **Email parameters**. Enter the SMTP settings if you use email in your UAT environment.  
* System administration -> Inquiries -> **Batch jobs**. Highlight the jobs you wish to run in your UAT environment and update the status to *Waiting*.

[!Note]
>It is best practice that all batch jobs which will run with recurrence that are mission critical be created and run by the Admin account.  This should be a generic user such as erp@customer.com and not tied to a specific employees AAD account which could later be disabled when they leave the company.

## Open the environment to users
When the system is configured as you see fit, you can enable select users to access the environment.  By default all users except for the Admin and Microsoft Service Accounts are disabled.

To enable users visit:
* System administration -> Users -> **Users**. Enable the users you wish to have access to the UAT environment.  If there are many to enable this can be done quicker via the [Excel Add-In](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in#open-entity-data-in-excel-when-you-start-from-finance-and-operations).

## Community tools
Looking for more tools to help with preparing backup files from your developer environments?  Here are some other sources of information:
* [D365fo.Tools](https://github.com/d365collaborative/d365fo.tools/blob/development/docs/Import-D365Bacpac.md) provides many valuable tools created by the community
* [Community provided open source projects on GitHub](https://github.com/search?q=dynamics+365+finance+operations&s=stars)





