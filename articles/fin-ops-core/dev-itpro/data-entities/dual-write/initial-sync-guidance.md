---
title: Considerations for initial synchronization
description: Learn about considerations, constraints, known issues, and guidance for the initial synchronization of dual-write.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: article
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-10-12
ms.dyn365.ops.version: AX 7.0.0
---

# Considerations for initial synchronization

[!include [banner](../../includes/banner.md)]

Before you start dual-write on a table, run an initial synchronization to handle existing data on both sides: finance and operations apps and customer engagement apps. You can skip the initial synchronization if you don't need to sync data between the two environments.

The initial synchronization copies existing data from one app to another bidirectionally, and there are several considerations when you run it. For example, you might need to migrate data before your go-live. In this case, you can load data into one side through data migration and then sync it to the other side through the initial synchronization.

Use the following approach for the initial synchronization:

+ **[Single-threaded tables](#single-threaded-entities):** First migrate data into the finance and operations app, and then trigger the initial synchronization to move the data over to Dataverse. Based on lab testing that Microsoft has done, this sequence has better performance than synchronization from Dataverse to finance and operations apps.
+ **Multithreaded tables:** First migrate data into Dataverse, and then trigger the initial synchronization to move the data over to the finance and operations app.

## Constraints

### Data migration slow-down with enabled dual-write

If you first activate the map in dual-write and then start to import data, migration performance is poor. Don't activate running maps in dual-write until the data migration is complete.

### Limit of 500,000 rows per run

The maximum number of rows that the initial synchronization allows is 500,000 per run. The limit of 500,000 rows applies to each legal entity, because each legal entity runs separately. For more information, see [Integrate data into Dataverse](/power-platform/admin/data-integrator). In particular, pay attention to the note that states, "To optimize performance and not overload the apps, we currently limit project executions to 500k rows per execution per project."

If you need more than 500,000 rows in a run when using initial synchronization, migrate data into the finance and operations app and Dataverse separately, and skip the initial synchronization.

### 24-hour limit

When you run the initial synchronization from Dataverse to the finance and operations app, the finance and operations app must send the import result back within 24 hours. Otherwise, a time out occurs. Therefore, if you're syncing lots of data and the single run takes more than 24 hours, the initial synchronization might fail because of a time out. For example, an initial synchronization from Dataverse to a finance and operations app for the **Customer/Account** table involves 70,000 rows. Therefore, the run might take more than 24 hours and time out.

Don't run the initial synchronization from Dataverse to a finance and operations app for [single-threaded tables](#single-threaded-entities) if the data volume is more than 70,000 rows. Because these tables don't support multithreading during import, a time out might occur if the volume is more 70,000 rows. In this situation, you should migrate data into the finance and operations app and Dataverse separately, and skip the initial synchronization.

### Limit of 40 legal entities while the environments are linking

Currently, there's a limit of 40 legal entities while the environments are linking. If you try to enable maps where more than 40 legal entities are linked between the environments, you receive the following error message:

```console
Dual-write failure - Plugin registration failed: [(Unable to get partition map for project DWM-1ae35e60-4bc2-4905-88ea-XXXXX. Error Exceeds the maximum partitions allowed for mapping DWM-1ae35e60-4bc2-4905-88ea- XXXXX)], One or more errors occurred.
```

### Initial synchronization isn't currently supported for table maps that have 10 or more lookups

This limitation applies only to the initial synchronization from Dataverse for table maps that have 10 or more lookups. If you run the initial synchronization against a table map that has 10 or more lookups, you might receive the following error message:

```console
5 Attempts to get data from https://XXXX.azure-apim.net/apim... Failed
```

As a workaround you can split the initial sync into these steps:

1. Remove some of the lookup columns that aren't mandatory from the dual-write table map and bring the number of lookups to 10.
1. After the lookup columns are removed, save the map, and do the initial sync.
1. After the initial sync for the first step is successful, add the remaining lookup columns and remove the lookup columns that were synced in first step. Once again make sure the number of lookup columns is 10. Save the map and run the initial sync. Repeat these steps to make sure all the lookup columns are synced.
1. Add all the lookup columns back to the map, save the map and run the map with skip initial sync. This enables the map for live sync mode.

### Five-minute limit for finance and operations data export

When you run the initial synchronization from the finance and operations app to Dataverse, the synchronization might time out if the finance and operations data export takes more than five minutes. The time out can happen if the data table has virtual columns with the `postLoad` method, or the export query isn't optimized (for example, if it has missing indexes).

This type of synchronization is supported in Platform update 37 (PU37) and later. Therefore, you should update your finance and operations app to PU37 or later.

### Security role for write access

Add every user in a customer engagement organization with dual-write to the **Dual-Write Runtime User** role. Without this role, users can't create any rows in tables in the customer engagement organization.

### Company and Currency Exchange Tables Required Security Role

Company and currency exchange tables are global in nature, and all dual-write users need read access to these two tables. To provide access, add all dual-write users to the **Dual-Write App User** security role. If a user doesn't have this security role assigned, they can't read tables that contain Company and Currency values.

### Error handling capabilities

#### Initial synchronization is a full push or incremental push

If an individual row fails to synchronize, you can't resync only that individual row. The first run of initial synchronization pushes the whole data set. This behavior is known as a *full push*. When change tracking is enabled in finance and operations apps, the subsequent runs are an incremental push that is based on the last run map version. When change tracking is disabled, subsequent runs cause a full push. During the incremental push, the error records aren't considered for resubmission.

#### Only the top five errors can be viewed

You can view only the top five errors from the initial synchronization error log.

### Double quotes limitation

Because the initial sync process handles some source fields, double quotes in your data can cause the initial sync to fail with an error message similar to the following error message:

```console
Initial writes failed while parsing the data for leg:From Dynamics 365 for Finance and Operations Entity to Dynamics 365 for Sales Entity - Legal Entity. Message: Type=Microsoft.VisualBasic.FileIO.MalformedLineException, Msg=Line # cannot be parsed using the current Delimiters.
```

To address this error, locate and remove the double quotes from your data.

## Known issues

For information about known issues, see [Troubleshoot issues during initial synchronization](dual-write-troubleshooting-initial-sync.md).

## Guidance matrix

| finance and operations app instance | Dataverse instance | Has data to run the initial synchronization | Description | Maximum volume in a table | Single-threaded or multithreaded | Approach |
| --- | --- | --- | --- | --- | --- | --- |
| New | New | No | A new finance and operations app instance and a new customer engagement app instance, where neither app has initial data | Not applicable | Any | <ul><li>Activate dual-write, and skip the initial synchronization.</li></ul> |
| New | New | Yes | A new finance and operations app instance and a new customer engagement app instance, where one of the apps has migrated data | &lt; 500,000 | [Single-threaded](#single-threaded-entities) | <ol><li>Migrate data to the finance and operations app.</li><li>Run the initial synchronization.</li></ol> |
| New | New | Yes | A new finance and operations app instance and a new customer engagement app instance, where one of the apps has migrated data | &lt; 500,000 | Multithreaded | <ol><li>Migrate data to Dataverse.</li><li>Run the initial synchronization.</li></ol> |
| New | New | Yes | A new finance and operations app instance and a new customer engagement app instance, where one of the apps has migrated data | &gt; 500,000 | Any | <ol><li>Migrate data to each app outside the initial synchronization.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |
| New | Existing | Yes | A new finance and operations app instance and an existing customer engagement app instance | &lt; 70,000 | [Single-threaded](#single-threaded-entities) | <ol><li>Create a new company in the finance and operations app.</li><li>Bootstrap Dataverse for the company code.</li><li>Run the initial synchronization.</li></ol> |
| New | Existing | Yes | A new finance and operations app instance and an existing customer engagement app instance | &gt; 70,000 | [Single-threaded](#single-threaded-entities) | <ol><li>Create a new company in the finance and operations app.</li><li>Bootstrap Dataverse for the company code.</li><li>Migrate data to each app outside the initial synchronization.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |
| New | Existing | Yes | A new finance and operations app instance and an existing customer engagement app instance | &lt; 500,000 | Multithreaded | <ol><li>Create a new company in the finance and operations app.</li><li>Bootstrap Dataverse for the company code.</li><li>Run the initial synchronization.</li></ol> |
| New | Existing | Yes | A new finance and operations app instance and an existing customer engagement app instance | &gt; 500,000 | Any | <ol><li>Create a new company in the finance and operations app.</li><li>Bootstrap Dataverse for the company code.</li><li>Migrate data to each app outside the initial synchronization.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |
| Existing | New | Yes | An existing finance and operations app instance and a new customer engagement app instance | &lt; 500,000 | Any | <ul><li>Run the initial synchronization.</li></ul> |
| Existing | New | Yes | An existing finance and operations app instance and a new customer engagement app instance | &gt; 500,000 | Any | <ol><li>Migrate data to each app.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |
| Existing | Existing | Yes | An existing finance and operations app instance and an existing customer engagement app instance | &lt; 70,000 | [Single-threaded](#single-threaded-entities) | <ol><li>Bootstrap Dataverse for the company code.</li><li>Run the initial synchronization.</li></ol> |
| Existing | Existing | Yes | An existing finance and operations app instance and an existing customer engagement app instance | &gt; 70,000 | [Single-threaded](#single-threaded-entities) | <ol><li>Bootstrap Dataverse for the company code.</li><li>Migrate data to each app outside the initial synchronization.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |
| Existing | Existing | Yes | An existing finance and operations app instance and an existing customer engagement app instance | &lt; 500,000 | Multithreaded | <ol><li>Bootstrap Dataverse for the company code.</li><li>Run the initial synchronization.</li></ol> |
| Existing | Existing | Yes | An existing finance and operations app instance and an existing customer engagement app instance | &gt; 500,000 | Any | <ol><li>Bootstrap Dataverse for the company code.</li><li>Migrate data to each app outside the initial synchronization.</li><li>Activate dual-write, and skip the initial synchronization.</li></ol> |

## <a id="single-threaded-entities"></a>Single-threaded tables

+ Sales tax codes (msdyn_taxcodes)
+ Customers V3 (accounts)
+ Vendors V2 (msdyn_vendors)
+ Warehouses (msdyn_warehouses)
+ Product categories (msdyn_productcategories)
+ Employment (cdm_employments)
+ Position worker assignments (cdm_positionworkerassignmentmaps)
+ Warehouse locations (msdyn_inventorylocations)
+ Modes of delivery (msdyn_shipvias)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
