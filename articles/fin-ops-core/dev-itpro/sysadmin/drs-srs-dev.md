---
title: Cross-company data sharing for developers
description: Learn about cross-company data sharing for developers. This is a mechanism for sharing reference and group data among companies in a deployment.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: how-to
ms.date: 01/08/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2022-01-27
ms.search.form: SysDataSharingConfiguration
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
---

# Cross-company data sharing for developers

[!include [banner](../includes/banner.md)]

This article describes cross-company data sharing for developers. Cross-company data sharing is a mechanism for sharing reference and group data among companies in a deployment.

## Enable a table for cross-company data sharing

Enabling a table for data sharing is a two-step process that requires updating the metadata property for the table. To enable a custom table for cross-company data sharing, follow these steps. 

1. Open the table properties, and set the **Data Sharing Type** property to **Single** or **Duplicate**. **Single** stands for single record sharing (SRS), and **Duplicate** stands for duplicate record sharing (DRS).
1. For each field on the table, you must review the **Single Data Sharing Type** metadata property. **Always** is the default value and implies that the field is always shared. **Never** implies that the field is never shared. Don't select **Optional**, because there isn't currently any related logic.

> [!NOTE]
> - When a table is set as **Duplicate**, it can participate in both DRS and SRS policies.
> - When a table is set to **Single**, it can participate only in SRS policies.
> - When a table property is set to **Duplicate**, it can't be changed to **Single**. This change is considered a breaking change, because DRS policies that use the table would no longer be valid.
> - When you use SRS, fields that are set to **Never** get the default value for the field's type in all child companies. You can't update these fields to a different value in a child company. For example, if an integer/real field has a value of **0**, strings will be empty, and enumerations will be nondeterministic, based on whether they're extensible.

## How does it work?

When a table is enabled for data sharing, kernel logic automatically creates a view that's named **\<*tablename*\>\_SharingView**. This view should be used for non-kernel-based access to the shared data.

In the following example, the **CustGroup** table is enabled for data sharing, **USMF** is selected as the master company, and **CH1** and **CH2** are the child companies. The illustration shows the output when you read records from CustGroup (Physical) and CustGroup\_SharingView. (*View* illustrates kernel logic but is used only for non-kernel-based scenarios.)

![Single record sharing example.](media/SRS-image3.png)

## Guidelines to enable data sharing on tables

The ability to define or modify DRS or SRS settings applies to base tables that the current model provides. For example, you can't use an extension to modify existing data sharing table or field properties.

If a company-specific table has **Data Sharing Type = Single**, the table has been evaluated for SRS. You can't revert the property to **Duplicate** or **None**.

If a company-specific table has **Data Sharing Type = Duplicate**, the table has been evaluated for DRS. If you want to enable the table for SRS, you must evaluate its functional eligibility before you change the property to **Single**.

If a custom company-specific table has **Data Sharing Type = None**, but you want to enable data sharing, then the recommendation is to enable it for DRS whenever possible. Because a DRS table can participate in both DRS and SRS policies, it may not be possible for the sharing type to be DRS. Use the following information to determine the appropriate setting.

+ If a company-specific table has a unique index or alternate key, then apply DRS.
    + If the table has a foreign key field and the corresponding table is set to **Data Sharing Type = None**, then set the **Single Data Sharing Type** property for that field to **Never**.
    + If the table has a surrogate foreign key field, then set the **Single Data Sharing Type** property for that field to **Never**.
    + If the table field is referencing any of the tables mentioned under the limitation section, then set the **Single Data Sharing Type** property to **Never**.

+ If a company-specific table doesn't have a unique index or alternate key, then apply SRS.
    + If the table has a foreign key field and the corresponding table is set to **Data Sharing Type = None**, then set the **Single Data Sharing Type** property for that key field to **Never**.
    + If the table has a surrogate foreign key field, then set the **Single Data Sharing Type** property for that field to **Never**.
    + If the table field is referencing any of the tables mentioned under the limitation section, then set the **Single Data Sharing Type** property to **Never**.

> [!NOTE]
> Cross-company shared policy simulator detects the eligibility of a table and its fields along with table references associated with each field.

After you modify data sharing metadata properties, you must do a full database synchronization, which creates or updates the \_SharingView views.

Data sharing is applicable to tables where the **Save data per company** property is set to **Yes**. Tables where **Save data per company** is set to **No** are global, and no other sharing configuration is needed.

From a development perspective, it isn't enough to look at the primary and alternate key of a table to determine the sharing type. More work might be required to enable sharing without causing data issues.

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
<td>Check the tables and fields, and determine whether they must be shared. Also determine whether there's an impact of DRS versus SRS for the table and field.</td>
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
<td>Logic might refer to a table that isn't shared, such as transactions. Therefore, refactoring is required to handle the logic cross-company.</td>
</tr>
<tr class="3">
<td>Defaulting
<ul>
<li>initValue</li>
<li>defaultField</li>
</ul>
</td>
<td><ul><li>Check what logic is done in the defaulting. Many places values are initialized from a nonshared table. As a result, records are initialized differently, depending on the company record that's created.</li>
<li>Are there data dependencies that aren't modeled, such as fields that are shared between tables and used for validation? ProjCategory and ProjCategoryGroup have a <b>CategoryType</b> field. Code-level validation is done to ensure that the value is the same for the project category and the group that are assigned. If the fields aren't included in the policy update, the project category fails because of the validation check.</li></ul>
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
<td><ul><li>Are there data dependencies not modeled?
Due to data model decisions, the table metadata, Save date company property, may be set to No.</li>
<li>How are these tables related to data sharing tables?</li>
<li>The table contains DataAreaId as alternate field.
(example: InventItemGroupItem > InventItemGroup)</li>
<li>Code needs to handle populating tables like this cross company.</li>
</ul>
</td>
</tr>
<tr class="5">
<td>Design patterns using overloaded field values.</td>
<td>In some tables, there's the pattern of two paired fields to indicate relationships. The most common usage is posting profiles. There's an enumeration field and then a field that represents the alternate key from a referenced table. For example, the ProjPosting table has the <b>ProjCode</b> field that's derived from the <b>TableGroupAll</b> enumeration and an associated <b>ProjRelationship</b> field that either stores the natural key from ProjTable or ProjGroup, or is empty Tables that have this pattern might be shareable, but clear documentation has to be provided about all related tables and fields that must be included in the policy.</td>
</tr>
<tr class="6">
<td>LedgerDimensionDefaultAccount</td>
<td>Tables that use <b>LedgerDimensionDefaultAccount</b> typically store the reference to a main account value and aren't shareable.</td>
</tr>
<tr class="7">
<td>Number sequences</td>
<td>Number sequences are typically set up per company. The defaulting logic fields that use them probably won't work without code changes.</td>
</tr>
</tbody>
</table>

The **SysDataSharingCommonAPI**, **SysDataSharingCrossCompanyValidator**, and **SysDataSharingCrossCompanyValidatorQueryBuilder** classes, and methods on the **SysDataSharingPolicy** table, can be used to determine whether a table is being used in a data sharing policy. These classes typically are used in the CRUD and logic default methods to handle table dependencies.

## Examples
The following examples show how to handle and analyze business logic that takes the part of cross-company data sharing.

### Example 1: Validate methods – check whether transactions exist

In this example, check by default whether transactions exist in the current company before the object is deleted. This approach isn't enough, because objects are also deleted in all the companies that are part of the cross-company data sharing policy. Therefore, you must extend the code to do the validation for all companies in the policy before the object is deleted.

The **InventLocation** table has several examples of business logic that must be run across all companies that are part of the policy.

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

### Example 2: Rename the primary key

If you want to rename the primary key of a table, and **renamePrimaryKey()** contains business logic, you must ensure that the logic is run for all companies that are part of a cross-company data sharing policy. The following code shows whether a site is allowed to be renamed if a warehouse is associated with the old site and the new site value has previously been used with any warehouse.

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

### Example 3: Defaulting/initialization logic

By default, a record can have business logic that ensures that specific setup is done. In the following example, you must ensure that a **InventParameter** record exists before you can properly initialize an **InventTable** record. Therefore, you must ensure that this logic is done for all companies that are part of the cross-company data sharing policy.

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

Code analysis of defaulting logic is important when a field value is defaulted from a company-specific table, such as the Parameter table, because the value might differ in the companies that are part of the cross-company data sharing policy.

The following example shows a field that's defaulted from the parameter table, where the parameter field value might differ from company to company. Therefore, the value varies, depending on the company where the record is initialized. You must either ensure that the parameter value is the same in all companies or use, for example, MasterCompany as the defaulting company with an SRS policy. For DRS, the company can be the first company in the policy list.

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
