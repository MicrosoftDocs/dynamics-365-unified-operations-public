---

# required metadata

title: Configure and manage database logging
description: You can track changes to tables and fields in Dynamics 365 Human Resources with database logging.
author: Darinkramer
manager: AnnBe
ms.date: 06/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Human Resources

---

# Configure and manage database logging

You can track changes to tables and fields in Dynamics 365 Human Resources with database logging. This topic describes how to:

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
2. Complete the wizard.

## Clean up database logs

You can delete all or part of the database logs, using the following options:

- Select all logs for a particular table.
- Select specific types of database log.
- Select a date and time that a log was created.

To set up database log cleanup, follow these steps: 

1. Go to **System administration > Links > Database > Database log**. Select **Clean up log**.

2. Choose a method of selecting logs to delete by entering one of the following options:

   - Table ID
   - Type of log
   - Created date and time

3. Use the **Database log cleanup** tab to determine when to run the log cleanup task. By default, database logs are available for 30 days.
