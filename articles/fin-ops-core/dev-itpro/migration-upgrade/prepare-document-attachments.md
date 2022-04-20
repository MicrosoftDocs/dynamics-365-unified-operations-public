---
# required metadata

title: Prepare document attachments
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Prepare document attachments

[!include[banner](../includes/banner.md)]

This topic provides information on how to migrate document attachments from Microsoft Dynamics AX 2012.

## Background
In Microsoft Dynamics AX 2012 attachments were stored in a number of locations: a file share, database or in a local Microsoft SharePoint server. 

The location for the attachments was set within the **Document Types** form for each file type.  

In Microsoft Dynamics 365 Finance and Operations, the attachments are mostly stored in a private Azure Blob storage location assigned to the environment, or linked to a Microsoft Sharepoint On-Line site that is under the customer's own tenant. 

In order for the attchements to be avaiable in D365 after the upgrade they must be migrated to the AX 2012 database prior to the upgrade and then a post upgrade step migrates these into the Azure blob storage. 

## Migration Options

### Database Location
Attachements already set to be stored in the AX 2012 database, table DocuValue, require no action

### File Share Location
Attachments that are stored in a file share on the AX 2012 environment need to be migrated to the database. Please see the following GitHub project to migrate these:
[Move Documents from Shared Location to Database](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/AX2012DataUpgrade/MoveDocumentsToDatabase)

### Local SharePoint Location
At this point there is no supported approach to migrate attachments from a local SharePoint site.

## Post Upgrade Steps
Once the upgrade is completed, existing documents or attachments that are stored in the database should be migrated to Microsoft Azure Blob storage. To complete this migration, use the **Migrate files** button on the **Migrate files** tab on the **Document management parameters page**. This operation is not critical as document management can still access file stored in the database, but the files can take considerable database storage and the retrieval is less efficient. The file migration process will migrate all possible database files to Microsoft Azure Blob storage, reporting on any failures and continuing. If any errors are reported, attempt running the file migration process again.

> [!NOTE] 
> When doing the Production Go-Live, do not migrate the attachments until you have completed the [Self-service database refresh process](../database/database-refresh.md#self-service-database-refresh) to copy your upgraded database from the sandbox environment into your production environment.Otherwise the attachments will not be available in production as they were migrated to the Sandbox Azure Blob storage rather than the production one.

If the file migration process isn’t able to complete without failure, this may be that the files stored in the database are corrupt, which Microsoft is unable to repair. If this is the case, you can request a non-business critical support case be opened to enable conversion of the attachments into note records, which will retain any previous notes as well as the names of the files that were stored in the database. Note that the files themselves cannot be recovered.


