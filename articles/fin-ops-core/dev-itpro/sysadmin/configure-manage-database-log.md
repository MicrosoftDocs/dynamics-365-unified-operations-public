---
# required metadata

title: Configure and manage database logging
description: This topic provides information about database logging, including how to set it up, how to manage security and performance, and how to clean up database logs.
author: hasaid
manager: AnnBe
ms.date: 03/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 57201
ms.assetid: 22a56b7d-4e07-4161-8416-0cac4a0b65a2
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure and manage database logging

[!include [banner](../includes/banner.md)]

Database logging is a way to track specific types of changes to the tables and fields in Dynamics 365 Finance and Operation apps. Changes that can be tracked include insert, update, delete, or rename key. When you configure logging for a table or field, a record of any change to that table or field is stored in the database log table, **sysdatabaselog** in the environment database.

Database logging can be used to:

  - Create an auditable record of changes to specific tables that contain sensitive information.
  - Monitor the use of electronic signatures. By default, all transactions that have been signed with electronic signatures are logged.

Database logging is intended to track single transactions. It is not intended to track automated transactions that run in batch jobs.

## Security for database logging

Database logs can contain sensitive data. By default, any user who has database access can query the database log table (**sysdatabaselog**) by using  X++, alerts, or by querying the database directly. To protect data, restrict permissions on the **sysdatabaselog** table for on-premises deployments.

## Database logging and performance

Although it can be valuable from a business perspective, database logging can be expensive with regard to resource use and management. The performance implications of database logging include the following:

  - The database log table can grow quickly and increase the size of the database. The amount of growth depends on the amount of logged data that you decide to retain.
  - When logging is enabled for a particular transaction type, each instance of that transaction type causes multiple records to be written to the SQL Server transaction log file. Specifically, one record is written for the initial transaction, and one record logs the transaction in the database log table. The transaction log file will grow more quickly and might require additional maintenance.
  - Database logging can adversely affect long-running automated processes, such as inventory close, BOM calculations, master planning, and long-running data imports.
  - When logging is enabled for a table, all database operations that would be set-based are downgraded to row-based operations. For example, if you are logging inserts for a table, each insert is performed as a row-based insert.

Our recommended practices include the following:

  - Create a plan for how long you will retain logged data, and how you will archive or delete data.
  - Limit log entries, and improve performance by selecting specific fields to log instead of whole tables.

    > [!NOTE]
    > Only updates can be logged for individual fields.

  - Consider increasing how often you perform SQL Server transaction log backups after you have configured database logging.
  
      > [!NOTE]
      > This is applicable only to on-premises deployments with a local SQL Server.

## Set up database logging

You can use the **Logging database changes** wizard to set up database logging. The wizard provides a flexible way to set up logging for tables or fields.

1. Go to **System administration** \> **Setup** \> **Database** \> **Database log setup**. 
2. Select **New** to start the **Logging database changes** wizard.
3. Complete the wizard.

## Clean up database logs

You can delete database logs when needed. You can select to delete logs for a particular table, specific types of database log, or delete based on the date and time that a log was created.


> [!NOTE]
> Records that have been electronically signed can't be deleted from logs.


1. Go to **System administration** \> **Inquiries** \> **Database** \> **Database log**. 
2. Select **Clean up log**.
3. Choose a method of selecting logs to delete by entering the table ID that they refer to, the type of log, or the created date and time.
4. Use the **Database log cleanup** tab to determine when to run the log cleanup task.

## Consistency check for database log triggers

As of **Platform Update 34**, a consistency check functionality has been added. The check is executed as part of the Database log wizard and will be executed after you select **Finish** or through a consistency check button in the **Database log setup** page.
Consistency check will recreate any missing database log trigger and drop any orphaned database log trigger for which no corresponding configuration is found.
The new functionality will quickly detect and fix any inconsistency between the current configuration and the database triggers used to implement the logging functionality.

1. Go to **System administration** \> **Inquiries** \> **Database** \> **Database log**.
2. On the **Database log** page, then select **Consistency check**.
