---
title: Enable SQL change tracking for data entities
description: Learn how to enable SQL change tracking for incremental exports of finance and operations data entities in Data management.
author: Milindav2
ms.author: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/26/2026
ms.reviewer: twheeloc
audience: IT Pro, Developer
ms.assetid: 434b5d9f-9877-4769-ad96-d4e8d460a7fa
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Enable SQL change tracking for data entities

[!INCLUDE [banner](../includes/banner.md)]

This article describes the SQL Server Change Tracking mechanism that you configure from the **Data management** workspace. By using SQL change tracking, you can incrementally export data from finance and operations apps. In an incremental export, you export only records that changed. If you don't enable SQL change tracking on an entity, you can only enable a full export each time.

You can enable SQL change tracking for both bring your own database (BYOD) and non-BYOD exports in Data management.

For the separate row version mechanism, see [Row version change tracking for tables and data entities](rowversion-change-track.md). For the table exclusions that apply to each mechanism, see [Table eligibility for change tracking](change-tracking-table-eligibility.md).

> [!NOTE]
> For Data management exports, record deletion is tracked only for BYOD, and only for the root data source in the entity. Non-BYOD exports don't include tracking record deletion. For row version deletion tracking, see [Track deletions and cleanup](rowversion-change-track.md#track-deletions-and-cleanup).

## Requirements for SQL change tracking

Before enabling SQL change tracking, check the [SQL table eligibility restrictions and export performance guidance](change-tracking-table-eligibility.md#sql-change-tracking).

SQL Server Change Tracking must also be enabled for the finance and operations database. Finance and operations services manage this configuration. Use the following application procedures rather than running SQL statements against the application database.

## Enable change tracking for BYOD

You can enable change tracking when you publish one or more entities to a data store (BYOD).

1. In the **Data management** workspace, select **Configure entity export to database**.
1. Select the database to export data to, and then select **Publish**.

    You can publish one or more entities to your database. Select **Show published only** to see a list of entities that you previously published.

1. Select an entity that you published, and then select **Change tracking**.
1. Select the appropriate option for change tracking for your environment.

    An entity can use more than one table. These options specify the granularity at which you can track changes in an entity.

    | Option               | How changes are tracked |
    |----------------------|-------------------------|
    | Enable primary table | Changes to any fields in the primary table trigger a change in the entity. Changes to fields in secondary tables don't trigger a change in the entity. |
    | Enable entire entity | Changes to any fields in the eligible tracked tables in the entity trigger a change in the entity. Table eligibility restrictions still apply. |
    | Enable custom query  | Uses a custom query that identifies the tables on which changes must be tracked. The custom query is defined in the entity. |

    > [!NOTE]
    > If a change triggers change tracking, the change is tracked on the entire record and not at the field level. The entire entity record is exported to the destination. Regardless of the option that you select, the number of fields in the entity is the number that is exported to the destination.

## Enable change tracking for non-BYOD scenarios

You can enable SQL change tracking for incremental exports to non-BYOD destinations in Data management.

> [!NOTE]
> For the row version change tracking setup for Dataverse virtual tables, see [Track changes for finance and operations virtual tables in Dataverse](../power-platform/track-changes-fin-ops-virtual-table.md).

To enable change tracking for non-BYOD scenarios:

1. From the **Data management** workspace, select the **Data entities** list page.
1. Select the entity for which you want to enable change tracking.
1. Select the **Change tracking** action on the action ribbon, and select the option for how changes should be tracked for the entity. For details about the available options, see the table in the [Enable change tracking for BYOD](#enable-change-tracking-for-byod) section.

## Custom query for change tracking

The following example shows how to add a static method to an entity. Ensure that the method returns a query and that the root node is the same as the entity. For example, for the Customer entity, the root node is `CustTable`, and the change tracking query also uses `CustTable` as its root.

- Enable change tracking on the tables that are part of the query.
- Create a join between the entity and the change tracking query (on the root table) to determine which records changed in the entity.

```xpp
public static Query defaultCTQuery()
{
 Query q = new Query();    
    
 QueryBuildDataSource custDs = q.addDataSource(tableNum(CustTable));

 QueryBuildDataSource partyDs = custDs.addDataSource(tableNum(DirPartyTable));
 partyDs.relations(true);

 QueryBuildDataSource locationDs = partyDs.addDataSource(tableNum(DirPartyLocation));
 locationDs.addRange(fieldNum(DirPartyLocation, IsPrimary)).value(queryValue(NoYes::Yes));        
 locationDs.addLink(fieldNum(DirPartyTable, RecId), fieldNum(DirPartyLocation, Party));

 QueryBuildDataSource addressDs = locationDs.addDataSource(tableStr(LogisticsPostalAddress));        
 addressDs.addLink(fieldNum(DirPartyLocation, Location), fieldNum(LogisticsPostalAddress, Location));

 return q;
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
