---
# required metadata

title: Cross-company data sharing
description: This topic describes cross-company data sharing, which is a mechanism for sharing reference and group data among companies in a deployment.
author: ramasri
ms.date: 01/27/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysDataSharingConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 89071
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.region: Global
# ms.search.industry: 
ms.author: ramasri
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: Platform update 1

---

# Enable a table for cross-company data sharing

[!include [banner](../includes/banner.md)]

Enabling a table for data sharing is a 2-step process updating the metadata
property for the table.

1.  Open the table properties and set the "Data Sharing Type" property to
    "Single" or "Duplicate". (Single stands for single record sharing (SRS) and
    Duplicate stands for duplicate record sharing (DRS).

2.  For each field on the table defined as using SRS sharing, you need to set
    the "Single Data Sharing Type" metadata property to "Always" or "Never".
    (Always implies the field is shared always; Never implies the field is never
    shared. Don’t choose "Optional" since there is no related logic currently.

Note:

-   When a table is set as "Duplicate", it can participate in both DRS as well
    as SRS policies.

-   When a table is set to “Single”, it can participate in SRS policy only.

-   Once a table property is set to “Single”, it cannot be changed to
    “Duplicate”.This would be seen as a breaking change as SRS policies using
    the table would no longer be valid.

-   Once a policy is defined as Single record sharing, it cannot be disabled or
    changed to Duplicate record sharing.

-   When using SRS, fields set to “Never” will get the default value for the
    field’s type. You cannot update these fields to contain another value. E.g
    integer/real will contain a value of 0, strings will be empty, enumerations
    will be non-deterministic based on whether or not they are extensible.

-   Only required foreign key fields are selected by default. Optional foreign
    keys need to be selected manually to be included. The best practice is to
    add one or more tables when selecting a foreign key field, unless the table
    has already been added.

## How does it work?

When a table is enabled for data sharing, kernel logic auto-creates a view with
name "\<tablename\>_SharingView". This view should be used to access the shared
data.

Say for example, **CustGroup** table is enabled for data sharing and **USMF** is
chosen as master company and **CH1** and **CH2** are chosen as child companies.
Here is how the output looks when you read records from CustGroup (Phyiscal) and
CustGroup_SharingView.(View illustrates kernel logic, but is only used for
non-kernel based scenarios)

![SRS-image3](media/SRS-image3.png)

## Guidelines to enable data sharing on tables:
The ability to define or modify DRS, SRS settings applies to base tables provided by the current model. For example, it is not possible to modify existing table or field properties via an extension.

If a company specific table has Data Sharing Type = Single, it means it has already been evaluated for SRS. You can’t revert it to Duplicate or None.

If a company specific table has Data Sharing Type = Duplicate, it means it has already been evaluated for DRS. If you want to enable it for SRS, you need to evaluate its functional eligibility before changing the property to “Single”.

If a company specific table has Data Sharing Type = None, but you want to enable data sharing, then the recommendation is to enable it for DRS. Because a DRS table can participate in both DRS and SRS policies. It may not be possible for the sharing type to be DRS. The following information can be used to determine the appropriate setting.

+ If a company specific table is having a unique index or alternate key (AK), then apply DRS.
    +	If the table has foreign key (FK) field and the corresponding table is set to "Data Sharing Type" = "None", then set the "Single Data Sharing Type" property for that FK field to "Never".
    +	If the table has a surrogate foreign key (FK) field, then set the "Single Data Sharing Type" property for that field to "Never".
    +	If the table field is referencing any of the tables mentioned under limitation section then set the "Single Data Sharing Type" property to "Never".

+ If a company specific table doesn’t have a unique index or alternate key (AK), then apply SRS.
    +	If the table has a foreign key (FK) field and the corresponding table is set to "Data Sharing Type" = "None", then set the "Single Data Sharing Type" property for that FK field to "Never".
    +	If the table has a surrogate foreign key (FK) field, then set the "Single Data Sharing Type" property for that field to "Never".
    +	If the table field is referencing any of the tables mentioned under limitation section, then set the "Single Data Sharing Type" property to "Never".

> [!Note]
> Cross-company shared policy simulator detects the eligibility of a table and its fields along with table references associated with each field.

> Upon release, If the Data Sharing Type=Single, it cannot be changed to duplicate or None. Can't go back.

When a data sharing policy is set to DRS, it can’t be changed to Single. Likewise, when a policy is set to Single, it can’t be changed to Duplicate.

Once you setup the data sharing policies, you need to do a full DB sync which will recreate the _SharingView.

Data sharing is applicable for tables with “Save data per company” property set to Yes. Tables with “Save data per company” property set to No, are global and no additional sharing configuration is needed.

From a development perspective, it is not enough to look at the Primary and Alternate Key of a table to determine the sharing type. Additional work may be required to share the to enable sharing without causing data issues.


<table>
<thead>
<tr class="header">
<th>Method / Metadata</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="1">
<td>Relationships
<ul>
<li>Alternate key (AK)</li>
<li>Foreign (FK)</li>
<li>Sharing Type (Table and Fields)</li>
<li>DeleteActions (Restricted / Casacade)</li>
</ul>
</td>
<td><ul>Check the tables and fields, if they are required to be shared. 
What is the impact of DRS vs SRS sharing for the table and field</ul>
</td>
</tr>
<tr class="2">
<td>Validate methods
<ul>
<li>validateDelete</li>
<li>validateInsert</li>
<li>validateWrite</li>
<li>validateField</li>
<li>validateFieldValue</li>
</ul>
</td>
<td><ul>Logic might refer to table that is not shared e.g. transactions, therefore refactoring is required to handle the logic cross company.</ul>
</td>
</tr>
<tr class="3">
<td>Defaulting
<ul>
<li>initValue</li>
<li>defaultField</li>
</ul>
</td>
<td><ul>Check what logic is done in the defaulting, many places we initialize values from a none shared table, resulting in records being initialized different depending on the company the records is created. </ul>

<ul>Are there data dependencies not modeled? E.g, fields shared between tables and used for validation.  ProjCateory and ProjCategoryGroup have CategoryType field. There is a code level validation that the value is the same for the project category and the group assigned. If the fields are not included in the policy update of project category fails due to the validation check.</ul>
</td>
</tr>
<tr class="4">
<td>CRUD methods
<ul>
<li>delete</li>
<li>insert</li>
<li>update</li>
<li>write</li>
</ul>
</td>
<td><ul>Are there data dependencies not modeled?
Due to data model decisions, table metadata property “Save date company” may be set to “No”
<li>How are these tables related to data sharing tables?</li>
<li>The table contains DataAreaId as alternate field?
(example: InventItemGroupItem -> InventItemGroup)</li>
<li>Code needs to handle populating tables like this cross company.</li>
 </ul>
</td>
</tr>
<tr class="5">
<td>Design patterns using overloaded field values.</td>
<td><ul>In some tables there exists the pattern of two paired fields to indicate relationships. The most common usage is posting profiles.  There will be an enumeration field and then a field representing the AK from a referenced table.  e.g., ProjPosting table has the field ProjCode derived from the enumeration TableGroupAll and an associated field ProjRelationship which will store the natural key (AK) from ProjTable, ProjGroup or be empty. 
Tables with this pattern maybe shareable, but clear documentation will need to be provided as to all related tables and fields need to be included in the policy.</ul>
</td>
</tr>
    <tr class="6">
<td>LedgerDimensionDefaultAccount</td>
<td><ul>Tables using this EDT are typically storing the reference to a main account value.  These are not shareable.</ul>
</td>
</tr>
    <tr class="7">
<td>Number sequences</td>
<td><ul>Number sequences are typically setup per company. The defaulting logic fields using them will probably not work without code changes.</ul>
</td>
</tr>
</tbody>
</table>

The classes SysDataSharingCrossCompanyValidator, SysDataSharingCrossCompanyValidatorQueryBuilder and methods on the table SysDataSharingPolicy, can be used to determine if a table is being used in a data sharing policy. These typically are used in the CRUD and logic default methods to hand table dependencies.







