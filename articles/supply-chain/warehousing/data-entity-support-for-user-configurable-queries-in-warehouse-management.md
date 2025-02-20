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

One of the challenges with the user-configurable queries has been the interaction with the data entities. As the queries are packed in a way that is not readable by the user, it was difficult to make changes to them through the data entities. This has been solved with the introduction of the special JSON fields to the warehouse data entities which have user-configurable queries. All the relevant warehouse entities have been updated with the JSON field support.

## Example

As an example, we are going to use a newly created **Location directive actions** query.

### Setup location directive action
1. Open the **Location directives** form (**Warehouse management** > **Setup** > **Location directives**).
1. Set **Work order type** to *Sales orders*.
1. Click **New** in the **Action Pane** to create a new location directive.
1. Set **Name** to *JSON test*.
1. Set **Work type** to **Pick**.
1. Click **Save** in the **Action Pane**.
1. Click **New** in the **Lines** fast tab.
1. Set **To quantity** to *999*.
1. Click **Save** in the **Action Pane**.
1. Click **New** in the **Location Directive Actions** fast tab.
1. Set **Name** to *JSON test action*.
1. Click **Save** in the **Action Pane**.
1. Follow the [Data entities overview](/fin-ops-core/dev-itpro/data-entities/data-entities.md) guide to setup the data entities.
1. Export the newly created location directive action with the *Warehouse location directive line actions V3* data entity, for example in the *XML-Element* format.

### Review the exported file

If you open the exported XML file, it's content will look something like below. Notice the new *ACTIONQUERYJSON* field.

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

The new JSON field contains all the tables, relations, sortings and ranges in a user-readable format. Learn more in [User-configurable queries in warehouse management](warehousing/user-configurable-queries-in-warehouse-management.md) article.
