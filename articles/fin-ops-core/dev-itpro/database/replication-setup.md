---
# required metadata

title: Replication setup
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: sarvanisathish
ms.date: 04/13/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sarvanis
ms.search.validFrom: 2021-04-30
---

# Replication setup

[!include[banner](../includes/banner.md)]

Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency. All this migration/copying happens with the source system online i.e. no need of AX Service downtime during the replication process. In the **Finance and Operations Online Database Migration Toolkit** we use transactional replication, this typically used in server-to-server scenarios that require high throughput, including improving scalability and availability.

The **Finance and Operations Online Database Migration Toolkit** can be downloaded from the LCS Portal under Shared Library   Model (Assert Type)

## Prerequisites

-	Source SQLServer should have enabled/installed replication feature. To check whether replication is enabled, execute the below SQL Secript.

     ```sql
     -- If @installed is 0, replication must be added to the SQL Server installation. 
    USE master;
    GO  
    DECLARE @installed int;  
    EXEC @installed = sys.sp_MS_replication_installed;  
    SELECT @installed; 
     ```

-	SQL Agent should be running in the source database server.

-	SA Authentication: User should have DB_Owner privilege in Source Database & Target Database. In Source Database, the user should have access to masterDb and sourceDb

-	Update the target firewall by allow-listing the source IP. This can be done via LCS portal and this allows only for 8Hrs. After allow-listing execute this below sp in the target database to have access more than 8 Hrs.

    To reate database-level firewall setting for IP a.b.c.d:
  
     ```sql
     EXECUTE sp_set_database_firewall_rule N'AX 2012 Upgrade', 'a.b.c.d', 'a.b.c.d'; 
     ```
- To Optimize the Replication Latency/Performance below are the few fine-tuned distributors parameters.
    1. MaxBcpThreads
    2. NumberOfPublishers
    3. Distributor DB paths

- Stop the AOS Service in the target environment, so that the target data base will get replicated smooth/fast. Running the AOS in the target might cause slowdown the replication process. Sometimes it may cause Schema Lock (or) deadlock in the replication process.

- When Setting up Distributor:
    The script creates a Database in the Source Server. So, make sure you have enough space (Recommended is minimum it should have the size of the source database). In params.json, you can specify the Distributor database path, so this database can be created in the specified path.

- Update params.xml

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
	<! -- Database replication parameters for an AX 2012 to Microsoft Dynamics 365 for Operations upgrade -->
	<Config>
   	  <!-- Edit the properties in this section for your source AX 2012 database -->
    	 <SourceDatabase>
           	     <Server>SQLINSTANCE\SQLSERVERNAME</Server>
           	     <Database>MicrosoftDynamicsAX</Database>
              	  <UserName>ReplicationUser</UserName>
              	  <Password>********************</Password>
    	 </SourceDatabase>
    	 <!-- Edit the properties in this section for your target D365 database -->
    	 <TargetDatabase>
              	  <Server>dbmigration.database.windows.net</Server>
             	   <Database>dbms-prod</Database>
             	   <UserName>axdbadmin</UserName>
             	   <Password>*******************</Password>
     	</TargetDatabase>
    	 <!-- Edit the properties in this section for your local SQL replication settings -->
     	<SQLReplicationSettings>
		<!-- ensure you have enough space in the drive/path -->
		<SnapShotWorkingDir>D:\SQLServer\SnapShot</SnapShotWorkingDir>
          	 <DistributorDBDataFolder>D:\SQLServer\Data</DistributorDBDataFolder>
         	  <DistributorLogFolder>D:\SQLServer\Data</DistributorLogFolder>
         	  <!-- Based on the systems number of cores we can set but max this value can be 8. Recomended:4 - 8 -->
         	  <MaxBCPThreads>4</MaxBCPThreads>
         	  <!-- To increases the performance of the replication, based on this value number of PK publisher will get created. This value should be between 1 to 3 -->
         	  <NumberOfPublishers>2</NumberOfPublishers>
         	  <!-- Ignore DB object xml files, Adding the object in these files will be ignored being replicated -->
        	   <IgnoreTablesList>\Data\ignoretables.xml</IgnoreTablesList>
        	   <IgnoreFunctionsList>\Data\ignorefunctions.xml</IgnoreFunctionsList>
     	</SQLReplicationSettings>
	</Config>
    ```
    
- XML Schema: To ignore selected tables, views, and functions during replication

    ```xml
    <IgnoreTables>                      <IgnoreFunctions>
        <Name>SYSDATABASELOG</Name>         <Name></Name>
    </IgnoreTables>                      </IgnoreFunctions>
    ```
    
## Configuring replication

SQLTransactionalReplication folder has all the PowerShell scripts that required to configure the SQL transactional replication. These scripts should be executed in the same sequence as below and wait for it to finish.

1. **Replication_01_DataBaseCleanup.ps1** - Will empty the target database.
2. **Replication_02_Distributor.ps1** - Upon completing distributor database will get created in the source database server under system database.
3. **Replication_03_PublisherTables.ps1** - Once the publisher scripts are executed successfully, publication will get created under the replication folder. Note that this will take some time to complete. Created publishers AXDB_PUB_TABLE_Obj_[*].

    > [WARNING!]
    > Wait for data replication to complete before executing cutover scripts. You can check the status in the following ways:
    > 1. Replication monitor: On the source server, right click 'Replication' folder and select **Launch Replication Monitor**. 
    > 2. Run GetStatus.ps1 script embedded in the replication toolkit. 'DataReplicationStatus' must be set to complete for each of the AXDB_PUB_TABLE_Obj_[*] publication.
  
4. **Replication_04_PublisherOtherObjects.ps1** - Replicates functions to target database by creating new publication. This step can be omitted if you don't want to move functions. Note that this will be completed quickly. Creates publisher AX_PUB_OtherObjects.
5. **CutOver_01_PublisherNoPK**.ps1 - This creates two publications to replicate: 
        - Non Primary Key tables 
        - Locked tables with publication names: AX_PUB_NoPKTable, AXDB_PUB_TABLE_Locked
7. **CutOver_02_PKDeletion_PostReplication.ps1** - This will clean up the temp tables created for no primary key tables. Deletes publication AX_PUB_NoPKTable.
8. **CutOver_03_RetrieveAndCreateNoPKConstraints.ps1** - This extracts constraints for the non PK tables from the source and create them in the target database.
9. **CutOver_04_RemoveReplication.ps1** - After successful replication of database, we can execute this script to remove replication setup. If you want to remove the Snap Shot folder without error execute this below SP in the source Db (or) after execution you will get an exception unable to remove the snap shot folders and can be removed manually.

```sql
EXEC master.dbo.sp_configure 'show advanced options', 1
RECONFIGURE WITH OVERRIDE
EXEC master.dbo.sp_configure 'xp_cmdshell', 1
RECONFIGURE WITH OVERRIDE
```

Below are the publications that will get created on source database when setting up the replication.

![The publications that will get created on source database when setting up the replication](media/Replication.png)

## To know replication status and get exception

Execute the power shell script and wait for it to finish.

**GetStatus.ps1** - If we execute this script, Replication status table will be listed, with this scheam AgentId, PublicationName, Job, LastSynced, JobStatus, ReplicationStatus, Comments.

- AgentId - Will be use to fetch the exception details about the job
- PublicationName - This is the publication names what we created for replicating the data, you can find the same in the SQLServerExplorer under Replication folder
- Job - It will have two types of jobs, Snapshot & Data Replication
- JobStatus - This will display any of these status, Started, Succeeded, In Progress, Idle, Retrying, Failed, for Snapshot jobs after it got succeeded this will not execute, but for the data replication jobs the job status will keep changing based on the new data update in the database.
- ReplicationStatus - This status applies only to the Data Replication jobs, will display Waiting, In Progress, Completed
- Comments - This will keep changing when the job is InProgress stat
 
**GetException.ps1** - To get the exception, need to provide AgengId this can be retrieve/get from the status

## To know the replication configuration and status via SQL Server Management Studio

- To know that the replication feature is available and installed on the server, you should see the Replication folder in Object Explorer, as shown in the image below.
   
   ![Replication folder](media/Replication1.png)

- After executing the **Replication_03_PublisherTables.ps1** script, you should be able to see the publisher configured under the Replication folder.
    
    ![See publishers under the Replication folder](media/Replication2.png)

- To know the replication status, right-click on the Replication folder and select the Launch Replication Monitor.
   
   ![Select Launch Replication Monitor in the menu.](media/Replication3.png)

- In the Replication Montior window, you can see all the publishers that have been created for replication.
    
    ![See all the publishers that have been created for replication](media/Replication4.png)

- Selecting the Snapshot tab, you can see the status of the snapshot.
  
  ![Selecting the Snapshot tab, you can see the status of the snapshot.](media/Replication5.png)

- To view the detail log/transaction, double-click on the item.
   
   ![To view the detail log/transaction, double-click on the item.](media/Replication6.png)

- To view the data replication to the target, select the All Subscription tab and double-click the subscription from the item. 

## Troubleshooting FAQs

| **Exception** | **Solution/Fix** |
|-------------------------|-------------------------|
| After creating the publication if the snapshot creation is failing<br></br><em>Error messages:</em></br><em>Source: Microsoft.SqlServer.Smo</em></br><em>Target Site: Void PrefetchObjectsImpl(System.Type, Microsoft.SqlServer.Management.Smo.ScriptingPreferences)</em></br><em>Message: Prefetch objects failed for Database 'AxDB_ASIA'.</em></br><em>Stack:    at Microsoft.SqlServer.Management.Smo.Database.PrefetchObjectsImpl(Type objectType, ScriptingPreferences scriptingPreferences)</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.ObjectPrefetchControl.DoPrefetch(Database database)</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.PrefetchObjects(ObjectPrefetchControl[] objectPrefetchControls)</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoPrefetchWithRetry()</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SmoScriptingManager.DoScripting()</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.DoScripting()</em></br><em>   at Microsoft.SqlServer.Replication.Snapshot.SqlServerSnapshotProvider.GenerateSnapshot()</em></br><em>   at Microsoft.SqlServer.Replication.SnapshotGenerationAgent.InternalRun()</em></br><em>   at Microsoft.SqlServer.Replication.AgentCore.Run() (Source: Microsoft.SqlServer.Smo, Error number: 0)</em> | From the Replication Monitor, restart the snapshot creation. |
| The subscription(s) have been marked inactive and must be reinitialized. NoSync subscriptions will need to be dropped and recreated. (Source: MSSQLServer, Error number: 21074) | 1) Check the status in the source database with the below query and update the status to &quot;2&quot; for the specific publication</br><em><br>Check the status, you can get the srvname from this output query</em></br>**select** * **from** syssubscriptions **WHERE** status != 2</br><em><br>Update only if the status !=2</em></br>**Update** syssubscriptions **SET** status = 2 **where** srvname = 'your target server name'</br><br>2) Check the status in the distributor database with the below query and update the status to &quot;2&quot; for the specific publication</br><em><br>To get the publication_id use this below query and you can match with your publication name</em></br>**SELECT** * **FROM** MSpublications</br><em><br>Check the status from the below query</em></br>**SELECT** * **FROM** MSsubscriptions **WHERE** status !=2 publication_id = &lt;@publicationId&gt;</br><em><br>Update if the status is !-2 for that specific publication_id</em></br>**Update** MSsubscriptions **SET** status = 2 **where** publication_id = &lt;@publicationId&gt; |
| Error messages:</br><em><br>The process could not execute 'sp_replcmds' on 'replicationsrv\MSSQLSERVER2016'. (Source: MSSQL_REPL, Error number: MSSQL_REPL20011)</em></br><em>Get help: http://help/MSSQL_REPL20011</em></br><em><br>Cannot execute as the database principal because the principal &quot;dbo&quot; does not exist, this type of principal cannot be impersonated, or you do not have permission. (Source: MSSQLServer, Error number: 15517)</em></br><em>Get help: http://help/15517</em></br><em><br>The process could not execute 'sp_replcmds' on 'replicationsrv\MSSQLSERVER2016'. (Source: MSSQL_REPL, Error number: MSSQL_REPL22037)</em></br><em>Get help: http://help/MSSQL_REPL22037</em> | Execute this in the source database and log in with the credentials you used to create the publication</br>**EXEC** sp_changedbowner 'sa' |
| To remove/delete a publication | Execute this Sp's in the source database;</br><em><br>Cleaning the subscription:</em></br>**exec** sp_subscription_cleanup @publisher = @publisherServer, @publisher_db = @publisherDb, @publication = @publicationName</br><em><br>Drop subscription:</em></br>**exec** sp_dropsubscription @publication = @publicationName, @subscriber = N'all', @article = N'all'</br><em><br>Drop publication:</em></br>**exec** sp_droppublication @publication = @publicationName |
| To remove an article from the publication, see [sp_dropsubscription (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql?view=sql-server-ver15) | Execute this Sp in the source database:<br><br>**EXEC** sp_dropsubscription</br>@publication = @publication,</br>@article = N'all',</br>@subscriber = @subscriber;</br><em><br>Example: </em></br>**EXEC** sp_dropsubscription @publication = N'OtherObjects_sp', @article = N'MaintainShipCarrierRole', @subscriber = N'SPARTAN-SRV-NAM-D365OPSDEV-D5E38124F9F8.DATABASE.WINDOWS.NET'; |



