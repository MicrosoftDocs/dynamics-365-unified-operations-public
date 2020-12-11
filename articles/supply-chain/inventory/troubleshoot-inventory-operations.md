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

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
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

## I can't find the "Workflow" drop-down dialog box for inventory journals.

### Issue description

You can't find the **Workflow** drop-down dialog box on the journal page, or related workflow operations aren't available.

This issue can occur for three reasons, as described in the following subsections.

### Issue resolution 1

If the issue applies to all users, it might be occurring because the approval workflow hasn't been assigned to the journal name. To fix the issue, follow these steps.

1. Go to **Inventory Management &gt; Setup &gt; Journal names &gt; Inventory**.
1. In the list pane, select a journal name to open its settings.
1. On the **General** FastTab, set the **Approval workflow** option to *Yes*. If you're prompted to confirm the change, select **Yes**.
1. In the **Workflow** field, select the workflow that you want to use for the selected journal name.

### Issue resolution 2

If your workflow uses customized code, issues might occur after you upgrade the system. For example, you might be unable to enable the **Submit** button.

When the **Submit** button can't be enabled, your workflow might have been customized so that it uses a post-handler for `canSubmitToWorkflow()` in `FormDataUtil`. Therefore, the return value can't override the existing value in the data source (`canSubmitToWorkflow()` is now in forms). To fix this issue, change the way that you extend `canSubmitToWorkflow()`, so that the following code structure is used.

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

If the issue applies only to a few specific users, those users might not have the security privileges that are required to run workflow operations on inventory journals. Verify that each affected user has the *Maintain inventory journal workflow* security privilege. By default, this privilege is assigned to a duty that has same name, and that duty is applied to the *Warehouse worker* and *Warehouse manager* roles.

## My inventory journal remains in system-locked status, and the workflow batch job doesn't work.

### Issue description

One of your inventory journals is locked by some operation and isn't being released. For example, if an unknown error occurs during posting (which is a system lock operation), the journal might remain in system-locked status. In this case, the workflow work item handler will throw an error while it does lock validation.

### Issue resolution

Sign in to the SQL Server instance for Supply Chain Management, and check whether **InventJournalTable.SystemBlocked** is set to *1*. If it is, make sure that the journal should not be in locked status, and then reset **InventJournalTable.SystemBlocked** to *0*.

## My inventory journal workflow is never completed, and the journal can't be edited or posted.

### Issue description

After you submit a journal approval workflow, workflow processing stops responding, and you can't edit or process your journals.

### Issue resolution

There are several reasons why workflow processing might not be completed. Check for the following issues:

- Go to **Inventory management &gt; Setup &gt; Inventory management workflows**, and review the configuration of the affected workflow. For more information, see [Inventory journal approval workflows](inventory-journal-workflow.md).
- The workflow might be encountering an exception or error. Review the work item history of the affected workflow to see whether it includes an application error that terminates the workflow.
- The inventory journal can be updated or edited only if it's approved. If recall is active, you can try to recall the journal. Execution of the workflow batch job might be suspended for multiple reasons. Some of these reasons might be caused by the workflow framework issue.

## Inventory journal workflow conditions apply only at the journal level, not at the line level

### Issue description

You might experience this issue if, for example, you try to set up an inventory journal workflow condition on the cost amount. You set up the condition so that step 1 is run only when the cost amount is less than 100. You then set up another condition so that step 2 is run only when the cost amount is more than or equal to 100. Then, when the workflow is run, the workflow history shows only one line, and the first condition is always evaluated as *true*, regardless of the value that is submitted.

### Issue workaround

In the current release, inventory workflow conditions apply only at the journal level, not at the line level. This behavior is by design. We recommend that you set your condition criteria only on journal-level attributes.

## The filter pane on the On-hand list page doesn't filter results as I expect.

### Issue description

The filters in the filter pane on the **On-hand list** page don't filter results as you expect.

### Issue resolution

This behavior is by design.

The **On-hand list** page is assembled from a detailed on-hand inventory table that includes all available dimensions. However, the list on this page is a summary. Therefore, it might combine rows from the source table by aggregating values according to the dimensions that are shown.

Filters that are set up in the filter pane apply to the source table, not to the aggregated list. This behavior can sometimes produce unexpected results, as shown in [these examples](inventory-on-hand-list.md#examples).

However, the [filters that are provided in the grid](inventory-on-hand-list.md#grid-filters) *do* apply to the aggregated list. These filters include both the QuickFilter at the top of the grid and the filter for each column heading.

## The unit and unit quantity aren't working correctly in the inventory journal.

### Issue description

You might encounter one or both of the following issues when you work with units and quantities in an inventory journal:

- You don't see units or unit quantities in the inventory journal while a unit of conversion is set up for the released product, and you can't change the unit in the inventory journal.
- You see the **Quantity** and **Unit** fields in the inventory journal, but you don't see the **Unit quantity** field. If you change the unit, enter a quantity, and post the journal, the journal still shows the original unit of measurement for that quantity.

### Issue resolution

To fix this issue, follow these steps.

1. In the **Feature management** workspace, make sure that the *Using unit of measure and unit quantity in inventory journals* feature is turned on. This feature adds the **Unit** and **Unit quantity** fields to the journal.
1. After the feature is turned on, use the **Quantity**, **Unit quantity**, and **Unit** fields in the following way:

    - **Quantity** – Specify the quantity by using the default unit that is defined for the released product. However, the default unit itself isn't shown here. If a conversion is set up between the default unit and the unit that is selected in the **Unit** field, the **Quantity** field is automatically updated, based on the selections in the **Unit quantity** and **Unit** fields.
    - **Unit quantity** – Specify the quantity by using the unit that is selected in the **Unit** field.
    - **Unit** – Select the unit to apply to the value in the **Unit quantity** field.

## I receive the following error message: "Maximum number of decimals for the stock keeping unit is 0."

### Issue description

When you try to post an inventory transaction or an inventory reservation, you receive the following error message: "Maximum number of decimals for the stock keeping unit is 0."

This issue occurs when the inventory transaction quantity is specified as a decimal value that is below the level of precision that the field supports. For example, a quantity of *0.5* has been specified for an inventory transaction, but only integer quantities are supported. Therefore, the value should be *1* instead of *0.5*.

### Issue resolution

1. Run the following script on your SQL Server instance to round quantities in the inventory transactions. This script will correct values in the **inventTrans** table.

    ```sql
    update it set it.QTY = round(it.qty, decimalPrecisionValue) from inventtrans it where it.DATAAREAID='XXXX' and it.PARTITION=XXXXXX and it.qty <> round(it.qty, decimalPrecisionValue) and exists (select 'x' from INVENTTABLEMODULE a, unitofmeasure b where  a.unitid =b.SYMBOL and a.partition=it.partition and a.PARTITION=b.PARTITION and  MODULETYPE =0 and  b.DECIMALPRECISION=decimalPrecisionValue and a.DATAAREAID='XXXX' and a.ITEMID =it.ITEMID and it.DATAAREAID=a.DATAAREAID)
    ```

1. Run an on-hand consistency check where the **fix error** option is turned on. This check will correct values in the **inventSum** table.

> [!IMPORTANT]
> We strongly recommend that you carefully edit the script as required for your environment, test it in a test environment, and then check the resulting data before you run the script in a production environment.
