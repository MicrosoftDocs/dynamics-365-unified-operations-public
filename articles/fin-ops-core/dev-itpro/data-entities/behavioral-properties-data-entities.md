---
# required metadata

title: Behavioral properties on data entities
description: This article describes data entity properties that let you override property values on the tables or views that are the data sources of that entity. 
author: peakerbl
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 8e214c95-616b-4ee1-b5a4-fa5ce5147f2c
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Behavioral properties on data entities

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Every data entity has properties that let you override the same property values on the tables or views that are the data sources of that entity. Your choices affect the behavior of the entity. In the following table, the first column lists the properties that are discussed in this article. The top row lists the levels where the property is found in the entity designer. The levels are listed in order of increasing granularity: the data source level is more granular than the entity level but less granular than the field level.

|  &nbsp;           | Entity level | Data source level | Field level |
|-------------------|--------------|-------------------|-------------|
| ReadOnly          | Applies      | Applies           | .           |
| AllowEdit         | .            | .                 | Applies     |
| AllowEditOnCreate | .            | .                 | Applies     |
| Mandatory         | .            | .                 | Applies     |

## Entity level
In the designer for your data entity, when you click the name at the root node, the **Properties** pane includes the **Is Read Only** property. The following table describes the behavioral differences between the **Yes** and **No** values of this property.

<table>
<thead>
<tr>
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Values</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Behavior</td>
<td>IsReadOnly</td>
<td>Is Read Only</td>
<td>No, Yes</td>
<td>No</td>
<td><ul>
<li><strong>No:</strong> Data modification operations (CUD) <em>are</em> allowed, <em>unless</em> an individual data source node in the entity's designer is set to <strong>IsReadOnly</strong> = <strong>Yes</strong>.</li>
<li><strong>Yes:</strong> Only read operations are allowed, regardless of the <strong>IsReadOnly</strong> settings on the individual data source nodes in the entity's designer.</li>
</ul></td>
</tr>
</tbody>
</table>

You would set **IsReadOnly** to **Yes** for entities that are consumed mainly for export.

## Data source level
If a data entity has three data sources, you might want to allow processes to use the entity to modify the data in one of the data sources but not in the other two. A read-only data source can be used for lookup purposes. You can use the entity designer to achieve this extra degree of granular control. Under the entity's **Metadata** &gt; **Data Sources** node, you can select an entity node and then set the **IsReadOnly** property value for that one data source. The following table describes the interaction between the **IsReadOnly** settings at the data source level and the entity level.

<table>
<thead>
<tr>
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Values</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Behavior</td>
<td>IsReadOnly</td>
<td>Is Read Only</td>
<td>No, Yes</td>
<td>No</td>
<td><ul>
<li><strong>No:</strong> Data modification operations (CUD) <em>are</em> allowed on the data source, <em>unless</em> <strong>IsReadOnly</strong> is set to <strong>Yes</strong> at the entity level.</li>
<li><strong>Yes:</strong> Only operations are allowed, regardless of the <strong>IsReadOnly</strong> setting on the entity.</li>
</ul></td>
</tr>
</tbody>
</table>

## Field level
At the field level, the **AllowEdit** and **AllowEditOnCreate** properties are available instead of an **IsReadOnly** property. The two **Allow** properties include **Auto** as a third available value. The **Auto** value inherits the value that is on the field in the underlying table.

> [!NOTE]
> The **Auto** value isn't available for unmapped fields, such as computed or virtual fields.

<table>
<thead>
<tr>
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Value</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Behavior</td>
<td>AllowEditOnCreate</td>
<td>Allow edit on create</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td><ul>
<li><strong>Auto:</strong> The property is inherited from the underlying table field.
<strong>Note:</strong>  The <strong>Auto</strong> value isn't available for unmapped fields, such as computed or virtual fields.
</li>
<li><strong>No:</strong> Users aren't allowed to modify the data for this field in a new record.</li>
<li><strong>Yes:</strong> Users are allowed to modify the data for this field for a new record.</li>
</ul>
This behavior is enforced for all consumers – X++, OData, and so on.
<strong>Important:</strong>  The <strong>No</strong> and <strong>Yes</strong> values do <em>not</em> override the setting on the field in the underlying table.</td>
</tr>
<tr>
<td>Behavior</td>
<td>AllowEdit</td>
<td>Allow edit</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td>The behavior is the same as the behavior for <strong>AllowEditOnCreate</strong>, but it applies to updates to <em>existing</em> records instead of new records that are being created. This behavior is enforced for all consumers – X++, OData, and so on.</td>
</tr>
<tr>
<td>Behavior</td>
<td>Mandatory</td>
<td>Mandatory</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td><strong>Auto:</strong> The property is inherited from the underlying table field. This behavior is enforced for all consumers – X++, OData, and so on.
<strong>Important:</strong>  The <strong>No</strong> and <strong>Yes</strong> values do <em>not</em> override the setting on the field in the underlying table.</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
