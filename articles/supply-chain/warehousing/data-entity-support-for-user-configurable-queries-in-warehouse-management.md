---
title: Data entity support for user-configurable queries in warehouse management
description: Learn how to use data entities with user-configurable queries in warehouse management.
author: ivanma
ms.author: ivanma
ms.topic: article
ms.date: 02/20/2025
ms.reviewer: kamaybac
ms.search.form: DataManagementWorkspace, WHSWaveTemplateTable, WHSWorkTemplateTable, WHSLocDirTable, WHSLaborStandards, WHSDocumentRouting, WHSWaveLabelTemplate, WHSWaveLabelLayout, WHSLabelLayoutDataSource, WHSContainerLabelRouting, WHSWaveFilterTable, WHSRFMenuItem, WHSClusterProfile, WHSLoadBuildTemplate, WHSCrossDockingTemplate, WHSContainerizationTable, WHSReplenishmentTemplates, WHSSlotTemplate, WHSOutboundSortTemplate, WHSCycleCountPlan, WHSCycleCountThreshold, WHSShipConsolidationPolicy, WHSShipConsolidationTemplate
---

# Data entity support for user-configurable queries in warehouse management

One challenge of user-configurable queries is the interaction with data entities. Because the queries are packed in a way that isn't readable by users, it's difficult to make changes to them through the data entities. To address this issue, special JavaScript Object Notation (JSON) fields are added to the warehouse data entities that have user-configurable queries. All relevant warehouse entities are updated with support for these JSON fields.

## Example

This article uses the example of a newly created *Location directive actions* query.

### Set up a location directive action

To set up a location directive action, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Location directives**.
1. In the **Work order type** field, select *Sales orders*.
1. On the Action Pane, select **New** to create a location directive.
1. In the **Name** field, enter *JSON test*.
1. In the **Work type** field, select *Pick*.
1. Select **Save**.
1. On the **Lines** FastTab, select **New**.
1. In the **To quantity** field, enter *999*.
1. Select **Save**.
1. On the **Location Directive Actions** FastTab, select **New**.
1. In the **Name** field, enter *JSON test action*.
1. Select **Save**.
1. Set up the data entities. Learn more in [Data entities overview](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).
1. Export the new location directive action with the *Warehouse location directive line actions V3* data entity, for example, in the *XML-Element* format.

### Review the exported file

If you open the exported XML file, its content should resemble the following example.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSWAREHOUSELOCATIONDIRECTIVELINEACTIONV3ENTITY>
        <ACTIONNAME>JSON test action</ACTIONNAME>
		<WAREHOUSELOCATIONDIRECTIVEID>JSON test</WAREHOUSELOCATIONDIRECTIVEID>
		<WAREHOUSELOCATIONDIRECTIVEWORKTYPE>Pick</WAREHOUSELOCATIONDIRECTIVEWORKTYPE>
		<WAREHOUSELOCATIONDIRECTIVEWORKORDERTYPE>Sales</WAREHOUSELOCATIONDIRECTIVEWORKORDERTYPE>
		<WAREHOUSELOCATIONDIRECTIVEINVENTORYSITEID/>
		<WAREHOUSELOCATIONDIRECTIVEWAREHOUSEID/>
		<WAREHOUSELOCATIONDIRECTIVELINESEQUENCENUMBER>1</WAREHOUSELOCATIONDIRECTIVELINESEQUENCENUMBER>
		<ACTIONQUERYJSON><![CDATA[{"table":"WMSLocation","name":"WMSLocation","firstOnly":false,"fetchMode":1,"type":"InnerJoin","fields":["inventLocationId","LocProfileId","wMSLocationId"],"links":[],"ranges":[{"field":"wMSLocationId","rangeStatus":"Open"},{"field":"inventLocationId","rangeStatus":"Locked"}],"joins":[{"table":"InventSum","name":"InventSum","firstOnly":false,"fetchMode":0,"type":"InnerJoin","fields":["configId","InventBatchId","InventColorId","InventDimension1","InventDimension10","InventDimension11","InventDimension12","InventDimension2","InventDimension3","InventDimension4","InventDimension5","InventDimension6","InventDimension7","InventDimension8","InventDimension9","InventDimId","InventGtdId_RU","InventLocationId","InventOwnerId_RU","InventProfileId_RU","InventSerialId","InventSiteId","InventSizeId","InventStatusId","InventStyleId","InventVersionId","ItemId","LicensePlateId","PhysicalInvent","wMSLocationId","wMSPalletId"],"links":[{"field":"inventLocationId","relatedField":"InventLocationId","table":"WMSLocation","relatedTable":"InventSum","joinRelation":""},{"field":"wMSLocationId","relatedField":"wMSLocationId","table":"WMSLocation","relatedTable":"InventSum","joinRelation":""}],"ranges":[{"field":"PhysicalInvent","value":">0","rangeStatus":"Locked"},{"field":"ItemId","rangeStatus":"Open"},{"field":"ClosedQty","value":"No","rangeStatus":"Locked"}]}]}]]></ACTIONQUERYJSON>
        <ACTIONSEQUENCENUMBER>1</ACTIONSEQUENCENUMBER>
        <ACTIONSTRATEGY>None</ACTIONSTRATEGY>
        <FIXEDLOCATIONUSAGEMETHOD>Any</FIXEDLOCATIONUSAGEMETHOD>
        <ISITEMBATCHENABLED>No</ISITEMBATCHENABLED>
        <ISNEGATIVEINVENTORYALLOWED>No</ISNEGATIVEINVENTORYALLOWED>
    </WHSWAREHOUSELOCATIONDIRECTIVELINEACTIONV3ENTITY>
</Document>
```

Notice the `ACTIONQUERYJSON` field. This new JSON field contains all the tables, relations, sortings, and ranges in a user-readable format. Learn more in [User-configurable queries in warehouse management](user-configurable-queries-in-warehouse-management.md).
