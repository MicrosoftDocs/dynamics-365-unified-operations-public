---
title: Golden configuration promotion
description: Learn about a golden configuration promotion for finance and operations, prerequisites and what to know before starting.
author: LaneSwenka
ms.author: laswenka
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: IT Pro, Developer
ms.search.region: Global 
ms.search.validFrom: 2019-01-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.3
---

# Golden configuration promotion

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that you can use as part of data application lifecycle management (DataALM). "Golden configuration" refers to a common practice among customers and partners in the Microsoft Dynamics ecosystem, where a developer environment is used as a configuration store. In this approach, implementation projects store finalized global and company-specific settings in a database that can later become a baseline for Conference Room Pilots, mock go-lives, and go-lives. This tutorial shows how to prepare a golden configuration database and hydrate a target user acceptance testing (UAT) environment.

In this tutorial, you learn how to:

> [!div class="checklist"]
>
> - Prepare the golden configuration database for Microsoft Azure SQL Database.
> - Run the import to the target UAT environment.
> - Copy the UAT environment into a production environment.

As an example of this scenario, a customer who isn't yet live is preparing for a Conference Room Pilot, mock go-live, or go-live. This scenario supports promoting a baseline golden database from a developer environment to a UAT environment and eventually to production.

## Prerequisites

To complete this tutorial, you must have a developer environment that's deployed with a database curated as a golden configuration database. You must also have at least one standard UAT environment deployed and, optionally, a production environment.

The developer environment must run the same *application version* as the target UAT environment. In addition, the *platform version* of the developer environment must be earlier than or the same as the platform version in the target UAT environment.

## Before you begin

### Supported SQL Server collation

The only supported collation for databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Make sure that your Microsoft SQL Server and database collations in development environments are set to this value. Also make sure that any configuration environments that you publish to sandbox use this collation.

### Document the values of encrypted fields

You can't import encrypted and environment-specific values into a new environment. After you complete the import, you must reenter some data from your source environment in your target environment.

Because of a technical limitation that's related to the certificate used for data encryption, values stored in encrypted fields in a database are unreadable after that database is imported into a new environment. Therefore, after an import, you must manually delete and reenter values stored in encrypted fields. New values entered in encrypted fields after an import are readable. The following fields are affected. The field names are given in *Table.Field* format.

| Field name                                               | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | The Data Import/Export Framework (DIXF) uses this field. |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field is obsolete since Microsoft Dynamics AX 7.0 (February 2016). It previously appeared on the **All worker actions** page (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMPTPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | Application Object Server (AOS) uses this field internally. You can ignore it. |
| SysOAuthUserTokens.EncryptedRefreshToken                 | AOS uses this field internally. You can ignore it. |

### If you're running Commerce components, document encrypted and environment-specific values

The values on the following pages are either environment-specific or encrypted in the database. Therefore, all the imported values are incorrect.

- Payments services (**Accounts receivable** &gt; **Payments setup** &gt; **Payments services**)
- Hardware profiles (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**)

## Create a copy of the source database

Back up the source database by using SSMS. Right-click the source database, and select **Tasks** > **Backup**. When the backup finishes, right-click the **Databases** folder in the SSMS navigation window, and select **Restore database**. Choose the backup that you just made, but give the target database a new name such as AXDB_CopyForExport.

## Prepare the database

Run the following script against the AxDB\_CopyForExport database that you created in the previous section. This script makes the following changes:

- Sets the **SysGlobalConfiguration** flag to inform the application that the database is Azure-based.
- Removes a reference to tempDB in the XU\_DisableEnableNonClusteredIndexes procedure. Azure SQL databases don't allow references to tempDB. The database synchronization process re-creates the reference later.
- Drops users, because Microsoft Windows users aren't allowed in Azure SQL databases. You must re-create other users later so that they're correctly linked to the appropriate sign-in on the target server.
- Clears encrypted hardware profile merchant properties.

A successful export and import of the database requires all these changes.

```sql
update sysglobalconfiguration
set value = 'SQLAZURE'
where name = 'BACKENDDB'

update sysglobalconfiguration
set value = 1
where name = 'TEMPTABLEINAXDB'

drop procedure if exists XU_DisableEnableNonClusteredIndexes
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

--Tidy up the batch server config from the previous environment
DELETE FROM SYSSERVERCONFIG

--Tidy up server sessions from the previous environment
DELETE FROM SYSSERVERSESSIONS

--Tidy up printers from the previous environment
DELETE FROM SYSCORPNETPRINTERS

--Tidy up client sessions from the previous environment
DELETE FROM SYSCLIENTSESSIONS

--Tidy up batch sessions from the previous environment
DELETE FROM BATCHSERVERCONFIG

--Tidy up batch server to batch group relation table
DELETE FROM BATCHSERVERGROUP

-- Clear encrypted hardware profile merchant properties
update dbo.RETAILHARDWAREPROFILE set SECUREMERCHANTPROPERTIES = null where SECUREMERCHANTPROPERTIES is not null
```

## Export the database from SQL Server

Download sqlpackage .NET Core for Windows from [Get sqlpackage .NET Core for Windows](/sql/tools/sqlpackage-download#get-sqlpackage-net-core-for-windows). Open a **Command Prompt** window, and run the following commands from the sqlpackage .NET Core folder.

```Console
cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin\
SqlPackage.exe /a:export /ssn:localhost /sdn:<database to export> /tf:D:\Exportedbacpac\<filename>.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false /SourceTrustServerCertificate:True
```

Here's an explanation of the parameters:

- **ssn (source server name)** – The name of the SQL Server to export from. For the purposes of this article, the name is always **localhost**.
- **sdn (source database name)** – The name of the database to export.
- **tf (target file)** – The path and name of the file to export to. The folder should already exist, but the export process creates the file.

## Import the database

Upload the .bacpac file that you created in the previous step to the **Database backup** section in your Lifecycle Services project's Asset Library. Then, begin the import. The target UAT environment's databases are overwritten by the golden configuration database.

> [!NOTE]
> Certain elements aren't copied as part of the import database step. In the golden configuration scenario, this limitation affects things such as email addresses and Print Management setup. Ideally, you populate these settings as part of the master data migration in the steps described later. These settings shouldn't be part of the golden configuration database.

[!include [dbmovement-import](../includes/dbmovement-import.md)]

## Perform master data migration

Now that the UAT environment is hydrated with the golden configuration, you can begin to migrate master data. You can perform this data migration by [using data entities](../data-entities/develop-entity-for-data-migration.md). Complete your data migration activities before you copy the UAT environment to production, because you have access to the database in the UAT environment for troubleshooting.  

> [!IMPORTANT]
> Files stored in Azure blob storage aren't copied from UAT to production in the next step. This limitation includes document attachments and custom Microsoft Office templates. If your go-live requires attachments or custom templates, import those items in the production environment directly.

## Copy the sandbox database to production

When you're ready to do a mock go-live or actual go-live, you can copy the UAT environment to production. This process is often referred to as *cutover*. Do a cutover more than one time before your actual go-live. In this way, you can get detailed time estimates for each step of the process.

Determine the **Environment type** of your production environment and follow the relevant steps accordingly.

### Self-service

1. In Lifecycle Services, open the **Full details** for the production environment to load the **Environment page**.
1. In the **Maintain** menu, select **Move database**.
1. For the operations options, select **Refresh database**.
1. In the **Source environment**, select the sandbox where your golden configuration is. Note the important instructions found on the [Refresh database page](database-refresh.md) for this operation.
1. Select the check box to confirm that you understand this operation overwrites the production database. The operation starts immediately after submitting the request.

### Microsoft-managed

1. In Lifecycle Services, on the project home page, select **Service requests**.
1. On **Service requests**, select **Add**, and then select **Sandbox to Production**.
1. In **Sandbox to Production**, follow these steps:

    1. In **Source environment name**, select the sandbox environment to copy the database from.
    1. Set the **Preferred downtime start date** and **Preferred downtime end date**. The end date must be at least four hours after the start date. To help ensure that resources are available to run the request, submit your request at least 24 hours before your preferred downtime window.
    1. Select the check boxes at the bottom to agree to the terms.

> [!IMPORTANT]
> Every database refresh creates a new database that resets the **Point-in-time-restore** chain of restore points.

## Reconfigure environment specific settings

After the refresh finishes, use the **Sign off** button in Lifecycle Services to close out of the operation. You can then start to configure the environment-specific settings.

First, sign in to the environment by using the admin account that you find on the **Environment details** page in Lifecycle Services. Here are some typical areas of reconfiguration. You might require more reconfiguration, based on your setup and the independent software vendor (ISV) solutions that are installed:

- **System administration** \> **Setup** \> **Batch groups:** Add the various AOS instances to the batch server groups that you require.
- **System administration** \> **Setup** \> **Entity Store:** Update the various entities that you require for Microsoft Power BI reporting.
- **System administration** \> **Setup** \> **System parameters:** Reconnect the environment to the Lifecycle Services Help configuration for task guides.
- **System administration** \> **Setup** \> **Email** \> **Email parameters:** Enter the Simple Mail Transfer Protocol (SMTP) settings if you use email in your UAT environment.
- **System administration** \> **Setup** \> **Integration configuration** \> **Azure storage account connection string:** Enter the storage account string.
- **System administration** \> **Setup** \> **System Parameters:** On the **Document connections** tab enter the Azure Key and Application Secret.
- **System administration** \> **Inquiries** \> **Batch jobs:** Select the jobs that you want to run in your UAT environment, and update the status to **Waiting**.

> [!NOTE]
> As a best practice, create and run all mission-critical batch jobs that run with recurrence by using the admin account. Use a generic user such as `erp@customer.com`. Don't link the admin to a specific employee's Microsoft Entra account, because that account might be disabled later if the employee leaves the company.

## Open the environment to users

The user configuration in Sandbox is copied as-is to Production environment. Configure the users in the Sandbox environment before copying to Production to avoid any unwanted access after copying is completed.

After copying is completed, if you want to update user access, go to **System administration** > **Users** > **Users**, and enable or disable the users to manage the access to Production environment. If many users must be enabled or disabled, you can complete this task more quickly by using the [Microsoft Excel add-in](../office-integration/use-excel-add-in.md#open-entity-data-in-excel-when-you-start-from-a-finance-and-operations-app).

## Community tools

Are you looking for more tools to help you prepare backup files from your developer environments? Here are some other sources of information:

- [D365fo.Tools](https://github.com/d365collaborative/d365fo.tools/blob/development/docs/Import-D365Bacpac.md) provides many valuable tools that the community creates.
- [Community-provided open source projects on GitHub](https://github.com/search?q=dynamics+365+finance+operations&s=stars).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
