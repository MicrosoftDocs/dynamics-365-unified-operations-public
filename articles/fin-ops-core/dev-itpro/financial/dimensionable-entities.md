---
title: Make backing tables consumable as financial dimensions
description: Learn about the steps that you need to follow to make a backing table usable as a Financial dimension, including code examples.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 12/09/2024
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Make backing tables consumable as financial dimensions

[!include [banner](../includes/banner.md)]

This article provides the steps to make a backing table usable as a Financial dimension.

> [!IMPORTANT]
> Don't create financial dimensions that have values that are not reusable or use one-to-one dimension value combinations. A physical table, and not a view must be used as a source of dimension values for a DimAttribute[BackingTable] view you will create in the following steps. Though using a view as the base data source may seem to work, financial reporting queries will fall back to row-by-row processing to get the dimension fact data imported to the database. This results in extremely slow performance or broken reports. 
>
> The primary table that is to be used as a source of financial dimension data MUST have a unique natural key value of 30 characters or less, and that value MUST resolve to a single RECID within that table. The extended Name column can come from another source join (such as DirPartyTable or elsewhere) because it is used only for displaying additional context to the user and isn't used to resolve uniqueness on natural key entry.
     
Financial dimensions should be reusable values needed for transaction and analytical processes. These dimensions should represent sources of data that can provide high level of reuse across multiple transactions. Don't select a backing table that supplies identity data that represents high volatility when represented with other dimension values. This can increase storage and processing costs and negatively impact performance and analytical value.

Examples of highly variable data include timestamps and identifiers that are frequently incremented, such as:

 - Documents
 - Sales orders
 - Purchase orders
 - Transactions
 - Checks
 - Serials
 - Tickets
 - License numbers 

These are considered highly variable values and shouldn't be used as financial dimensions. The correct use is to implement these as financial tags. For more information about financial tags, see [Financial tags](../../../finance/general-ledger/financial-tag.md).

By following these steps, your view automatically appears in the **Use values from** drop-down menu on the **Financial dimensions** page, and the values are populated on the **Financial dimension values** page.


> [!NOTE]
> If your dimension is backed by the **OMOperatingUnit** table then many of the steps are already completed for you. Follow the steps in the "[Add a new OMOperatingUnit type backed entity](#add-a-new-omoperatingunit-type-backed-entity)" section.

## Step 1: Create a view

The first step is to create a view in the same model as your backing table. Before you complete the following steps, verify that the backing table has **Create Rec Id Index = Yes** in the **Table Properties** pane. Alternatively, ensure that the table has a unique index and RECID is the first segment of that index.

1.  In your project, click **Add** > **New Item**. Select **View** and then click **Add**.
1.  Right-click **View** and select **Rename**. Name the view **DimAttribute**[BackingTableName]. For example, DimAttributeCustTable.
1.  Expand **View Metadata**, and then drag your table to the **Data Sources** node on the view.
1.  Rename the node from **BackingTableName** to **BackingEntity**.
1.  Identify the key, value, and name for the table that you want to use as a financial dimension. Find the fields and drag to the BackingEntity data source list, or copy and paste the fields on the data source. Rename the three fields to:
      + **Key** – This is the surrogate key, typically the RecID.
      + **Value** - This is the natural key, for example the AccountNum. It is a string up to 30 characters.
      + **Name** – This is the description, which is typically the **Name** or **Description** field. It is a string up to 60 characters.
1.  You may need to create a **Range** on the view if the backing table removes data. For example, if you are using an Operating unit and only want Department, use the range for that operating unit.
1.  Right-click **Indexes** and select **New Index**. Select **Value** as the Data field on the **Properties** pane. You can rename the index if needed, however, you need to set **Allow Duplicates** to **No**.
1. Right-click **Indexes** and select **New Index**. Select **Name** as the Data field on the **Properties** pane. You can rename the index if needed, however, you need to set **Allow Duplicates** to **Yes**.
1. Click **View**, and in the **Properties** pane, set the **Singular label** field to the reference label ID of your choice. This should be the label that indicates a single value, such as Customer.
1. Set the **Label** field to the reference label ID of your choice. This should be the label that indicates multiple values, such as Customers. This value shows in the drop-down list in the **Use Values from** field on the **Financial dimensions** page.
1. Enter **Value** in the **TitleField1** field in the **Properties** pane.
1. Enter **Name** in the **TitleField2** field in the **Properties** pane.
1. Review the backing table properties and identify the config key it is using. On **View**, enter the same **Configuration key** as the backing table.

    > [!IMPORTANT]
    > Security access must be granted to non-admin users for the new view.
    > - For releases 7.2 and earlier where over-layering is used - Search for **DimensionEssentials** and add it to the Project. Expand **DimensionEssentials**, right-click **Permissions**, and then select **New Permission**. In the **Properties** pane, set the **Access Level** to **Read**. Click **Security Privilege** and add the view under the **Permissions** node with an **Access Level** of **Read**. You may need to extend one of these into the model that you're using.
    > - For releases 7.3 and later where extensions are used - Create a new Security Privilege in your custom model alongside the new view. Right-click the **Permissions** node, and choose **New Permission**. Enter the name of new DimAttribute[DimensionName] view created above in step 2 and set the **Access Level** to **Read**. Search for **Security Duty SysServerAXBasicMaintain**. Right-click and choose **Create extension**. Rename the extension as appropriate. Drag-and-drop the newly created **Security Privilege** into the **Privileges list**.  
       
14. Right-click **View** and select **View Code**. Add the following code to the view. This registers it in the dimension framework. Here's an example using the view created for CustTable.

      ```xpp
      [SubscribesTo(classstr(DimensionEnabledType),
      delegatestr(DimensionEnabledType,
      registerDimensionEnabledTypeIdentifiersDelegate))]

      public static void registerDimensionEnabledTypeIdentifier(DimensionIEnabledType _dimensionEnabledType)
      {
         _dimensionEnabledType.registerViewIdentifier(tablestr(DimAttribute**CustTable**));
      }
      ```

15. Select **Microsoft Dynamics 365** and click **Options**. Select **Best Practices**. Select your model and then scroll until you find
    **Microsoft.Dynamics.AX.Framework.ViewRules/ViewDimensionEnabledTypeChecker**. Verify that the rule and its children are selected.
16.  Build and then synchronize the view.

## Step 2: Validate that the view returns the correct data in SQL

At this point you should be able to run the following query in SQL Server Management Studio to ensure that it's pulling the correct data. Here's an abbreviated example using the view created for CustTable.

```sql
select * from DIMATTRIBUTECUSTTABLE
```
    

| KEY   | VALUE    | DATA AREA ID | PARTITION | RECID   | NAME           | PARTITION #2 |
|-------------|--------------|----------------|---------------|-------------|--------------------|------------------|
| 22565425322 | US\_SI\_0129 | ussi           | 5637144576    | 22565425322 | Adventure Services | 5637144576       |
| 22565424579 | US\_SI\_0128 | ussi           | 5637144576    | 22565424579 | Alpine Electronics | 5637144576       |


## Step 3: Override methods on the backing table

To integrate with the dimensions framework when deleting or renaming the natural key of the backing table, you must write custom code on the backing table's delete method, and on either the update or renamePrimaryKey method. If your table blocks updates of the natural key, you need to use the renamePrimaryKey override. If it doesn't, then you can put the code in the update method. Here's an example from CustTable.

```xpp
public void delete()
{
    if (!DimensionValidation::canDeleteEntityValue(this))
    {
        throw error(strFmt("@SYS134392", this.AccountNum));
    }
      
    ttsbegin;
    DimensionAttributeValue::updateForEntityValueDelete(this);
    ttscommit;
}
   
public void update()
{
    Common originalRecord = this.orig();
     DimensionValueRenameV2 rename = DimensionValueRenameV2::construct(this, originalRecord);
     rename.syncRenamedValuePreSuper();
     super();
     rename.syncRenamedValuePostSuper();
}
   
public void renamePrimaryKey()
{
     Common originalRecord = this.orig();
     DimensionValueRenameV2 rename = DimensionValueRenameV2::construct(this, originalRecord);
     rename.syncRenamedValuePreSuper();
     super();
     rename.syncRenamedValuePostSuper();
}
```

## Step 4: Clear caches to force detection of the new view

Because the list of entities that can be consumed as a dimension are cached on the server, the creation of a new entity won't appear in the list of existing entities until a call to clear the caches is performed, or until both the client and the server are restarted. To clear the caches and have the new view appear immediately, you must execute the following line of code within a runnable class.

```xpp
DimensionCache::clearAllScopes();
```

## Step 5: Verify that the dimension appears in the Use Value From lookup

Now that you have completed the steps, navigate to the **Financial dimensions** page in the General ledger. Click the drop-down menu on the **Use Values from** field and verify that your value is available.


## Add a new OMOperatingUnit type backed entity

If a new Organization Model OMOperatingUnitType enumeration is added, the steps to make it consumable as a dimension are similar but can be made shorter as follows:

1. Copy one of the existing DimAttributeOM[BackingTableName] views, rename it appropriately, and then adjust all associated labels and help text.
1. Expand the Datasource\BackingEntity (OMOperatingUnit)\Ranges node on the copied view. Change the value property on the range to the new OMOperatingUnitType enumeration value that was added.
1. Build and synchronize the project.
1. Follow the steps in this article starting with Step 2, where you validate the data in SQL, and then continue through Step 5, where you validate that the dimension appears in the **Use Value From** lookup.

Because the **OMOperatingUnitType** is backed by the **OMOperatingUnit** table, generic code already exists to handle the delete, update, and **renamePrimaryKey** methods. Therefore, you don't need to update these methods.

## Step 6: Setting a dimension to be self-referenced 

If you also want to create a data entity for your new entity, and that entity has a reference to default dimensions, add this code to the persistEntity() method.

```xpp
if (_entityCtx.getDatabaseOperation() == DataEntityDatabaseOperation::Insert)
{
    this.<Your entity ‘private’ RecId Dimension field> = DimensionDefaultResolver::checkAndCreateSelfReference(tablenum(<Your backing table>), this.<Your entity Key field>, this.<Your entity ‘public’ DisplayValue field>);
}
```                                                                                            
**Example**

```xpp
public void persistEntity(DataEntityRuntimeContext _entityCtx)
{
    if (_entityCtx.getDatabaseOperation() == DataEntityDatabaseOperation::Insert)
    {
        this.DefaultDimension = DimensionDefaultResolver::checkAndCreateSelfReference(tablenum(BankAccountTable), this.BankAccountId, this.DefaultDimensionDisplayValue);
    }

    super(_entityCtx);
}
```

> [!NOTE]
> This ensures that if you also want the dimension to use itself as a default dimension value, the information is created in the correct sequence.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
