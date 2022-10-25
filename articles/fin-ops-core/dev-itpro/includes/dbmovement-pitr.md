To restore the database of a standard user acceptance test (UAT) environment to a previous point-in-time, follow the steps outlined below:

1. Go to your target sandbox **Environment Details** page, and select the **Maintain** > **Move database** menu option.
2. Select the **Point-in-time restore** option and choose a point-in-time.
3. Note the warnings. Review the list of data elements that are not copied over from the previous point-in-time.
4. The restore operation will begin immediately.

[!IMPORTANT] Restoring the database in production to a previous point-in-time (PITR) is not a common lifecyle operation and it could result into the following
1. Large downtime for production environment since PITR could take multiple hours based on the database size
2. SQL data loss based on how far back point-in-time the request is made
3. It would break the SQL database [chain of avaliable restore points](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public/blob/main/articles/fin-ops-core/dev-itpro/database/database-point-in-time-restore.md#breaking-the-chain-of-available-restore-points)

To restore the database of a production environment to a previous point-in-time, follow the steps outlined below:

1. Go to your target production **Environment Details** page, and select the **Maintain** > **Move database** menu option.
2. Select the **Point-in-time restore** option and choose a point-in-time.
3. Note the warnings. Review the list of data elements that are not copied over from the previous point-in-time.
4. The restore operation will begin immediately. 

