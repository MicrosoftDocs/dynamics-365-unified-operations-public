---
# required metadata

title: Migrate document attachments from Dynamics AX 2012
description: This topic describes how to migrate document attachments from Microsoft Dynamics AX 2012.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Migrate document attachments from Dynamics AX 2012

[!include[banner](../includes/banner.md)]

This topic describes how to migrate document attachments from Microsoft Dynamics AX 2012.

## Background

In Dynamics AX 2012, attachments are stored in a number of locations, such as a file share, database, or local Microsoft SharePoint server. The location for the attachments was set within the **Document Types** form for each file type.  

In Microsoft Dynamics 365 Finance + Operations, attachments are mostly stored in a private Azure Blob Storage location assigned to the environment, or linked to a Sharepoint online site that is under the customer's tenant. 

For attachments to be available in Dynamics 365 after the upgrade from Dynamics AX 2012, they must be migrated to the Dynamics AX 2012 database prior to the upgrade. A post-upgrade step then migrates the attachments into the Azure Blob Storage location. 

## Migration options

To migrate document attachments from Dynamics AX 2012, you have the following options.

###  Migrate attachments from a database location

Attachments already set to be stored in the Dynamics AX 2012 database table **DocuValue** require no action.

###  Migrate attachments from a file share location

Attachments that are stored in a file share on the Dynamics AX 2012 environment must be migrated to the Dynamics AX 2012 database. For more information, see [Move Documents from Shared Location to Database](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/AX2012DataUpgrade/MoveDocumentsToDatabase).

### Migrate attachments from a local SharePoint site

Currently there is no supported approach to migrate attachments from a local SharePoint site.

## Post-upgrade steps

Once the upgrade is completed, existing documents or attachments that are stored in the Dynamics AX 2012 database should be migrated to Microsoft Azure Blob storage. 

To complete this migration, on the **Document management parameters page** select **Migrate files** on the **Migrate files** tab. This operation is not critical since document management can still access files stored in the database, but the files can use considerable database storage and the retrieval from the database is less efficient. The file migration process will migrate all possible database files to Microsoft Azure Blob storage, reporting on any failures while continuing the migration. If any errors are reported, try running the file migration process again.

> [!NOTE] 
> When doing the production go-live phase, do not migrate the attachments until you have completed the [Self-service database refresh process](../database/database-refresh.md#self-service-database-refresh) to copy your upgraded database from the sandbox environment into your production environment. Otherwise the attachments will not be available in production since they were migrated to the Sandbox Azure Blob Storage location rather than the production location.

If the file migration process isn't able to complete without failure, this may be because the files stored in the database are corrupt. In this case, Microsoft will not be able to repair the files. If this is the case, Microsoft will not be able to repair the files but you can request that a non-business critical support case be opened to enable conversion of the attachments into note records. These note records will retain any previous notes as well as the names of the files that were stored in the database. The files themselves cannot be recovered.


