---
# required metadata

title: Enable change tracking for entities
description: Use change tracking to enable incremental export of data from Finance and Operations.
author: Milindav2
manager: AnnBe
ms.date: 11/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 265974
ms.assetid: 434b5d9f-9877-4769-ad96-d4e8d460a7fa
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.0

---
# Enable change tracking for entities

[!include [banner](../includes/banner.md)]

Change tracking enables incremental export of data from Finance and Operations by using Data management. In an incremental export, only records that have changed are exported. To enable incremental export, you must enable change tracking on entities. If you don't enable change tracking on an entity, you can only enable a full export each time. Although, change tracking can be enabled for BYOD and non-BYOD scenarios, it must be noted that only for bring your own database (BYOD) use cases, change tracking also tracks deletes if the entity supports this. Deletion is tracked only for the root data source in the entity.

## Enable change tracking for BYOD
You can enable change tracking when you publish one or more entities to a data store (BYOD).

1. In the **Data management** workspace, select **Configure entity export to database**.
2. Select the database to export data to, and then select **Publish**.

    You can publish one or more entities to your database. Select **Show published only** to see a list of entities that have previously been published.

3. Select an entity that is published, and then select **Change tracking**.
4. Select the appropriate option for change tracking for your environment.

    An entity can be modeled by using more than one table. The options let you specify the granularity at which changes can be tracked in an entity.

    | Option               | How changes are tracked |
    |----------------------|-------------------------|
    | Enable primary table | Changes that are made to any fields in the primary table trigger a change in entity. Changes that are made to fields in secondary tables don't trigger a change in entity. |
    | Enable entire entity | Changes that are made to any fields in any table in the entity trigger a change in entity. |
    | Enable Custom query  | Select a set of custom fields from any tables that must trigger a change in entity. |

    > [!NOTE]
    > If a change is triggered, the change is tracked on the entire record and not at the field level. The entire entity record is exported to the destination. Regardless of the option that you select, the number of fields in the entity is the number that is exported to the destination.

## Enable change tracking for non-BYOD scenarios
For non-BYOD scenarios, change tracking can be enabled from the data entities list page in data management by selecting the entities and clicking **Change tracking**.

## Custom query for change tracking
The following example shows how to add a static method to an entity. You must make sure that the method returns a query, and that the root node is the same as the entity. For example, for the Customer entity, the root node is custTable, and the change tracking query for it is also custtable.

- You must enable change tracking on the tables that are part of the query.
- Create a join between the entity and the change tracking query (on the root table) to determine which records have changed in the entity.

```xpp
public static Query defaultCTQuery()
    {
        Query q;
        q = new Query();
        QueryBuildDataSource qbd = q.addDataSource(tablename2id('CustTable'));
        qbd = qbd.addDataSource(tablename2id('DirPartyTable'));
        qbd.relations(true);
        qbd = qbd.addDataSource(tablename2id('DirPartyLocation'));
        qbd.addRange(fieldname2id(tablename2id('DirPartyLocation'),'IsPrimary')).value("1");
        qbd.relations(false);
        qbd.addLink(fieldName2Id(tableName2Id('DirPartyTable'),'RecId'),fieldName2Id(tableName2Id('DirPartyLocation'),'Party'));
        qbd = qbd.addDataSource(tableName2Id('LogisticsPostalAddress'));
        qbd.relations(false);
        qbd.addLink(fieldName2Id(tableName2Id('DirPartyLocation'),'Location'),fieldName2Id(tableName2Id('LogisticsPostalAddress'),'Location'));
        return q;
    }
```
