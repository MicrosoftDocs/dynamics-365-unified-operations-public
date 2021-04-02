---
# required metadata

title: Replication setup
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: sarvanisathish
ms.date: 04/02/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sarvanis
ms.search.validFrom: 2021-04-30
---

# Replication setup

[!include[banner](../includes/banner.md)]

## Prerequisites

-	Source SQLServer should have enabled/installed replication feature.
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

- When Setting up Distributor:
    The script creates a Database in the Source Server. So, make sure you have enough space (Recommended is minimum it should have the size of the source database). In params.json, you can specify the Distributor database path, so this database can be created in the specified path.
Update params.json

    ```sql
    {
    "sourceServer" : "<<your source database server>>" eg: LAPTOP\\MSSQLSERVER2012", Don't use localhost
    "sourceDatabase" : "<<your source database, database to be migrated>>",
    "sourceServerUserName" : "<<SQL Login Username>>",
    "sourceServerPWD" : <<SQL Login Password>>,
    "targetServer" : "<<your target/spartan database server>>" eg:"dbmigration.database.windows.net",
    "targetDatabase" : "<<your target database>>",
    "targetServerUserName" : "axdbadmin",
    "targetServerPWD" : "<<admin password>>",
    "snapShotWorkingDir" : "<<snap shot creation folder>>" ensure you have enough space in the drive eg: D:\\SQLServer\\SnapShot",
    "distributorDbDataFolder":"<<distributor datafile path>>" ensure you have enough space in the drive,
    "distributorLogFolder":"<<distributor logfile path>>" ensure you have enough space in the drive,
    "maxBCPThreads":<<you can set 1 for one core, but max this value can be 8>> Recomended:4 - 8,
    "numberOfPublishers":<<how name publisher creation for PK Tables >> Recommended: less than or equal to(>=)3 based on t he maxBCPThreads
    "ignoreTablesList":<<xml list of tables you want to exclude from replication>> edit ignoretables.xml file under data folder and use same schema
    "ignoreFunctionsList":<<xml list of functions you want to exclude from replication>> edit ignorefunctions.xml file under data folder and use same schema
    }
    ```
    
    XML Schema: To ignore selected tables, views and functions during replication

    ```xml
    <IgnoreTables>                      <IgnoreFunctions>
        <Name>SYSDATABASELOG</Name>         <Name></Name>
    </IgnoreTables>                      </IgnoreFunctions>
    
    
