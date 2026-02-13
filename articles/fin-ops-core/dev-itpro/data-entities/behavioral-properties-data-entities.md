---
title: Behavioral properties on data entities
description: This article describes data entity properties that let you override property values on the tables or views that are the data sources of that entity. 
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 10/29/2025
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: 8e214c95-616b-4ee1-b5a4-fa5ce5147f2c
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Behavioral properties on data entities

[!include [banner](../includes/banner.md)]

Every data entity has properties that let you override the same property values on the tables or views that are the data sources of that entity. Your choices affect the behavior of the entity. In the following table, the first column lists the properties discussed in this article. The top row lists the levels where the property is found in the entity designer. The levels are listed in order of increasing granularity: the data source level is more granular than the entity level but less granular than the field level.

|  &nbsp;           | Entity level | Data source level | Field level |
|-------------------|--------------|-------------------|-------------|
| ReadOnly          | Applies      | Applies           | .           |
| AllowEdit         | .            | .                 | Applies     |
| AllowEditOnCreate | .            | .                 | Applies     |
| Mandatory         | .            | .                 | Applies     |

## Entity level

In the designer for your data entity, when you select the name at the root node, the **Properties** pane includes the **Is Read Only** property. The following table describes the behavioral differences between the **Yes** and **No** values of this property.

| Group | Property name | Display name | Values | Default | Description |
|-------|---------------|--------------|--------|---------|-------------|
| Behavior | IsReadOnly | Is Read Only | No, Yes | No | <ul><li><strong>No:</strong> Data modification operations (CUD) *are* allowed, *unless* an individual data source node in the entity's designer is set to <strong>IsReadOnly</strong> = <strong>Yes</strong>.</li><li><strong>Yes:</strong> Only read operations are allowed, regardless of the <strong>IsReadOnly</strong> settings on the individual data source nodes in the entity's designer.</li></ul> |

You would set **IsReadOnly** to **Yes** for entities that are consumed mainly for export.

## Data source level

If a data entity has three data sources, you might want to allow processes to use the entity to modify the data in one of the data sources but not in the other two. A read-only data source can be used for lookup purposes. You can use the entity designer to achieve this extra degree of granular control. Under the entity's **Metadata** &gt; **Data Sources** node, you can select an entity node and then set the **IsReadOnly** property value for that one data source. The following table describes the interaction between the **IsReadOnly** settings at the data source level and the entity level.

| Group | Property name | Display name | Values | Default | Description |
|-------|---------------|--------------|--------|---------|-------------|
| Behavior | IsReadOnly | Is Read Only | No, Yes | No | <ul><li><strong>No:</strong> Data modification operations (CUD) <em>are</em> allowed on the data source, <em>unless</em> <strong>IsReadOnly</strong> is set to <strong>Yes</strong> at the entity level.</li><li><strong>Yes:</strong> Only read operations are allowed, regardless of the <strong>IsReadOnly</strong> setting on the entity.</li></ul> |

## Field level

At the field level, the **AllowEdit** and **AllowEditOnCreate** properties are available instead of an **IsReadOnly** property. The two **Allow** properties include **Auto** as a third available value. The **Auto** value inherits the value that is on the field in the underlying table.

> [!NOTE]
> The **Auto** value isn't available for unmapped fields, such as computed or virtual fields.

| Group | Property name | Display name | Value | Default | Description |
|-------|---------------|--------------|-------|---------|-------------|
| Behavior | AllowEditOnCreate | Allow edit on create | Auto, No, Yes | Auto | <ul><li><strong>Auto:</strong> The property is inherited from the underlying table field. <strong>Note:</strong> The <strong>Auto</strong> value isn't available for unmapped fields, such as computed or virtual fields.</li><li><strong>No:</strong> Users aren't allowed to modify the data for this field in a new record.</li><li><strong>Yes:</strong> Users are allowed to modify the data for this field for a new record.</li></ul>This behavior is enforced for all consumers—X++, OData, and so on. <strong>Important:</strong> The <strong>No</strong> and <strong>Yes</strong> values don't override the setting on the field in the underlying table. |
| Behavior | AllowEdit | Allow edit | Auto, No, Yes | Auto | The behavior is the same as the behavior for <strong>AllowEditOnCreate</strong>, but it applies to updates to <em>existing</em> records instead of new records being created. This behavior is enforced for all consumers – X++, OData, and so on. |
| Behavior | Mandatory | Mandatory | Auto, No, Yes | Auto | <strong>Auto:</strong> The property is inherited from the underlying table field. This behavior is enforced for all consumers—X++, OData, and so on. <strong>Important:</strong> The <strong>No</strong> and <strong>Yes</strong> values don't override the setting on the field in the underlying table. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
