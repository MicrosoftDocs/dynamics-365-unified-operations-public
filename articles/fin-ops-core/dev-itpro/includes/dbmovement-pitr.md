To restore the database of a standard user acceptance test (UAT) environment to a previous point-in-time, follow the steps outlined below:

1. Go to your target sandbox **Environment Details** page, and select the **Maintain** > **Move database** menu option.
2. Select the **Point-in-time restore** option and choose a point-in-time.
3. Note the warnings. Review the list of data elements that are not copied over from the previous point-in-time.
4. The restore operation will begin immediately.

> [!IMPORTANT]
> Restoring the database in production to a previous point-in-time is not a common lifecycle operation and could result in the following issues:
> - **Large downtime for the production environment**. Point-in-time restore (PITR) may take multiple hours, depending on the database size.
> - **SQL data loss**. SQL data loss would depend on how far back the PITR request is made.
> - **Breaking of the SQL database [chain of available restore points](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public/blob/main/articles/fin-ops-core/dev-itpro/database/database-point-in-time-restore.md#breaking-the-chain-of-available-restore-points)**.

To restore the database of a production environment to a previous point-in-time, follow the steps outlined below:

1. Go to your target production **Environment Details** page, and select the **Maintain** > **Move database** menu option.
2. Select the **Point-in-time restore** option and choose a point-in-time.
3. Note the warnings. Review the list of data elements that are not copied over from the previous point-in-time.
4. The restore operation will begin immediately. 

