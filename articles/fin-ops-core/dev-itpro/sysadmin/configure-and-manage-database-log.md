# Configure and manage database logging 


This article describes database logging, including how to manage security and performance, how to set it up, and how to clean up database logs.

## Overview of database logging

Database logging is a means of tracking specific types of changes to Microsoft Dynamics Finance and Operations tables and fields. Changes that can be tracked include insert, update, delete or rename key. When you configure logging for a table or field, a record of any change to that table or field is stored in the database log table, sysdatabaselog, in the Microsoft Dynamics Finance and Operations database.

The business uses of database logging include the following:

  - Creating an auditable record of changes to specific tables that contain sensitive information.

  - Monitoring the use of electronic signatures.
    
    By default, all transactions that have been signed with electronic signatures are logged.

Database logging is intended to track single transactions. It is not intended for tracking automated transactions running in batch jobs.

## Security for database logging

Database logs can contain sensitive data. By default, any user who has database access can query the database log table (sysdatabaselog) by using Business Connector, X++, or alerts, or by querying the database directly. To protect data, restrict permissions on the sysdatabaselog table.

## Database logging and performance

Database logging, although it can be valuable from a business perspective, can be expensive with regard to resource use and management. The performance implications of database logging include the following:

  - The database log table can grow quickly and cause an increase in the size of the database. The amount of growth depends on the amount of logged data that you decide to retain.

  - When logging is enabled for a particular transaction type, each instance of that transaction type causes multiple records to be written to the SQL Server transaction log file. Specifically, one record is written for the initial transaction, and one record logs the transaction in the database log table. The transaction log file will grow more quickly and might require additional maintenance.

  - Database logging can adversely affect long-running automated processes, such as inventory close, BOM calculations, master planning, and long-running data imports.

  - When logging is enabled for a table, all database operations that would be set-based are downgraded to row-based operations. For example, if you are logging inserts for a table, each insert is performed as a row-based insert.

Our recommended practices include the following:

  - Create a plan for how long you will retain logged data, and how you will archive or delete data.

  - Limit log entries, and improve performance by selecting specific fields to log instead of whole tables.
    

    > [!NOTE]
    > <P>Only updates can be logged for individual fields.</P>



  - Consider increasing how often you perform SQL Server transaction log backups after you have configured database logging.

## Set up database logging

You can use the **Logging database changes** wizard to set up database logging. The wizard provides a flexible way to set up logging for tables or fields.

1.  Click **System administration** \> **Setup** \> **Database** \> **Database log setup**. Click **New** to start the **Logging database changes** wizard.

2.  Complete the wizard.

## Clean up database logs

You can delete database logs. You can select all logs for a particular table, specific types of database log, or a date and time that a log was created to delete.


> [!NOTE]
> <P>To enable auditing, records that have been signed cannot be deleted from logs. For more information, see <A href="electronic-signature-overview.md">Electronic signature overview</A>.</P>



1.  Click **System administration** \> **Inquiries** \> **Database** \> **Database log**. Click **Clean up log**.

2.  Choose a method of selecting logs to delete by entering the table ID that they refer to, or the type of log, or the created date and time.

3.  Use the **Database log cleanup** tab to determine when to run the log cleanup task.

  ## Consistency Check for database log triggers


