---
title: Cross-company data sharing for developers
description: This article describes cross-company data sharing for developers. This is a mechanism for sharing reference and group data among companies in a deployment.
author: RamaKrishnamoorthy
ms.date: 02/16/2022
ms.topic: article
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.form: SysDataSharingConfiguration
---

# Cross-company data sharing for developers

[!include [banner](../includes/banner.md)]

This article describes cross-company data sharing for developers. Cross-company data sharing is a mechanism for sharing reference and group data among companies in a deployment.

## Enable a table for cross-company data sharing

Enabling a table for data sharing is a two-step process that requires updating the metadata
property for the table. To enable a custom table for cross-company data sharing, follow these steps: 

1.  Open the table properties and set the **Data Sharing Type** property to
    **Single** or **Duplicate**. **Single** stands for single record sharing (SRS) and
    **Duplicate** stands for duplicate record sharing (DRS).

2.  For each field on the table, you need to review 
    the **Single Data Sharing Type** metadata property. **Always** is the default value and implies the field is shared always. **Never** implies the field is never
    shared. Don’t choose **Optional** as there is currently no related logic.

> [!NOTE]
> -   When a table is set as **Duplicate**, it can participate in both DRS as well
    as SRS policies.
> - When a table is set to **Single**, it can participate in SRS policy only.
> - When a table property is set to **Duplicate**, it cannot be changed to
    **Single**. This would be seen as a breaking change as DRS policies using
    the table would no longer be valid.
> - When using SRS, fields set to **Never** will get the default value for the
    field’s type in all child companies. You cannot update these fields in a child company to contain another value. For example,
    integer/real will contain a value of 0, strings will be empty, enumerations
    will be non-deterministic based on whether they are extensible.

## How does it work?

When a table is enabled for data sharing, kernel logic auto-creates a view with
name "\<tablename\>_SharingView". This view should be used for non-kernel based access to the shared
data.

In the following example, the **CustGroup** table is enabled for data sharing and **USMF** is
selected as the master company, and **CH1** and **CH2** are the child companies.
The output will look like this when you read records from CustGroup (Physical) and
CustGroup_SharingView. (*View* illustrates kernel logic, but is only used for
non-kernel based scenarios)

![Single record sharing example.](media/SRS-image3.png)

## Guidelines to enable data sharing on tables
The ability to define or modify DRS or SRS settings applies to base tables provided by the current model. For example, it is not possible to modify existing data sharing table or field properties using an extension.

If a company-specific table has **Data Sharing Type = Single**, it means it has already been evaluated for SRS. You can’t revert it to **Duplicate** or **None**.

If a company-specific table has **Data Sharing Type = Duplicate**, it means it has already been evaluated for DRS. If you want to enable it for SRS, you need to evaluate its functional eligibility before changing the property to **Single**.

If a custom company-specific table has **Data Sharing Type = None**, but you want to enable data sharing, then the recommendation is to enable it for DRS whenever possible. Because a DRS table can participate in both DRS and SRS policies, it may not be possible for the sharing type to be DRS. Use the following information to determine the appropriate setting.

+ If a company-specific table has a unique index or alternate key, then apply DRS.
    +	If the table has a foreign key field and the corresponding table is set to **Data Sharing Type = None**, then set the **Single Data Sharing Type** property for that field to **Never**.
    +	If the table has a surrogate foreign key field, then set the **Single Data Sharing Type** property for that field to **Never**.
    +	If the table field is referencing any of the tables mentioned under the limitation section, then set the **Single Data Sharing Type** property to **Never**.

+ If a company-specific table doesn’t have a unique index or alternate key, then apply SRS.
    +	If the table has a foreign key field and the corresponding table is set to **Data Sharing Type = None**, then set the **Single Data Sharing Type** property for that key field to **Never**.
    +	If the table has a surrogate foreign key field, then set the **Single Data Sharing Type** property for that field to **Never**.
    +	If the table field is referencing any of the tables mentioned under the limitation section, then set the **Single Data Sharing Type** property to **Never**.

> [!NOTE]
> Cross-company shared policy simulator detects the eligibility of a table and its fields along with table references associated with each field.

After you have modified data sharing metadata properties, you need to do a full DB sync, which will create or update the _SharingView(s).

Data sharing is applicable for tables with the **Save data per company** property set to **Yes**. Tables with **Save data per company** set to **No**, are global and no additional sharing configuration is needed.

From a development perspective, it is not enough to look at the primary and alternate key of a table to determine the sharing type. Additional work may be required to enable sharing without causing data issues.


<table>
<thead>
<tr class="header">
<th>Method/Metadata</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="1">
<td>Relationships
<ul>
<li>Alternate key</li>
<li>Foreign</li>
<li>Sharing Type (Table and fields)</li>
<li>DeleteActions (Restricted/Casacade)</li>
</ul>
</td>
<td><ul>Check the tables and fields and if they are required to be shared. Also, determine if there is impact of DRS versus SRS sharing for the table and field.</ul>
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
<td><ul>Logic might refer to table that is not shared such as transactions, therefore refactoring is required to handle the logic cross company.</ul>
</td>
</tr>
<tr class="3">
<td>Defaulting
<ul>
<li>initValue</li>
<li>defaultField</li>
</ul>
</td>
<td><ul>Check what logic is done in the defaulting, many places values are initialized from a non-shared table, resulting in records being initialized differently, depending on the company record that is created. </ul>

<ul>Are there data dependencies that are not modeled, such as fields shared between tables and used for validation. ProjCategory and ProjCategoryGroup have a CategoryType field. There is a code level validation that the value is the same for the project category and the group assigned. If the fields are not included in the policy update, the project category fails due to the validation check.</ul>
</td>
</tr>
<tr class="4">
<td>CRUD methods
<ul>
<li>delete</li>
<li>insert</li>
<li>update</li>
<li>write</li>
<li>renamePrimaryKey</li>
</ul>
</td>
<td><ul>Are there data dependencies not modeled?
Due to data model decisions, the table metadata, Save date company property, may be set to No.
<li>How are these tables related to data sharing tables?</li>
<li>The table contains DataAreaId as alternate field.
(example: InventItemGroupItem > InventItemGroup)</li>
<li>Code needs to handle populating tables like this cross company.</li>
 </ul>
</td>
</tr>
<tr class="5">
<td>Design patterns using overloaded field values.</td>
<td><ul>In some tables there exists the pattern of two paired fields to indicate relationships. The most common usage is posting profiles. There will be an enumeration field and then a field representing the alternate key from a referenced table. For example, the ProjPosting table has the field ProjCode derived from the enumeration TableGroupAll and an associated field ProjRelationship, which will store the natural key from ProjTable, ProjGroup, or it will be empty. 
Tables with this pattern may be shareable, but clear documentation will need to be provided as to all related tables and fields need to be included in the policy.</ul>
</td>
</tr>
    <tr class="6">
<td>LedgerDimensionDefaultAccount</td>
<td><ul>Tables using this are typically storing the reference to a main account value. These are not shareable.</ul>
</td>
</tr>
    <tr class="7">
<td>Number sequences</td>
<td><ul>Number sequences are typically set up per company. The defaulting logic fields using them will probably not work without code changes.</ul>
</td>
</tr>
</tbody>
</table>

The classes **SysDataSharingCommonAPI**, **SysDataSharingCrossCompanyValidator**, **SysDataSharingCrossCompanyValidatorQueryBuilder**, and methods on the table **SysDataSharingPolicy**, can be used to determine if a table is being used in a data sharing policy. These typically are used in the CRUD and logic default methods to handle table dependencies.

## Examples
Below is a set of examples on how to handle and analyse business logic that are take part of cross company data sharing.

### Example 1 - Validate methods - check if transaction exist

In this example we by default check if transactions exist in current company before deleting the object. This is not enough since object will also be deleted in all the companies that is part of the cross company data sharing policy. Therefore we need to extend the code to do the validation for all companies in the policy before deleting the object.

**InventLocation** table has several examples of business logic that needs to be executed across all companies part of the policy.

```X++
public boolean validateDelete()
{
    SysDataSharingPolicy policy = SysDataSharingPolicy::findSharingPolicyByCompanyAndTable(curExt(), tableId2name(this.TableId));

    if (policy.RecId && policy.IsEnabled)
    {
        Query query = SysDataSharingCrossCompanyValidatorQueryBuilder::buildQuery(this.orig(), policy.RecId);

        QueryRun queryRun = new QueryRun(query);
        while (queryRun.Next())
        {
            InventLocation companyInventLocation = queryRun.get(this.TableId);
            DataAreaId company = companyInventLocation.DataAreaId;
            if (companyInventLocation && company && company != curExt())
            {
                changecompany(company)
                {
                    if (inventLocation.hasOpenInventSumQuantity())
                    {
                        return true;
                    }
                }
            }
        }
    }    
}
```

### Example 2 - Rename primary key

In case we want to rename the primary key of a table and the renamePrimaryKey() contains business logic we need to ensure the logic is executed for all companies part of a cross company data sharing policy. Below code show if renaming a site is allowed if the old site has a warehouse associated with it and the new site value has previously been used with any warehouse.

```x++
public void renamePrimaryKey()
{
    InventSiteId origSiteId = this.orig().SiteId;
    container crossCompanyList = SysDataSharingCommonAPI::getCrossCompanySharingList(tableId2name(this.TableId), curExt());

    // original SiteId    
    select firstonly crosscompany:crossCompanyList RecId from inventDim
        where inventDim.InventSiteId == origSiteId && inventDim.InventLocationId != '';

    if (inventDim.RecId)
    {
        // new SiteId
        select firstonly crosscompany:crossCompanyList RecId from inventDim
            where inventDim.InventSiteId == this.SiteId && inventDim.InventLocationId != '';
    
        if (inventDim.RecId)
        {
            return checkFailed(Site 'XXX' can not be connected to warehouse 'YYY', since the warehouse has already been used in connection with site 'ZZZ'.);
        }       
}    

}
```

### Example 3 - Defaulting / initialization logic

Defaulting for a record, could have business logic that ensures that certain setup is done. In below example we need to ensure that **InventParameter** record exists before we can proper initialize an **InventTable** record, therefore we need to ensure this is done for all companies part of the cross company data sharing policy.

```x++
public void initValue()
{
    SetEnumerator crossCompanySet = SysDataSharingPolicy::crossCompaniesByCompanyAndTable(curExt(), tableStr(InventTable));
    while (crossCompanySet.moveNext())
    {
        DataAreaId company = crossCompanySet.current();
        changecompany(company)
        {
            InventParameters::find();
        }
    }
}
```

Code analysis of defaulting logic is important, when defaulting a field value from a company specific table e.g. Parameter table, then the value might be different in the companies that are part of the cross company data sharing policy.

Below is an example of a field defaulting from parameter table, and here the parameter field value might be different from company to company, leading to different value depending in which company the record is initialized. Either you need to ensure the parameter value is the same in all companies or use e.g. MasterCompany as the defaulting company in case of SRS policy, for DRS it could be the first company in the policy list.

```x++
public void initValue()
{
    SysDataSharingPolicy policy = SysDataSharingPolicy::findSharingPolicyByCompanyAndTable(curExt(), tableId2name(this.TableId));
    if (policy.MasterCompany)
    {
        changecompany(policy.MasterCompany)
        {
            this.BOMUnitId = InventParameters::find().DefaultUnitId;
        }
    }
}
```
