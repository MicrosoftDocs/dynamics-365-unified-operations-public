---
# required metadata

title: Make a backing table be consumable as a Financial dimension
description: 
author: aprilolson
manager: AnnBe
ms.date: 05/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 191363
ms.assetid: dd1dd40e-6bff-47b5-bf2e-55b9a4dcde1d
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Make a backing table be consumable as a Financial dimension

This toipc provides the steps you must follow if you want to make a backing table usable as a Financial dimension.

> [!NOTE]
> If your dimension is backed by the OMOperatingUnit table then many of the steps are already completed for you. Follow the steps in the **Configuration if adding a new OMOperatingUnit type backed entity** section.

By following these steps, your view will automatically appear in the Use values from drop down on the Financial dimensions page, and the values will be populated on the Financial dimension values page.

# Step 1: Create a view

The first step is to create a view in the same model as your backing table.Before you complete the following steps, verify that the backing table has **Create Rec Id Index == Yes** and in the Table Properties pane. Alternatively, check that the table has a unique index specified and RECID is the first segment of that index.

1.  In your project, click **Add**\> **New Item**. Select View and then click **Add**.
1.  Right-click the View and select **Rename**. Name the view **DimAttribute**[BackingTableName]. For example, DimAttributeCustTable
1.  Expand **View Metadata**, and then drag your table and drop it on the **Data Sources** node on the view.
1.  Rename the node from [BackingTableName] to **BackingEntity.**
1.  Identify the key, value and name for the table you want to make into a financial dimension. Find the fields and drag them onto the BackingEntity data source list, or copy and paste the fields on data source. **Rename** the three fields to:
      + **Key** – this is the surrogate key, typically the RecID
      + **Value** - this is the natural key, for example the AccountNum. It is a
        String up to 30 characters.
      + **Name** – this is the description, which is typically the Name or
        description field. It is a String up to 60 characters.
1.  You may need to create a **Range** on the view if the backing table stripes data. For example, if you are using an Operating unit and only want Department, you would need the range for that operating unit.
1.  Right-click Indexes and select **New Index**. Select **Value** as the Data Field on the Properties pane. You can rename the index if desired, but set Allow Duplicates to **No**.
1. Right-click Indexes and select **New Index**. Select **Name** as the Data Field on the Properties pane. You can rename the index if desired, and set Allow Duplicates to **Yes**.
1. Click on the View, and in the Properties pane, set the **Singular Label** field to the reference label ID of your choice. This should the label that indicates a single value, such as Customer.
1. Set the **Label** field to the reference label ID of your choice. This should be the label that indicates multiple values, such as Customers. This value will show in the drop-down list in the Use Values from field on the Financial dimensions page.
1. Type Value in the **TitleField1** field in the Properties pane.
1. Type Name in the **TitleField2** field in the Properties pane.
1. Review the backing table properties and identify the config key it is using. On the View, enter the same **Configuration Key** as the backing table.
1. Search for **DimensionEssentials** and add it to the Project. Expand DimensionEssentials and then right-click Permissions and select **New Permission**. In the Properties pane, set the Access Level to **Read**. Click security Privilege and add the view to it under the Permissions node with an Access Level of **Read**. You may need to extend one of these into the model you are using.
1. Right-click the View and select **View Code**. Add the following code to the view. This will register it in the dimension framework. Here is an example using the view created for CustTable:
      ```
      [SubscribesTo(classstr(DimensionEnabledType),
      delegatestr(DimensionEnabledType,
      registerDimensionEnabledTypeIdentifiersDelegate))]

      public static void registerDimensionEnabledTypeIdentifier(DimensionIEnabledType _dimensionEnabledType)
      {
         _dimensionEnabledType.registerViewIdentifier(tablestr(DimAttribute**CustTable**));
      }
      ```
1. Select **Microsoft Dynamics 365** and then click **Options**. Select Best Practices. Select your model and then scroll until you find
    **Microsoft.Dynamics.AX.Framework.ViewRules/ViewDimensionEnabledTypeChecker**. Verify the rule and its children are selected.
1.  **Build** and then **synchronize** the view.

# Step 2: Validate the view is returning the correct data in SQL

At this point you should be able to run the following query into SQL Server Management Studio to make sure it is pulling the correct data. Here is an abbreviated example using the view created for CustTable:

      select \* from DIMATTRIBUTE**CUSTTABLE**
    

| KEY\_   | VALUE    | DATAAREAID | PARTITION | RECID   | NAME           | PARTITION\#2 |
|-------------|--------------|----------------|---------------|-------------|--------------------|------------------|
| 22565425322 | US\_SI\_0129 | ussi           | 5637144576    | 22565425322 | Adventure Services | 5637144576       |
| 22565424579 | US\_SI\_0128 | ussi           | 5637144576    | 22565424579 | Alpine Electronics | 5637144576       |


# Step 3: Override methods on the backing table**

To integrate with the dimensions framework when deleting or renaming the natural key of the backing table, you must write custom code on the backing table's delete method, and also on either the update or renamePrimaryKey method. If your table blocks update of the natural key you will need to use the renamePrimaryKey override. If it does not, then you can put the code into the update method. Here is an example from CustTable:


   public void delete()
   {
      if (!DimensionValidation::canDeleteEntityValue(this))
      {
            throw error(strFmt("\@SYS134392", this.AccountNum));
      }
      
      ttsbegin;
      DimensionAttributeValue::updateForEntityValueDelete(this);
      ttscommit;
   }
   
   public void update()
   {
      Common originalRecord = this.orig();
      super();
      DimensionValueRename::syncRenamedValue(this, originalRecord);
   }
   
   public void renamePrimaryKey()
   {
      Common originalRecord = this.orig();
      super();
      DimensionValueRename::syncRenamedValue(this, originalRecord);
   }

# Step 4: Clear caches to force detection of new view**

Because the list of dimensionable entities are cached on the server, the creation of a new dimensionable entity will not appear in the list of existing entities until a call to clear the caches is performed, or until both the client and the server are restarted. To clear the caches and have the new view appear immediately, you must execute the following line of code within a runnable class:

      DimensionCache::clearAllScopes();

# Step 5: Validate that the dimension appears in the Use Value From lookup

Now that you have completed the steps, navigate to the Financial dimensions page in the General ledger area. Click on the drop-down on the Use Values from field and verify your value is available.


# Configuration if adding a new OMOperatingUnit type backed entity

If a new Organization Model OMOperatingUnitType enumeration is added, the steps to make it dimensionable are similar but can be made shorter as follows:
1. Copy one of the existing DimAttributeOM[BackingTableName] views, rename it appropriately and adjust all associated labels and help text.
1. Expand the Datasource\\BackingEntity (OMOperatingUnit)\\Ranges node on the copied view and change the value property on the range to the new OMOperatingUnitType enumeration value that was just added.
1. Build and synchronize the project.
1. Follow the steps from section **Step 2: Validate the view is returning the correct data in SQL** and on.

Because the OMOperatingUnitType is backed by the OMOperatingUnit table, generic code already exists to handle the delete, update and renamePrimaryKey methods. Therefore, you do not need to update these methods.
