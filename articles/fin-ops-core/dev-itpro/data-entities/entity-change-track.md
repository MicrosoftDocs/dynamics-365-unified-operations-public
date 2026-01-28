---
title: Enable change tracking for entities
description: Learn about using change tracking to enable incremental export of data from finance and operations, including a table outlining how changes are tracked for various options.
author: Milindav2
ms.author: twheeloc
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: twheeloc
audience: IT Pro, Developer
ms.assetid: 434b5d9f-9877-4769-ad96-d4e8d460a7fa
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Enable change tracking for entities

[!include [banner](../includes/banner.md)]

By using change tracking, you can incrementally export data from finance and operations apps by using Data management. In an incremental export, you export only records that changed. To enable incremental export, enable change tracking on entities. If you don't enable change tracking on an entity, you can only enable a full export each time.

You can enable change tracking for both bring your own database (BYOD) and non-BYOD scenarios. This capability includes retrieving record changes through Dataverse virtual entities.

> [!NOTE]
> Change tracking tracks record deletion only for bring your own database (BYOD) and Dataverse virtual entity use cases, if the entity supports it. Other non-BYOD scenarios don't include tracking record deletion. Deletion is tracked only for the root data source in the entity.

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
    | Enable entire entity | Changes to any fields in any table in the entity trigger a change in the entity. |
    | Enable custom query  | Uses a custom query that identifies the tables on which changes must be tracked. The custom query is defined in the entity. |

    > [!NOTE]
    > If a change triggers change tracking, the change is tracked on the entire record and not at the field level. The entire entity record is exported to the destination. Regardless of the option that you select, the number of fields in the entity is the number that is exported to the destination.

## Enable change tracking for non-BYOD scenarios

You can enable change tracking for non-BYOD scenarios. This feature includes retrieving record changes through Dataverse virtual entities for finance and operations apps. When you enable change tracking for an entity, you can retrieve changes through the entity's OData endpoint by adding `odata.track-changes` as a preference header.

For more information on using change tracking for an entity, see [Use change tracking to synchronize data with external systems](/powerapps/developer/data-platform/use-change-tracking-synchronize-data-external-systems).

To enable change tracking for non-BYOD scenarios:

1. From the **Data management** workspace, select the **Data entities** list page.
1. Select the entity for which you want to enable change tracking.
1. Select the **Change tracking** action on the action ribbon, and select the desired option for how changes should be tracked for the entity. See the table in the [Enable change tracking for BYOD](#enable-change-tracking-for-byod) section for detail on the available options.

## Custom query for change tracking

The following example shows how to add a static method to an entity. Make sure that the method returns a query, and that the root node is the same as the entity. For example, for the Customer entity, the root node is `custTable`, and the change tracking query for its also `custTable`.

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
