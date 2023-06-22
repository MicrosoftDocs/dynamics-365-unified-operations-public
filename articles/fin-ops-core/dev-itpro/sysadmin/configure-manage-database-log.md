---
title: Configure database logging
description: This article describes how to set up database logging, how to manage security and performance, and how to clean up database logs.
author: Peakerbl
ms.date: 06/11/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 22a56b7d-4e07-4161-8416-0cac4a0b65a2
---

# Configure database logging

[!include [banner](../includes/banner.md)]

Database logging provides a way to track specific types of changes to the tables and fields in Finance and Operation apps. Changes that can be tracked include insert, update, delete, and rename key operations. When you configure logging for a table or field, a record of every change to that table or field is stored in the database log table, **sysdatabaselog**, in the environment database.

Database logging can be used for these purposes:

- Create an auditable record of changes to specific tables that contain sensitive information.
- Monitor the use of electronic signatures. By default, all transactions that have been signed by using electronic signatures are logged.

Database logging is intended to track individual transactions. It isn't intended to track automated transactions that are run in batch jobs.

## Security for database logging

Database logs can contain sensitive data. By default, any user who has database access can query the database log table (**sysdatabaselog**) by using X++ or alerts, or by querying the database directly. To help protect data, you should restrict permissions on the **sysdatabaselog** table for on-premises deployments.

## Database logging and performance

Although database logging can be valuable from a business perspective, it can be expensive with regard to resource use and management. Here are some of the performance implications of database logging:

- The database log table can grow quickly and can increase the size of the database. The amount of growth depends on the amount of logged data that you decide to retain.
- When logging is turned on for a transaction type, each instance of that transaction type causes multiple records to be written to the Microsoft SQL Server transaction log file. Specifically, one record is written for the initial transaction, and one record logs the transaction in the database log table. Therefore, the transaction log file will grow more quickly and might require additional maintenance.
- Database logging can adversely affect long-running automated processes, such as inventory close, calculations for bills of materials (BOMs), master planning, and long-running data imports.
- When logging is turned on for a table, all set-based database operations are downgraded to row-based operations. For example, if you're logging inserts for a table, each insert is done as a row-based insert.
- The **Database Log** report will display a maximum of 10,000 records.

Here are some practices that Microsoft recommends:

- Create a plan for how long you will retain logged data, and how you will archive or delete data.
- Limit log entries, and help improve performance by selecting specific fields to log instead of whole tables.

    > [!NOTE]
    > Only updates can be logged for individual fields.

- After you configure database logging, consider increasing the frequency of backups of the SQL Server transaction log.

    > [!NOTE]
    > This recommendation applies only to on-premises deployments that have a local instance of SQL Server.

## Set up database logging

You can use the **Logging database changes** wizard to set up database logging. This wizard provides a flexible way to set up logging for tables or fields.

1. Go to **System administration** \> **Setup** \> **Database log** \> **Database log setup**.
2. Select **New** to open the **Logging database changes** wizard.
3. Complete the wizard.

## Clean up database logs

You can delete database logs as required. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created.

> [!NOTE]
> Records that have been electronically signed can't be deleted from logs.

1. Go to **System administration** \> **Inquiries** \> **Database** \> **Database log**.
2. Select **Clean up log**.
3. Select the method that should be used to select the logs that are deleted. Enter the table ID that the logs refer to, the type of log, or the creation date and time.
4. Use the **Database log cleanup** tab to specify when the log cleanup task should be run.

## Consistency check for database log triggers

In Platform update 34, functionality for a consistency check was added. The consistency check is run as part of the **Database log** wizard. It's run after you select **Finish** or after you select **Consistency check** on the **Database log setup** page.

The consistency check will re-create any missing database log triggers. It will also drop any "orphaned" database log triggers that no corresponding configuration is found for. In this way, the consistency check quickly detects and fixes any inconsistencies between the current configuration and the database triggers that are used to implement the logging functionality.

1. Go to **System administration** \> **Inquiries** \> **Database** \> **Database log**.
2. On the **Database log** page, select **Consistency check**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
