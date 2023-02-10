---
# required metadata

title: Migrate document attachments from Dynamics AX 2012
description: This article describes how to migrate document attachments from Microsoft Dynamics AX 2012.
author: ttreen 
ms.date: 04/26/2022
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

This article describes how to migrate document attachments from Microsoft Dynamics AX 2012.

## Background

In Dynamics AX 2012, attachments are stored in several locations, such as a file share, a database, or a local SharePoint server. The location for the attachments is set in the **Document Types** form for each file type.

In Dynamics 365 finance and operations, attachments are mostly stored in a private Azure Blob Storage location that is assigned to the environment. Alternatively, they are linked to a SharePoint online site that is under the customer's tenant.

Attachments will be available in Dynamics 365 after an upgrade from Dynamics AX 2012 only if they are migrated to the Dynamics AX 2012 database before the upgrade is done. A post-upgrade step then migrates them to the Blob Storage location.

## Migration options

To migrate document attachments from Dynamics AX 2012, you have two options. You can migrate them from a database location or a file share location.

> [!NOTE]
> Currently, migration of attachments from a local SharePoint site isn't supported.

### Option 1: Migrate attachments from a database location

Attachments that are already set up to be stored in the **DocuValue** table in the Dynamics AX 2012 database require no action.

### Option 2: Migrate attachments from a file share location

Attachments that are stored in a file share in the Dynamics AX 2012 environment must be migrated to the Dynamics AX 2012 database. For more information, see [Move Documents from Shared Location to Database](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/AX2012DataUpgrade/MoveDocumentsToDatabase).

## Post-upgrade steps

After the upgrade is completed, existing documents or attachments that are stored in the Dynamics AX 2012 database should be migrated to Blob Storage.

To do this migration, on the **Document management parameters** page, on the **Migrate files** tab, select **Migrate files**. This operation isn't critical, because document management can still access files that are stored in the database. However, the files can use considerable database storage, and retrieval from the database is less efficient. The file migration process will migrate all possible database files to Blob Storage. If any failures occur, the process will report them but continue the migration. If any errors are reported, try to run the file migration process again.

> [!NOTE]
> During the production go-live phase, don't migrate the attachments until you've completed the [self-service database refresh process](../database/database-refresh.md#self-service-database-refresh) to copy your upgraded database from the sandbox environment to your production environment. Otherwise, the attachments won't be available in the production environment, because they were migrated to the sandbox Blob Storage location instead of the production location.

If the file migration process can't be completed without failure, the files that are stored in the database might be corrupted. In this case, Microsoft won't be able to repair the files. However, you can request that a non–business critical support case be opened to enable conversion of the attachments to note records. Those note records will retain any previous notes and also the names of the files that were stored in the database. The files themselves can't be recovered.
