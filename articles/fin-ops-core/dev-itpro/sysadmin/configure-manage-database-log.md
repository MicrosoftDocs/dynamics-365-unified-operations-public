---
title: Configure database logging
description: Learn about how to set up database logging, how to manage security and performance, and how to clean up database logs.
author: Peakerbl
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 22a56b7d-4e07-4161-8416-0cac4a0b65a2
---

# Configure database logging

[!include [banner](../includes/banner.md)]

Database logging provides a way to track specific types of changes to the tables and fields in Finance and Operation apps. You can track changes such as insert, update, delete, and rename key operations. When you configure logging for a table or field, the system stores a record of every change to that table or field in the database log table, **sysdatabaselog**, in the environment database.

You can use database logging to:

- Create an auditable record of changes to specific tables that contain sensitive information.
- Monitor the use of electronic signatures. By default, the system logs all transactions that use electronic signatures.

Database logging is designed to track individual transactions. It isn't designed to track automated transactions that run in batch jobs.

## Security for database logging

Database logs can contain sensitive data. By default, any user who has database access can query the database log table (**sysdatabaselog**) by using X++ or alerts, or by querying the database directly. To help protect data, restrict permissions on the **sysdatabaselog** table for on-premises deployments.

## Database logging and performance

Although database logging can be valuable from a business perspective, it can use significant resources and add to management complexity. Here are some of the performance implications of database logging:

- The database log table can grow quickly and can increase the size of the database. The amount of growth depends on the amount of logged data that you decide to retain.
- When you turn on logging for a transaction type, each instance of that transaction type writes multiple records to the Microsoft SQL Server transaction log file. Specifically, one record is written for the initial transaction, and one record logs the transaction in the database log table. Therefore, the transaction log file grows more quickly and might require extra maintenance.
- Database logging can adversely affect long-running automated processes, such as inventory close, calculations for bills of materials (BOMs), master planning, and long-running data imports.
- When you turn on logging for a table, all set-based database operations downgrade to row-based operations. For example, if you're logging inserts for a table, each insert is done as a row-based insert.
- The **Database Log** report displays up to 10,000 records.

Here are some recommended practices:

- Create a plan for how long you will retain logged data, and how you will archive or delete data.
- Limit log entries and help improve performance by selecting specific fields to log instead of whole tables.

    > [!NOTE]
    > You can log only updates for individual fields.

- After you configure database logging, consider increasing the frequency of backups for the SQL Server transaction log.

    > [!NOTE]
    > This recommendation applies only to on-premises deployments that have a local instance of SQL Server.

## Set up database logging

Use the **Logging database changes** wizard to set up database logging. This wizard provides a flexible way to set up logging for tables or fields.

1. Go to **System administration** > **Setup** > **Database log** > **Database log setup**.
1. Select **New** to open the **Logging database changes** wizard.
1. Complete the wizard.

## Clean up database logs

You can delete database logs as needed. You can delete logs for specific tables, delete specific types of database logs, or delete logs based on the date and time when they were created.

> [!NOTE]
> You can't delete records that are electronically signed from logs.
> Admin must set up a job per company to clean up database logs.

1. Go to **System administration** > **Inquiries** > **Database** > **Database log**.
1. Select **Clean up log**.
1. Select the method to use for selecting the logs to delete. Enter the table ID that the logs refer to, the type of log, or the creation date and time.
1. Use the **Database log cleanup** tab to specify when the log cleanup task should run.

## Consistency check for database log triggers

In Platform update 34, Microsoft added functionality for a consistency check. The **Database log** wizard runs the consistency check after you select **Finish** or **Consistency check** on the **Database log setup** page.

The consistency check re-creates any missing database log triggers. It also drops any orphaned database log triggers when no corresponding configuration is found. By using this process, the consistency check quickly detects and fixes any inconsistencies between the current configuration and the database triggers that implement the logging functionality.

1. Go to **System administration** > **Inquiries** > **Database** > **Database log**.
1. On **Database log**, select **Consistency check**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
