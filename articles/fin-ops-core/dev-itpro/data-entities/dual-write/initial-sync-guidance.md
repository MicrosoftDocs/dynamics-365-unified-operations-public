---

title: Considerations for initial synchronization
description: This topic provides constraints, known issues, and guidance for the initial sychronization of dual-write.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 10/12/2020
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
ms.search.validFrom: 2020-10-12
ms.dyn365.ops.version: AX 7.0.0
---

# Considerations for initial synchronization

[!include [banner](../../includes/banner.md)]


## Overview

Before you start dual-write on an entity, you can run an initial sync to handle existing data on both sides of Finance and Operations apps and customer engagement apps. You can skip the initial sync if you don't need to synchronize data between the two environments.

The initial sync lets you copy existing data from one app to another bidirectionally, and there are several considerations to run initial sync. You might need to migrate data before your go-live. In that case, data can be loaded into one side through data migration and then synchronized to the other side through the initial sync.

Our recommendation for the initial sync:

+ [Single-threaded entities](#single-threaded-entities): Migrate data into the Finance and Operations app first and then trigger the initial sync to move the data over to Common Data Service. Based on our lab testing, that sequence has better performance than syncing from Common Data Service to Finance and Operations apps.
+ Multi-threaded entities: Migrate data into Common Data Service first and then trigger the initial sync to move the data over to the Finance and Operations app.

## Constraints

### Data migration slow-down with enabled dual-write

If you activate the map in dual-write first and then start importing data, then that will cause poor migration performance. We recommend that you not activate running maps in dual-write until the data migration is completed.

### 500k limit per execution

The maximum number of records allowed through initial sync is 500K per run. That is 500K per legal entity, because each legal entity runs separately. For more information, see [Integrate data into Common Data Service](https://docs.microsoft.com/power-platform/admin/data-integrator), in particular, "To optimize performance and not overload the apps, we currently limit project executions to 500k rows per execution per project."

If you need to run the initial sync with more than 500K records in a run, then we recommend that you migrate data into the Finance and Operations app and Common Data Service separately, skipping the initial sync.

### 24-hour limit

If you are running the initial sync from Common Data Service to the Finance and Operations apps, there is a timeout of 24 hours for getting the import result back from the Finance and Operations app. If you are syncing a lot of data and the single execution takes above 24 hours, you might hit the timeout and the initial sync fails. For example, an initial sync from Common Data Service to a Finance and Operations apps for the **Customer/Account** entity with 70k records could take more than 24 hours, hitting the 24-hour limit.

You should not run the initial sync from Common Data Service to a Finance and Operations app for the [single-threaded entities](#single-threaded-entities) if the data volume is above 70K. These entities do not support multi-threading during import and you might hit the limit if the volume is above 70K, In this situation, you should migrate data into the Finance and Operations app and Common Data Service separately, skipping the initial sync.

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

## <a id="single-threaded-entities"></a>Single-threaded entities

-   Sales tax codes (msdyn\_taxcodes)

-   Customers V3 (accounts)

-   Vendors V2 (msdyn\_vendors)

-   Warehouses (msdyn\_warehouses)

-   Product categories (msdyn\_productcategories)

-   Employment (cdm\_employments)
