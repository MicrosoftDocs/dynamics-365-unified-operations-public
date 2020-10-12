---

title: Guidance for initial sync in dual-write
description: 
author: 
manager: AnnBe
ms.date: 03/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author:
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Considerations for initial synchronization

[!include [banner](../../includes/banner.md)]


## Overview

Before you turn on dual-write for an entity, you can run initial sync to handle existing data on both sides of Finance and Operations apps, and model-driven apps which the data is saved in Common Data Service(CDS); or you can just skip the initial sync to turn on the dual-write if there is no need to synchronize data between those two apps.

Initial sync provides the ability to copy existing data from one app to another bidirectionally, as there are several considerations to run initial sync. 

Basically, you may need to migrate data before Go-live, so in that case, data can be loaded into one side through data migration and synchronize to the other side through initial sync.

Our recommendation for single-thread entities (*) is to migrate data into Finance and Operations apps first and then trigger initial sync to move it over to CDS. The reason for that is to get the best performance comparing to sync from CDS into Finance and Operations for single-thread entities based on our lab testing.

For other multi-thread entities, migrate data into CDS first and then trigger initial sync to move it over to Finance and Operations apps.


## Considerations

### Data migration slow-down with enabled dual-write

If you first activate the map in dual-write and then start data importing that will cause poor migration performance. It is recommended not activate running maps in dual-write until data migration is completed.

### 500k limit per execution

The maximum number of records allowed through initial sync is 500K per execution (per legal entity, as each legal entity will have its own execution). Please refer to details [here](https://docs.microsoft.com/en-us/power-platform/admin/data-integrator), to optimize performance and not overload the apps, we currently limit project executions to 500k rows per execution per project.

**Workaround** : In case you need to run initial sync with data volume greater than 500K per execution, then it is recommended to migrate data into Finance and Operations app and CDS separately and skip initial sync.

### 24-hour limit

In case of running initial sync from CDS to Finance and Operations apps, there is a timeout of 24 hours for getting the import result back from Finance and Operations app. For large volumes of initial sync from CDS to Finance and Operations app, if the single execution takes above 24 hours, that may hit the timeout and the initial sync will fail.

E.g. Initial sync from CDS to Finance and Operations apps for Customer/Account entity with 70k records may take above 24 hours, which will hit the 24-hour limit

**Workaround** : It is not recommended to run initial sync from CDS to Finance and Operations apps for below entities if the data volume is above 70,000, as those entities do not support multi-threading import and it may hit the limit if the volume is above 70,000, so in those cases you&#39;ll need to migrate data into Finance and Operations app and CDS separately outside Initial sync and skip initial sync.

-   Sales tax codes (msdyn\_taxcodes)

-   Customers V3 (accounts)

-   Vendors V2 (msdyn\_vendors)

-   Warehouses (msdyn\_warehouses)

-   Product categories (msdyn\_productcategories)

-   Employment (cdm\_employments)

### 40 legal entities limit while linking the environments

The current limit is 40 legal entities while linking the environments. You will get the below error if trying to enable maps with more than 40 legal entities linked between the environments.

Dual-write failure - Plugin registration failed: [(Unable to get partition map for project DWM-1ae35e60-4bc2-4905-88ea-XXXXX. Error Exceeds the maximum partitions allowed for mapping DWM-1ae35e60-4bc2-4905-88ea- XXXXX)], One or more errors occurred.

### Initial sync for entity map with 10+ lookups is not currently supported

This impacts only the initial sync from CDS for entity maps with 10+ lookups.

If run initial sync against entity map with 10+ lookups you may see error message: 5 Attempts to get data from https://XXXX.azure-apim.net/apim... Failed

**Workaround** : To migrate data into Finance and Operations app and CDS separately and skip initial sync.

### 5 minutes limit for Finance and Operations export

In case of running initial sync from Finance and Operations app to CDS, if Finance and Operations export takes 5+ minutes, the Initial sync may time out. This can happen if the data entity has virtual fields with postLoad method, or the export query isn&#39;t optimum (i.e. missing indexes etc.).

**Workaround** : This will be supported post PU37. Please consider update your Finance and Operations app to PU37+.

### Error handling capabilities

#### Initial sync is always full push

You can&#39;t reprocess only failed records; it always pushes entire data again (full push). When the initial sync was partially succeeded, then 2nd time will re-run for all the records, not only the error ones.

#### Only top 5 errors can be viewed

You can only view top 5 errors from the initial synch error log.

## Known issues

Please refer to [details](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-troubleshooting-initial-sync) that can help you fix issues that might occur during initial sync.

## Guidance matrix

<table><thead><tr class="header"><th>Finance and Operations instance</th><th>CDS instance</th><th>Has data to run initial sync</th><th>Description</th><th>Max Volume in an Entity</th><th>Data Entity Type (Single thread/Multi thread)</th><th>Approach</th></tr></thead><tbody><tr class="odd"><td>New</td><td>New</td><td>No</td><td>A new Finance and Operations app instance and a new model-driven app instance, with no initial data</td><td>-NA-</td><td>Any</td><td>1. Activate dual-write and skip initial write</td></tr><tr class="even"><td>New</td><td>New</td><td>Yes</td><td>A new Finance and Operations app instance and a new model-driven app instance, with migrated data in either apps</td><td>&lt; 500K</td><td>Single-Threaded (*)</td><td>1. Migrate data to Finance and Operations apps<br />
2. Run Initial sync</td></tr><tr class="odd"><td></td><td></td><td></td><td></td><td>&lt; 500K</td><td>Multi-Threaded</td><td>1. Migrate data to CDS<br />
2. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 500K</td><td>Any</td><td>1. Migrate data to each app, outside of Initial sync<br />
2. Activate dual-write and skip initial sync</td></tr><tr class="odd"><td>New</td><td>Existing</td><td>Yes</td><td>A new Finance and Operations app instance and an existing model-driven app instance</td><td>&lt; 70K</td><td>Single-Threaded (*)</td><td>1. Create a new company in Finance and Operations apps<br />
2. BootStrap CDS for company code<br />
3. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 70K</td><td>Single-Threaded (*)</td><td>1. Create a new company in Finance and Operations apps<br />
2. BootStrap CDS for company code<br />
3. Migrate data to each app, outside of Initial sync<br />
4. Activate dual-write and skip initial sync</td></tr><tr class="odd"><td></td><td></td><td></td><td></td><td>&lt; 500K</td><td>Multi-Threaded</td><td>1. Create a new company in Finance and Operations apps<br />
2. BootStrap CDS for company code<br />
3. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 500K</td><td>Any</td><td>1. Create a new company in Finance and Operations apps<br />
2. BootStrap CDS for company code<br />
3. Migrate data to each app, outside of Initial sync<br />
4. Activate Dual-write and skip initial sync</td></tr><tr class="odd"><td>Existing</td><td>New</td><td>Yes</td><td>An existing Finance and Operations app instance and a new model-driven app instance</td><td>&lt; 500K</td><td>Any</td><td>1. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 500K</td><td>Any</td><td>1. Migrate data to each app<br />
2. Activate Dual-write and skip initial sync</td></tr><tr class="odd"><td>Existing</td><td>Existing</td><td>Yes</td><td>An existing Finance and Operations app instance and existing model-driven app instance</td><td>&lt; 70K</td><td>Single-Threaded (*)</td><td>1. BootStrap CDS for company code<br />
2. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 70K</td><td>Single-Threaded (*)</td><td>1. BootStrap CDS for company code<br />
2. Migrate data to each app, outside of Initial sync<br />
3. Activate dual-write and skip initial sync</td></tr><tr class="odd"><td></td><td></td><td></td><td></td><td>&lt;500K</td><td>Multi-Threaded</td><td>1. BootStrap CDS for company code<br />
2. Run Initial sync</td></tr><tr class="even"><td></td><td></td><td></td><td></td><td>&gt; 500K</td><td>Any</td><td>1. BootStrap CDS for company code<br />
2. Migrate data to each app, outside of Initial sync<br />
3. Activate Dual-write and skip initial sync</td></tr></tbody></table>

\*Single-thread entities:

-   Sales tax codes (msdyn\_taxcodes)

-   Customers V3 (accounts)

-   Vendors V2 (msdyn\_vendors)

-   Warehouses (msdyn\_warehouses)

-   Product categories (msdyn\_productcategories)

-   Employment (cdm\_employments)
