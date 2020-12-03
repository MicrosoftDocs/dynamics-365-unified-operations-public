---
# required metadata

title: Troubleshoot inventory operations
description: This topic describes how to fix issues that you might encounter while you work with inventory operations.
author: sherry-zheng
manager: tfehr
ms.date: 12/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Release 10.0.16
---

# Troubleshoot inventory operations

[!include [banner](../includes/banner.md)]

This topic describes how to fix issues that you might encounter while you work with inventory operations.

## I can't find the workflow drop-down dialog box for inventory journals.

### Issue description

You can't find workflow the drop dialog in journal form or related workflow operations aren't enabled.

This can be caused by any of three different reasons, as described in the following subsections.

### Issue resolution 1

If the issue applies to all users, it could be that the approval workflow hasn't been assigned to the journal name. Do the following steps:

1. Go to **Inventory Management &gt; Setup &gt; Journal names &gt; Inventory**.
1. Select a journal name from the list pane to open its settings.
1. On the **General** FastTab, set **Approval workflow** to *Yes*. If you are prompted to confirm your setting, select **Yes** to accept it.
1. From the **Workflow** drop-down list, select the workflow you want to use for the selected journal name.

### Issue resolution 2

If your workflow uses customized code, then issues may occur after you upgrade the system. For example, you might be unable to enable the **Submit** button.

When the **Submit** button can't be enabled, it may be because your workflow has been customized to use a posthandler for **canSubmitToWorkflow()** in **FormDataUtil.** As a result, the return value can't override the one already in the data source (**canSubmitToWorkflow()** is now in forms). To solve this issue, change the way you extend **canSubmitToWorkflow()** to use the following code structure:

```xpp
[ExtensionOf(formStr(InventJournalMovement))]
public final class InventJournalMovement_extension
{
    public boolean canSubmitToWorkflow()
    {
        boolean ret = YourLogicOfCanSubmitToWorkflow();

        return ret;
    }
}
```

### Issue resolution 3

If the issue applies only for a few specific users, it could be that those users don't have the security privileges required to run workflow operations on inventory journals. Check that each affected user has the "Maintain inventory journal workflow" security privilege. By default, this privilege is assigned to a duty with same name and that duty is applied to the roles of "warehouse worker" and "warehouse manager".

## My inventory journal stays in system lock status and the workflow batch job doesn't work.

### Issue description

One of your inventory journals is locked by some operation and isn't being released. For example, if an unknown error occurs during posting (which is a system lock operation) the journal may stay in system-locked status, and the workflow work item handler will throw an error while doing lock validation.

### Issue resolution

Sign into the SQL Server for Supply Chain Management and check whether the **InventJournalTable.SystemBlocked** is set to "1". If so, make sure the journal should not be in locked status and then reset it to "0".

## My inventory journal workflow never completes and the journal can't be edited or posted.

### Issue description

After you submit a journal approval workflow, workflow processing freezes so you can't edit or process your journals.

### Issue resolution

There are several potential reasons why workflow processing might fail to complete. Check for the following issues:

- Go to **Inventory management** &gt; **Setup**&gt; **Inventory management** **workflows** and check the configuration of the affected your workflow. For more information, see [Inventory journal approval workflows](inventory-journal-workflow.md).
- The workflow may be running into an exception or error. Check the work item history of the affected workflow to see if it shows an application error that terminates the workflow.
- The inventory journal can't be updated or edited when it isn't approved. You can try to recall the journal if recall is active. There are multiple reasons that can cause the workflow batch job to suspend in execution, some may be due to the workflow framework issue.

## Inventory journal workflow conditions only apply at the journal level, not the line level

### Issue description

You may experience this issue, for example, if you try to set up an inventory journal workflow condition on the cost amount. You set the condition to execute step 1 only when the cost amount is less than 100, and then set up another condition that executes step 2 only when the cost amount is greater than or equal to 100. On executing the workflow, the workflow history will only show one line and the first condition will always evaluate to "true" no matter what value is submitted.

### Issue workaround

In the current release, inventory workflow conditions only apply at the journal level, not on the line level. This is by design. We suggest that you set your condition criteria only on journal-level attributes.

## The filters pane on the on-hand list page doesn't filter results as expected.

### Issue description

The filters on the **Filters** pane on the **On-hand list** page don't filter the results as expected.

### Issue resolution

This behavior is by design.

The **On-hand list** page is assembled from a detailed on-hand inventory table that includes all available dimensions. However, the list on this page is a summary. Therefore, it might combine rows from the source table by aggregating values according to the dimensions that are shown.

Filters set up in the **Filters** pane apply to the source table, not to the aggregated list. This behavior can sometimes produce unexpected results, as [illustrated in these examples](inventory-on-hand-list.md#examples)

However, the [filters that are provided in the grid](inventory-on-hand-list.md#grid-filters) *do* apply to the aggregated list. These filters include both the QuickFilter at the top of the grid and the filter for each column heading.

## The unit and unit quantity aren't working correctly in the inventory journal.

### Issue description

You might see one or both of the following issues when working units and quantities in an inventory journal:

- You don't see units or unit quantities in the inventory journal while a unit of conversion is set up for the released product, and you can't change the unit in the inventory journal.

- You can see the **Unit** field and **Quantity** fields in the inventory journal, but not the **Unit quantity** field. When you change the unit, enter a quantity, and post the journal, the journal still shows the original unit of measurement with that quantity.

### Issue resolution

To fix this issue, do the following steps:

1. Go to the **Feature management** page and make sure you have enabled the *Using unit of measure and unit quantity in inventory journals* feature. This feature adds the**Unit** and **Unit quantity** fields to the journal.
1. On enabling the feature, use the quantity and unit fields as follows:

    - **Quantity** - Specify the quantity using the default unit defined for the released product. However, the default unit itself isn't shown here. If a conversion is set up between the default unit and the unit selected in the **Unit** field, then the **Quantity** field will update automatically based on the selections in the **Unit quantity** and **Unit** fields.
    - **Unit quantity** - Specify the quantity using the unit selected in the **Unit** field.
    - **Unit** - Select the unit to apply to the value in the **Unit quantity** field.

## I get the error message: "Maximum number of decimals for the stock keeping unit is 0"

### Issue description

When you are trying to post an inventory transaction or an inventory reservation, you get see the error message "Maximum number of decimals for the stock keeping unit is 0".

This issue occurs when the inventory transaction quantity value is specified using a decimal value that is below the level of precision supported by the field. For example, an inventory transaction has been specified using a quantity of 0.5, but only integer quantities are supported. Therefore, the value should be 1 instead of 0.5.

### Issue resolution

1. Run the following script on your SQL Server to round quantities in the inventory transactions. It will correct values in the **inventTrans** table.

    ```sql
    update it set it.QTY = round(it.qty, decimalPrecisionValue) from inventtrans it where it.DATAAREAID='XXXX' and it.PARTITION=XXXXXX and it.qty <> round(it.qty, decimalPrecisionValue) and exists (select 'x' from INVENTTABLEMODULE a, unitofmeasure b where  a.unitid =b.SYMBOL and a.partition=it.partition and a.PARTITION=b.PARTITION and  MODULETYPE =0 and  b.DECIMALPRECISION=decimalPrecisionValue and a.DATAAREAID='XXXX' and a.ITEMID =it.ITEMID and it.DATAAREAID=a.DATAAREAID)
    ```

1. Run an on-hand consistency check with the **fix error** option enabled, which will correct values in the **inventSum** table.

> [!IMPORTANT]
> We strongly recommend that edit the script carefully as needed for your environment, test it on a test environment, and then check the resulting data before running it on a production environment.
