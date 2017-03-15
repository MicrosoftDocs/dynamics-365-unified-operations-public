---
# required metadata

title: Metadata properties - ReadOnly, AllowEdit, Mandatory
description: This article covers the behavioral properties of metadata for ReadOnly, AllowEdit, and Mandatory. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-04 21 - 45 - 18
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 17911
ms.assetid: d53c5fdd-5da7-4cc5-b9b1-a6959ab47547
ms.search.region: Global
# ms.search.industry: 
ms.author: kuntalme
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Metadata properties - ReadOnly, AllowEdit, Mandatory

This article covers the behavioral properties of metadata for ReadOnly, AllowEdit, and Mandatory. 

Behavioral properties on data entities
--------------------------------------

Each data entity has certain properties that give you the option to override the same property values on the tables or views that are the data sources of the entity. Your choices affect the behaviors of the entity. In the following table, the left column lists the properties that are discussed in this topic. The top row lists the level where the property is found in entity designer. The data source level is more granular than the entity level and less granular than the field level. You can find a complete list of properties by examining the data entity in Visual Studio.

| Property          | Entity level | Data source level | Field level |
|-------------------|--------------|-------------------|-------------|
| ReadOnly          | Applies      | Applies           |             |
| AllowEdit         |              |                   | Applies     |
| AllowEditOnCreate |              |                   | Applies     |
| Mandatory         |              |                   | Applies     |

[ ](http://dynamics/teams/Server/Rainier/Shared%20Documents/Data%20Management%20Platform/Data%20Entity%20Uptake/Workshop/Metadata%20properties.xlsx)

### Entity level

In the designer for your data entity, when you click the name at its root node, the **Properties** pane includes the **Is Read Only** property. The following table describes the behavioral differences between the **Yes** and **No** values.

<table style="width:100%;">
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Values</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Behavior</td>
<td>IsReadOnly</td>
<td>Is Read Only</td>
<td>No, Yes</td>
<td>No</td>
<td><ul>
<li><strong>No</strong> – Data modification operations (CUD) <em>are</em> allowed, <em>unless</em> an individual data source node in the entity’s designer is set to <strong>IsReadOnly</strong> = <strong>Yes</strong>.</li>
<li><strong>Yes</strong> – <em>Only</em> read operations are allowed, <em>regardless</em> of the <strong>IsReadOnly</strong> settings on the individual data source nodes in the entity’s designer.</li>
</ul></td>
</tr>
</tbody>
</table>

**IsReadOnly** = **Yes** would be used for entities that would be consumed mainly for export.

### Data source level

When a data entity has three data sources, you might want to enable processes to use the entity to modify the data in only one of the data sources while disallowing data modification for the remaining data sources. A read-only data source would be used for lookup purposes. You can use the entity designer to achieve this extra degree of granular control. Under the entity’s **Metadata** &gt; **Data Sources** node, you can highlight any entity node and then set the **IsReadOnly** property value for that data source. The following table describes the interaction between the **IsReadOnly** settings at the data source level versus the entity level.

<table style="width:100%;">
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Values</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Behavior</td>
<td>IsReadOnly</td>
<td>Is Read Only</td>
<td>No, Yes</td>
<td>No</td>
<td><ul>
<li><strong>No</strong> – Data modification operations (CUD) <em>are</em> allowed on the data source, <em>unless</em> <strong>IsReadOnly</strong> = <strong>Yes</strong> is set at the entity level.</li>
<li><strong>Yes</strong> – <em>Only</em> read operations are allowed, <em>regardless</em> of the <strong>IsReadOnly</strong> setting on the entity.</li>
</ul></td>
</tr>
</tbody>
</table>

#### Scenario

Suppose the FMCustomerEntity entity has a second data source of FMCustGroup. Additionally, the FMCustomer table has a foreign key field named CustGroup that references the FMCustGroup, and the relation is N:1. Because the entity is for a customer, it's reasonable to allow use of the entity for data modifications to the FMCustomer data source. However, FMCustGroup is added as a data source for lookup to allow surrogate foreign key (SFK) expansion to the natural key. When a customer is inserted/updated, the intention isn't to insert/update attributes on customer group. In this scenario, you set **IsReadOnly** = **No** at the entity level and FMCustomer data source level. In the entity designer, at the data source level, you set **IsReadOnly** = **Yes** on the FMCustGroup. In this scenario, an entity field from the FMCustGroup data source, such as the **CustomerGroupDescription** field, isn't updatable through the entity. However, entity fields from FMCustomer can be updated through the entity.

#### 

### Field level

At the field level, the **AllowEdit** and **AllowEditOnCreate** properties are available in place of an **IsReadOnly** property. The two **Allow\*** properties add **Auto** as a third available value. The **Auto** value inherits the value that is on the field in the underlying table. **Note:** The **Auto** value isn't available for unmapped fields (that is, computed or virtual fields).

<table style="width:100%;">
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Property name</th>
<th>Display name</th>
<th>Value</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Behavior</td>
<td>AllowEditOnCreate</td>
<td>Allow edit on create</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td><ul>
<li><strong>Auto</strong> – Inherit the property from the underlying table field. <strong>Note:</strong> The <strong>Auto</strong> value isn't available for unmapped fields (computed or virtual fields).</li>
<li><strong>No</strong> – Users <em>are <strong>not</strong></em> allowed to modify the data for this field in a new record.</li>
<li><strong>Yes</strong> – Users <em>are</em> allowed to modify the data for this field for a new record.</li>
</ul>
This is enforced for all consumers (X++, OData, and so on). <strong>Important:</strong> A value of <strong>No</strong> or <strong>Yes</strong> does <strong>not</strong> override the setting on the field in the underlying table. If entity values are less restrictive than table fields, a BP warning is thrown.</td>
</tr>
<tr class="even">
<td>Behavior</td>
<td>AllowEdit</td>
<td>Allow edit</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td>The same as for <strong>AllowEditOnCreate</strong>, except it applies to updates to <em>existing</em> records instead of new records that are being created. This is enforced for all consumers (X++, OData, and so on).</td>
</tr>
<tr class="odd">
<td>Behavior</td>
<td>Mandatory</td>
<td>Mandatory</td>
<td>Auto, No, Yes</td>
<td>Auto</td>
<td><strong>Auto</strong> – Inherit the property from the underlying table field. This is enforced for all consumers (X++, OData, and so on).<strong>Important:</strong> A value of <strong>No</strong> or <strong>Yes</strong> does <strong>not</strong> override the setting on the field in the underlying table.</td>
</tr>
</tbody>
</table>



