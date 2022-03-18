---
title: Considerations for initial synchronization
description: This topic provides information about constraints, known issues, and guidance for the initial synchronization of dual-write.
author: RamaKrishnamoorthy
ms.date: 10/12/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2020-10-12
ms.dyn365.ops.version: AX 7.0.0
---

# Considerations for initial synchronization

[!include [banner](../../includes/banner.md)]



Before you start dual-write on a table, you can run an initial synchronization to handle existing data on both sides: Finance and Operations apps and customer engagement apps. You can skip the initial synchronization if you don't have to sync data between the two environments.

The initial synchronization lets you copy existing data from one app to another bidirectionally, and there are several considerations when you run it. For example, you might have to migrate data before your go-live. In this case, data can be loaded into one side through data migration and then synced to the other side through the initial synchronization.

We recommend that you use the following approach for the initial synchronization:

+ **[Single-threaded tables](#single-threaded-entities):** First migrate data into the Finance and Operations app, and then trigger the initial synchronization to move the data over to Dataverse. Based on lab testing that Microsoft has done, this sequence has better performance than synchronization from Dataverse to Finance and Operations apps.
+ **Multi-threaded tables:** First migrate data into Dataverse, and then trigger the initial synchronization to move the data over to the Finance and Operations app.

## Constraints

### Data migration slow-down with enabled dual-write

If you first activate the map in dual-write and then start to import data, migration performance will be poor. We recommend that you not activate running maps in dual-write until the data migration is completed.

### Limit of 500,000 rows per run

The maximum number of rows that is allowed through initial synchronization is 500,000 per run. The limit of 500,000 rows applies to each legal table, because each legal entity runs separately. For more information, see [Integrate data into Dataverse](/power-platform/admin/data-integrator). In particular, pay attention to the note that states, "To optimize performance and not overload the apps, we currently limit project executions to 500k rows per execution per project."

If there must be more than 500,000 rows in a run when you the initial synchronization, we recommend that you migrate data into the Finance and Operations app and Dataverse separately, and skip the initial synchronization.

### Twenty-four-hour limit

If you're running the initial synchronization from Dataverse to the Finance and Operations app, the import result must be received back from the Finance and Operations app within 24 hours. Otherwise, a time-out occurs. Therefore, if you're syncing lots of data, and the single run takes more than 24 hours, the initial synchronization might fail because of a time-out. For example, an initial synchronization from Dataverse to a Finance and Operations app for the **Customer/Account** table involves 70,000 rows. Therefore, the run might take more than 24 hours and time out.

Don't run the initial synchronization from Dataverse to a Finance and Operations app for [single-threaded tables](#single-threaded-entities) if the data volume is more than 70,000 rows. Because these tables don't support multi-threading during import, a time-out might occur if the volume is more 70,000 rows. In this situation, you should migrate data into the Finance and Operations app and Dataverse separately, and skip the initial synchronization.

### Limit of 40 legal entities while the environments are being linked

Currently, there is a limit of 40 legal entities while the environments are being linked. If you try to enable maps where more than 40 legal entities are linked between the environments, you will receive the following error message:

```console
Dual-write failure - Plugin registration failed: [(Unable to get partition map for project DWM-1ae35e60-4bc2-4905-88ea-XXXXX. Error Exceeds the maximum partitions allowed for mapping DWM-1ae35e60-4bc2-4905-88ea- XXXXX)], One or more errors occurred.
```

### Initial synchronization isn't currently supported for table maps that have 10 or more lookups

This limitation applies only to the initial synchronization from Dataverse for table maps that have 10 or more lookups. If you run the initial synchronization against a table map that has 10 or more lookups, you might receive the following error message:

```console
5 Attempts to get data from https://XXXX.azure-apim.net/apim... Failed
```

As a workaround you can split the initial sync into these steps:

1. Remove some of the lookup columns that are not mandatory from the dual-write table map and bring the number of lookups to 10. 
2. After the lookup columns are removed, save the map and do the initial sync. 
3. After the initial sync for the first step is successful, add the remaining lookup columns and remove the lookup columns that were synced in first step. Once again make sure the number of lookup columns is 10. Save the map and run the initial sync. Repeat these steps to make sure all the lookup columns are synced. 
4. Add all the lookup columns back to the map, save the map and run the map with skip initial sync. This will enable the map for live sync mode.

### Five-minute limit for Finance and Operations data export

If you're running the initial synchronization from the Finance and Operations app to Dataverse and the Finance and Operations data export takes more than five minutes, then the initial sync might time out. The time-out can happen if the data table has virtual columns with the `postLoad` method, or the export query isn't optimized (for example, if it has missing indexes).

This type of synchronization is supported in Platform update 37 (PU37) and later. Therefore, you should update your Finance and Operations app to PU37 or later.

### Security role for write access

Every user in a customer engagement organization with dual-write must be added to the **Dual-Write Runtime User** role. Without this role, users will be unable to create any rows in tables in the customer engagement organization.

### Company and Currency Exchange Tables Required Security Role

Company and currency exchange tables are global in nature and all dual-write users require read access to these 2 tables. To provide access, all dual-write users will need to be added to the **Dual-Write App User** security role. If a user does not have this security role assigned to them, they will be unable to read tables that contain Company and Currency values.

### Error handling capabilities

#### Initial synchronization is always a full push

If an individual row fails to be synced, you can't resync only that individual row. The initial synchronization always pushes the whole data set. This behavior is known as a *full push*. If the initial synchronization only partially succeeds, a second synchronization runs for all the rows, not just the rows that failed to be synced during the initial synchronization.

#### Only the top five errors can be viewed

You can view only the top five errors from the initial synchronization error log.

## Known issues

For information about known issues, see [Troubleshoot issues during initial synchronization](dual-write-troubleshooting-initial-sync.md).

## Guidance matrix

<table>
<thead>
<tr>
<th>Finance and Operations app instance</th>
<th>Dataverse instance</th>
<th>Has data to run the initial synchronization</th>
<th>Description</th>
<th>Maximum volume in a table</th>
<th>Single-threaded or multi-threaded</th>
<th>Approach</th>
</tr>
</thead>
<tbody>
<tr>
<td>New</td>
<td>New</td>
<td>No</td>
<td>A new Finance and Operations app instance and a new customer engagement app instance, where neither app has initial data</td>
<td>Not applicable</td>
<td>Any</td>
<td>
<ul>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ul>
</td>
</tr>
<tr>
<td rowspan='3'>New</td>
<td rowspan='3'>New</td>
<td rowspan='3'>Yes</td>
<td rowspan='3'>A new Finance and Operations app instance and a new customer engagement app instance, where one of the apps has migrated data</td>
<td>&lt; 500,000</td>
<td><a href='#single-threaded-entities'>Single-threaded</a></td>
<td>
<ol>
<li>Migrate data to the Finance and Operations app.</li>
<li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&lt; 500,000</td>
<td>Multi-threaded</td>
<td>
<ol>
<li>Migrate data to Dataverse.</li>
<li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&gt; 500,000</td>
<td>Any</td>
<td>
<ol>
<li>Migrate data to each app outside the initial synchronization.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td rowspan='4'>New</td>
<td rowspan='4'>Existing</td>
<td rowspan='4'>Yes</td>
<td rowspan='4'>A new Finance and Operations app instance and an existing customer engagement app instance</td>
<td>&lt; 70,000</td>
<td><a href='#single-threaded-entities'>Single-threaded</a></td>
<td>
<ol>
<li>Create a new company in the Finance and Operations app.</li>
<li>Bootstrap Dataverse for the company code.</li
><li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&gt; 70,000</td>
<td><a href='#single-threaded-entities'>Single-threaded</a></td>
<td>
<ol>
<li>Create a new company in the Finance and Operations app.</li>
<li>Bootstrap Dataverse for the company code.</li>
<li>Migrate data to each app outside the initial synchronization.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&lt; 500,000</td>
<td>Multi-threaded</td>
<td>
<ol>
<li>Create a new company in the Finance and Operations app.</li>
<li>Bootstrap Dataverse for the company code.</li>
<li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&gt; 500,000</td>
<td>Any</td>
<td>
<ol>
<li>Create a new company in the Finance and Operations app.</li>
<li>Bootstrap Dataverse for the company code.</li>
<li>Migrate data to each app outside the initial synchronization.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td rowspan='2'>Existing</td>
<td rowspan='2'>New</td>
<td rowspan='2'>Yes</td>
<td rowspan='2'>An existing Finance and Operations app instance and a new customer engagement app instance</td>
<td>&lt; 500,000</td>
<td>Any</td>
<td>
<ul>
<li>Run the initial synchronization.</li>
</ul>
</td>
</tr>
<tr>
<td>&gt; 500,000</td>
<td>Any</td>
<td>
<ol>
<li>Migrate data to each app.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td rowspan='4'>Existing</td>
<td rowspan='4'>Existing</td>
<td rowspan='4'>Yes</td>
<td rowspan='4'>An existing Finance and Operations app instance and an existing customer engagement app instance</td>
<td>&lt; 70,000</td>
<td><a href='#single-threaded-entities'>Single-threaded</a></td>
<td>
<ol>
<li>Bootstrap Dataverse for the company code.</li>
<li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&gt; 70,000</td>
<td><a href='#single-threaded-entities'>Single-threaded</a></td>
<td>
<ol>
<li>Bootstrap Dataverse for the company code.</li>
<li>Migrate data to each app outside the initial synchronization.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&lt; 500,000</td>
<td>Multi-threaded</td>
<td>
<ol>
<li>Bootstrap Dataverse for the company code.</li>
<li>Run the initial synchronization.</li>
</ol>
</td>
</tr>
<tr>
<td>&gt; 500,000</td>
<td>Any</td>
<td>
<ol>
<li>Bootstrap Dataverse for the company code.</li>
<li>Migrate data to each app outside the initial synchronization.</li>
<li>Activate dual-write, and skip the initial synchronization.</li>
</ol>
</td>
</tr>
</tbody>
</table>

## <a id="single-threaded-entities"></a>Single-threaded tables

- Sales tax codes (msdyn\_taxcodes)
- Customers V3 (accounts)
- Vendors V2 (msdyn\_vendors)
- Warehouses (msdyn\_warehouses)
- Product categories (msdyn\_productcategories)
- Employment (cdm\_employments)
- Position worker assignments (cdm\_positionworkerassignmentmaps)
- Warehouse locations (msdyn\_inventorylocations)
- Modes of delivery (msdyn\_shipvias)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
