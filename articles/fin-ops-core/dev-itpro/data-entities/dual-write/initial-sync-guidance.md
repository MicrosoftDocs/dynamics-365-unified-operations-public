---

title: Considerations for initial synchronization
description: This topic provides constraints, known issues, and guidance for the initial synchronization of dual-write.
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
# ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramasri
ms.search.validFrom: 2020-10-12
ms.dyn365.ops.version: AX 7.0.0
---

# Considerations for initial synchronization

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]


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

The maximum number of records allowed through initial sync is 500K per run. That limit is 500K per legal entity, because each legal entity runs separately. For more information, see [Integrate data into Common Data Service](https://docs.microsoft.com/power-platform/admin/data-integrator), in particular, "To optimize performance and not overload the apps, we currently limit project executions to 500k rows per execution per project."

If you need to run the initial sync with more than 500K records in a run, then we recommend that you migrate data into the Finance and Operations app and Common Data Service separately, skipping the initial sync.

### 24-hour limit

If you are running the initial sync from Common Data Service to the Finance and Operations apps, there is a timeout of 24 hours for getting the import result back from the Finance and Operations app. If you are syncing a lot of data and the single execution takes above 24 hours, you might hit the timeout and the initial sync fails. For example, an initial sync from Common Data Service to a Finance and Operations apps for the **Customer/Account** entity with 70k records could take more than 24 hours, hitting the 24-hour limit.

Do not the initial sync from Common Data Service to a Finance and Operations app for the [single-threaded entities](#single-threaded-entities) if the data volume is above 70K. These entities do not support multi-threading during import and you might hit the limit if the volume is above 70K. In this situation, you should migrate data into the Finance and Operations app and Common Data Service separately, skipping the initial sync.

### 40 legal entities limit while linking the environments

The current limit is 40 legal entities while linking the environments. You will encounter the following error if you try to enable maps with more than 40 legal entities linked between the environments.

```console
Dual-write failure - Plugin registration failed: [(Unable to get partition map for project DWM-1ae35e60-4bc2-4905-88ea-XXXXX. Error Exceeds the maximum partitions allowed for mapping DWM-1ae35e60-4bc2-4905-88ea- XXXXX)], One or more errors occurred.
```

### Initial sync for entity map with 10 or more lookups is not currently supported

This limitation applies to only the initial sync from Common Data Service for entity maps with 10 or more lookups. If you run the initial sync against an entity map with 10 or more lookups, you might encounter this error:

```console
5 Attempts to get data from https://XXXX.azure-apim.net/apim... Failed
```

In this situation, you should migrate data into the Finance and Operations app and Common Data Service separately, skipping the initial sync.

### 5-minute limit for Finance and Operations data export

If you are running the initial sync from the Finance and Operations app to Common Data Service and the Finance and Operations data export takes more than 5 minutes, then the initial sync might time out. The time out can happen if the data entity has virtual fields with the **postLoad** method, or the export query isn't optimized (for example, it has missing indexes).

This kind of sync will be supported after PU37. You should update your Finance and Operations app to PU37 or later.

### Error handling capabilities

#### Initial sync is always full push

If an individual record fails to sync, you cannot resync the individual record. The initials sync always pushes the entire data set, called a full push. If the initial sync only  partially succeeded, then the second sync runs again for all the records, not just the ones that failed.

#### Only top 5 errors can be viewed

You can view only the top 5 errors from the initial synch error log.

## Known issues

For information about known issues, see [Troubleshoot issues during initial synchronization](dual-write-troubleshooting-initial-sync.md).

## Guidance matrix

Finance and Operations instance | Common Data Service instance | Has data to run initial sync | Description | Max volume in an entity | Data entity type (single-threaded or multi-threaded) | Approach
---|---|---|---|---|---|---
| New | New | No | A new Finance and Operations app instance and a customer engagement app instance, with no initial data. | -NA- | Any | 1. Activate dual-write and skip the initial sync.
| New | New | Yes | A new Finance and Operations app instance and a customer engagement app instance, with migrated data in either app. | < 500K | [single-threaded](#single-threaded-entities) | 1. Migrate data to the Finance and Operations app.<br>2. Run the initial sync.
|  |  |  |  | < 500K | multi-threaded | 1. Migrate data to Common Data Service.<br>2. Run the initial sync.
|  |  |  |  | > 500K | Any | 1. Migrate data to each app, outside of the initial sync.<br>2. Activate dual-write and skip initial sync.
| New | Existing | Yes | A new Finance and Operations app instance and an existing customer engagement app instance | < 70K | [single-threaded](#single-threaded-entities) | 1. Create a new company in the Finance and Operations app<br>2.Bootstrap Common Data Service for the company code.<br>3. Run the initial sync.
|  |  |  |  | > 70K | [single-threaded](#single-threaded-entities) | 1. Create a new company in the Finance and Operations app.<br>2. Bootstrap Common Data Service for the company code.<br>3. Migrate data to each app, outside of the initial sync.<br>4. Activate dual-write and skip the initial sync.
|  |  |  |  | < 500K | multi-threaded | 1. Create a new company in the Finance and Operations app.<br>2. Bootstrap Common Data Service for the company code.<br>3. Run the initial sync.
|  |  |  |  | > 500K | Any | 1. Create a new company in the Finance and Operations app.<br>2. Bootstrap Common Data Service for the company code.<br>3. Migrate data to each app, outside of the initial sync.<br>4. Activate dual-write and skip the initial sync.
| Existing | New | Yes | An existing Finance and Operations app instance and a new customer engagement app instance | < 500K | Any | 1. Run the initial sync.
|  |  |  |  | > 500K | Any | 1. Migrate data to each app.<br>2. Activate dual-write and skip the initial sync.
| Existing | Existing | Yes | An existing Finance and Operations app instance and an existing customer engagement app instance | < 70K | [single-threaded](#single-threaded-entities) | 1. Bootstrap Common Data Service for the company code.<br>2. Run the initial sync.
|  |  |  |  | > 70K | [single-threaded](#single-threaded-entities) | 1. Bootstrap Common Data Service for the company code.<br>2. Migrate data to each app, outside of the initial sync.<br>3. Activate dual-write and skip the initial sync.
|  |  |  |  | < 500K | multi-threaded | 1. Bootstrap Common Data Service for the company code.<br>2. Run the initial sync.
|  |  |  |  | > 500K | Any | 1. Bootstrap Common Data Service for the company code.<br>2. Migrate data to each app, outside of the initial sync.<br>3. Activate dual-write and skip the initial sync.

## <a id="single-threaded-entities"></a>Single-threaded entities

- Sales tax codes (msdyn\_taxcodes)
- Customers V3 (accounts)
- Vendors V2 (msdyn\_vendors)
- Warehouses (msdyn\_warehouses)
- Product categories (msdyn\_productcategories)
- Employment (cdm\_employments)
- Position worker assignments (cdm\_positionworkerassignmentmaps)
- Warehouse locations (msdyn\_inventorylocations)
- Modes of delivery (msdyn\_shipvias)
