---
# required metadata

title: Standard cost conversion overview
description: This article provides a process overview to help you set up and run a standard cost conversion. The steps listed are intended to be completed after you've completed the prerequisites for a standard cost conversion. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostingVersion, InventStdCostConv
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: d601d9d5-1de3-4868-aff4-534dca01d624
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Standard cost conversion overview

[!include [banner](../includes/banner.md)]

This article provides a process overview to help you set up and run a standard cost conversion. The steps listed are intended to be completed after you've completed the prerequisites for a standard cost conversion. 

Use the **Standard cost conversions** page to convert the inventory model for a batch of selected items from an actual costing approach to a standard costing approach. The conversion process involves a prerequisite inventory close, several steps during a transition period, which is defined by a transition start date and a planned conversion date, and then the conversion and an associated inventory close.

-   Inventory close before the transition period – An inventory close represents a prerequisite step because it settles an item’s open transactions using the old valuation method. During the transition period, you can enter and post backdated transactions, such as invoices, so that you can close the previous period. The inventory close date must be one day before the transition start date to ensure a clean break from the old valuation method.
-   Conversion steps during the transition period – Use the **Standard cost conversions** page to create a conversion record that also contains the user-defined identifier for a new costing version. You identify the items that require conversion, and then enter the items’ pending standard costs in the new costing version. You perform a check of the selected items to identify issues that might prevent conversion, resolve the issues, and then perform another check. After the items have successfully passed the checks, you change the status of the conversion record to **Ready**. On the planned conversion date, you perform the conversion and optionally include an inventory close. An item’s inventory movements during the transition period are posted and valued according to the old inventory model. Then, after the conversion is successfully completed, the inventory movements are revalued to standard cost.
-   Inventory close before the conversion – The inventory close can be included as part of the conversion on the planned conversion date, or it can be performed as a separate step before the conversion.

After the conversion process is successfully completed, the inventory model for each item is based on standard cost, and the item’s standard cost is enabled. Subsequent inventory transactions will be valued at the item’s standard cost. In addition, the system converts the item’s physical inventory transactions for receipts and issues to standard cost based on the conversion date. The system also converts the item’s financial on-hand inventory to standard cost, and posts the difference in value as an inventory revaluation. Any transactions that occur after the conversion are valued at the item’s standard cost. You cannot enter backdated transactions before the conversion date, because an inventory close must be performed one day before the conversion date. A conversion can only be performed if an inventory close was performed one day earlier. This inventory close cannot be canceled.

## 1. Define a standard cost conversion record and the associated costing version
Use the **Standard cost conversions** page to create a conversion record. You can create a new conversion record only when existing conversion records have been completed. The duration of the planned transition period is defined by the transition start date and the planned conversion date. A planned transition period can be as short as one day. A planned transition period helps to ensure that the conversion process has enough time to complete all its steps. An inventory close must be performed on a date that is one day before the transition start date, to help ensure that settlements are completed before you start the conversion process. To make sure that the transition start date and inventory close date are correctly aligned, you can either change the transition start date to one day after an existing inventory close or perform an inventory close. When you enter a conversion record, you also enter a user-defined identifier for a new costing version that will contain the standard costs for converted items. The costing version is generated automatically when you save the conversion record.

## 2. Review and change the new costing version for the conversion record
The new costing version is dedicated to the conversion record, as the **Conversion** costing type indicates. The dedicated costing version is similar to a costing version for standard costs and contains the item cost records for items that are associated with the conversion record. The dedicated costing version for a conversion record has the following settings, which you should review and modify on the various tabs as required:

-   **Costing type:** This field should be set to **Standard cost**.
-   **Version:** The identifier reflects the information that is entered on the conversion record for the costing version ID.
-   **Name:** By default, the name is blank. You can optionally enter a name.
-   **Block:** This field should be set to **No**. You can enter cost records into the costing version until you change the status of the conversion record to **Ready**. A status of **Ready** indicates that the selected items have been checked, and that changes to cost records should not be permitted.
-   **Block activation:** This field should be set to **Yes**. You can't manually activate a pending cost record in the dedicated costing version. Activation occurs when you perform the conversion.
-   **From date:** The from date reflects the planned conversion date that is entered on the conversion record.
-   **Site:** Leave this field blank, so that cost records can be entered for any site.
-   **Allow price type field group:** Set this field to **Yes**, so that only cost price records can be entered.
-   **Fallback principle:** This field is set to **None**. Change the fallback principle to **Active** if you require cost information that has been activated in other costing versions. For example, cost information about components, cost categories, and indirect costs might be required in order to calculate the costs of manufactured items.
-   **Fallback costing version:** Leave this field blank.

Item cost information in the dedicated costing version can be maintained only from the **Standard cost conversions** page. You can't use the **Costing version setup** page or the **Costing version maintenance** page to calculate costs for the costing version during conversion. However, you can use these pages to maintain the dedicated costing version after you've completed the conversion process.

## 3. Identify the items to convert to standard cost
Use the **Standard cost conversions** page to identify the individual items that should be converted to standard cost. You can add multiple items by using the **Add items to standard cost conversion** page. In general, you should include all manufactured items in a single conversion record to help ensure that costs are calculated correctly.

## 4. Enter or calculate the pending standard cost for each item that is being converted
Use the **Item price** page to enter pending standard costs in the dedicated costing version for purchased items and transfer items. Cost records are site-specific, and an item's pending costs must be entered for every site. Use the **Item price** page to calculate pending standard costs for manufactured items. A manufactured item's pending costs should be calculated for every manufacturing site, unless the site represents a transfer site. In this case, the pending costs should be entered manually. Some items might have color, size, or configuration product dimensions. On the **Standard cost conversions** page, the **Use cost price by variant** check box shows the standard cost for every combination of product dimensions. When this check box is cleared, you must enter only a pending cost for the item.

## 5. Check and resolve any issues for the items that are being converted
Use the **Standard cost conversion checks** report to identify issues for the items that are being converted. If an item doesn't have any issues, its status in the conversion record is changed to **Checked**. If an item has issues, you must resolve the issues and then run the report again until the item's status is changed to **Checked**. If you can't resolve an item's issues in a timely manner, you can optionally delete the item from the conversion record and then convert the item later.

## 6. Change the status of the conversion record to Ready
When the status of the conversion record is changed to **Ready**, the system performs a final check before it runs a standard cost conversion. The status is changed to **Ready** only if the following conditions have been met:

-   Every item in the conversion record has a status of **Checked**.
-   An inventory close was performed on a date that is one day before the transition start date. To make sure that the transition start date and inventory close date are correctly aligned, you can either change the transition start date to one day after an existing inventory close or perform an inventory close.

## 7. Back up the database before conversion
The backup lets you restore the database if errors are encountered during the conversion.

## 8. Perform the conversion when the conversion record has a Ready status
The conversion process requires that an inventory close be performed on a date that is one day before the planned conversion date. This requirement helps ensure that back-dated transactions can't be entered during the transition period. If an inventory close hasn't yet been performed, you will be asked if you want to perform it as part of the conversion process. The conversion process handles one item at a time. It starts with the lowest items in a product structure, based on the item's low-level code. When an item has been successfully converted, its status in the conversion record is changed to **Converted**. If the conversion process is interrupted, any items that haven't been successfully converted will still have a status of **Checked**. Successful completion of the conversion process has the following effects:

-   The status of the conversion record is changed from **Ready** to **Completed**, and the status of each selected item is changed from **Checked** to **Converted**.
-   The item model group for converted items is changed so that it reflects a new group that has a standard cost inventory model.
-   The standard costs for the converted items have been enabled in the dedicated costing version.
-   The costing type of the costing version is changed from **Conversion** to **Standard cost**, and the costing version is now like other costing versions for standard costs.

## 9. Validate and reconcile the inventory values for the converted items
The **Variance analysis statement** report lets you analyze revaluation variance and the **Inventory value** repot lets you view inventory value on a specific date.

-   Analyze revaluation variances. Use the **Variance analysis statement** report to view inventory revaluation variances for the converted items. You can also use the **Standard cost transactions** page to view the inventory revaluation transactions for the converted items that have inventory.
-   Analyze the inventory value before the transition start date. Use the **Inventory value** report to view inventory values for the converted items. For the To date for the report, use a date that is one day before the transition start date.
-   Analyze the inventory value before the conversion date. Use the **Inventory value** report to view inventory values for the converted items. As the To date for the report, use a date that reflects one day before the conversion date.
-   Analyze the inventory value on the conversion date. Use the **Inventory value** report to view inventory values as of the conversion date. Both the From date and the To date for the report should match the conversion date. The report selection criteria should reflect the converted items.
-   Analyze back-dated inventory movements. Use the **Inventory value** report to view back-dated inventory movements that were entered after the conversion. The "From date and the To date for the report should correspond to the transition start date and the conversion date, minus one day. The report selection criteria should reflect the converted items. The report shows inventory movements that were made at standard cost during the transition period.


## Additional resources

[Prerequisites for a standard cost conversion](prerequisites-standard-cost-conversion.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]