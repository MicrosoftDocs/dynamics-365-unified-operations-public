---

# required metadata

title: Configure and manage database logging
description: You can track changes to tables and fields in Dynamics 365 Human Resources with database logging.
author: twheeloc
ms.date: 12/15/2021
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Human Resources

---

# Configure and manage database logging

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can track changes to tables and fields in Dynamics 365 Human Resources with database logging. This article describes how to:

- Manage security and performance for database logging
- Set up database logging
- Clean up database logs

## Overview of database logging

Database logging tracks specific changes to Microsoft Dynamics 365 Human Resources tables and fields. These changes include inserting, updating, or deleting. Database logging stores a record of changes to tables or fields in the database log table.

The business uses of database logging include:

- Creating an audit record of changes to specific tables that contain sensitive information.
- Tracking single transactions. Database logging isn't intended for tracking automated transactions that run in batch jobs.

## Security for database logging

Database logs can contain sensitive data. Limit access to include only security roles that need access to the log data.

## Database logging and performance

While valuable from a business perspective, database logging can be expensive in resource use and management. The performance implications of database logging include:

- The database log table can grow quickly and cause an increase in the size of the database. Growth depends on the amount of logged data that you decide to keep. By default, the database log table maintains only 30 days of log data. 

- Database logging can adversely affect long-running automated processes, such as long-running data imports.

### Best practices

To improve performance, limit log entries by selecting specific fields to log instead of whole tables. To help maintain overall performance, database logging is limited to 20 tables.

> [!NOTE]
> Only updates can be logged for individual fields.

## Set up database logging

You can use the **Logging database changes** wizard to set up database logging. The wizard provides a flexible way to set up logging for tables or fields.

1. Go to **System administration > Links > Database > Database log setup**. Select **New** to start the **Logging database changes** wizard.
2. Select **Next**. 
3. On the **Tables and fields** page of the wizard, select the the tables and fields on which you want to enable database logging, and select **Next**.

   > [!Note]
   > Database logging is not available on all tables in the Human Resources database. Selecting **Show all tables** below the list expands the list of tables and fields to show all database tables for which database logging is available, but this will be a subset of the full list of database tables.

4. On the **Types of change** page of the wizard, select the data operations for which you want to track changes for each of the tables and fields, and select **Next**. See the table below for a description of the data operations that are available for logging.
5. On the **Finish** page, review the changes that will be made, and select **Finish**.

| Operation | Description |
| -- | -- |
| Track new transactions | Create a log for new records that are created in the table. |
| Update | Create a log for updates to table records, or updates to individually selected fields in the table. If you select to log updates for the table, then a log record is created each time an update is made to any field of any record on the table. If you select to log updates for specific fields, then a log record is created only when updates are made to those fields of table records. |
| Delete | Create a log for records deleted from the table. |
| Rename key | Create a log record when a table key is renamed. |


## Clean up database logs

You can delete all or part of the database logs, using the following options:

- Select all logs for a particular table.
- Select specific types of database log.
- Select a date and time that a log was created.

To set up database log cleanup, follow these steps: 

1. Go to **System administration > Links > Database > Database log**. Select **Clean up log**.
2. Under the **Records to include** header, select **Filter**.
3. Choose the method that will be used to select logs to delete. Enter one of the following options:

   - Table ID
   - Type of log
   - Created date and time

4. Use the **Database log cleanup** tab to determine when to run the log cleanup task. By default, database logs are available for 30 days.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
