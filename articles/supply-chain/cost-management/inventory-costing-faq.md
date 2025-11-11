---
title: Inventory costing FAQ
description: Access answers some frequently asked questions about inventory costing in Microsoft Dynamics 365 Supply Chain Management.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: faq
ms.date: 07/10/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
---

# Inventory costing FAQ

[!include [banner](../includes/banner.md)]

This article answers some frequently asked questions about inventory costing in Microsoft Dynamics 365 Supply Chain Management.

## Inventory closing, adjustments, recalculation, pre-closing, and reverse

### Why is inventory closing required?

The inventory close process matches and settles inventory issue transactions (resulting from sales, production order issue, transfer journals, and other transactions) to their receipt transactions (such as purchase, counting journals, and other transactions). The process uses the inventory valuation method that you define in the item model group and considers the item's active financial product, storage, and tracking dimensions.

You perform inventory closing for periodic inventory valuation methods (FIFO, LIFO, Weighted Average, and other methods). It ensures that the financial statements (income statement, balance sheet, trial balance, and other statements) reflect appropriate inventory values and cost of goods sold (COGS) based on all receipts and issues up to the period end.

You should ideally execute inventory closing on a regular basis for a specific period. Once you close the inventory for that period, you can no longer post any transactions in that period.  

The frequency of inventory close run varies by company. However, transaction volume should determine how often you decide to run inventory close. In general, most companies run inventory closing as part of their month-end closing and reconciliation procedures, and before any audit activities.

To balance out the transactional load, execute inventory closing regularly, once inventory transactions are finalized for a period, typically at a monthly frequency.  

You must execute inventory closing if you plan to change the valuation model in Item Model Group of an item from periodic to perpetual, or if you plan to archive old inventory transactions.

### Why is inventory recalculation required?

If you need to adjust inventory and the general ledger during a month or other inventory period, run inventory recalculation instead of inventory close. Inventory recalculation adjusts the inventory transactions according to the applicable valuation method but doesn't settle inventory transactions. Like inventory closing, you can only execute inventory recalculation for periodic inventory valuation methods.

During inventory recalculation, the system adjusts on-hand and inventory transactions. These tasks affect any ledger account that's linked to the original inventory transaction.

Inventory recalculation doesn't close any period, unlike inventory closing. You can still post transactions in the period for which you already executed inventory recalculation.

The frequency of inventory recalculation execution depends on your business requirements. You can execute recalculations daily, weekly, or monthly to adjust the on-hand and inventory transactions and reflect the accurate cost of the items based on their valuation method. However, executing inventory recalculation is an optional procedure and not a prerequisite to inventory closing. We recommend executing inventory closing monthly. Once you execute closing, the system automatically cancels all the recalculations you executed for dates after the closing date. Running many recalculations or executing scheduled recalculations has a performance impact.  

### What are the differences between inventory closing and inventory recalculation?

1. Inventory closing matches and settles transactions, whereas inventory recalculation adjusts transactions.  

1. Inventory closing closes the period for which you execute it, so you can't post any further transactions in that period. Inventory recalculation doesn't restrict inventory postings for any period.

1. You must execute inventory closing before making any modifications in an item's item model group* and before archiving old transactions. Besides, you should regularly execute inventory closing at periodic intervals to reduce the system load for high transactional volume. Inventory recalculation isn't a mandatory process.  

### Is it mandatory to execute inventory closing or recalculation?

You must execute inventory closing before making any modifications in an item's item model group and before archiving old inventory transactions. Besides, you should regularly execute inventory closing at periodic intervals to reduce the system load for high transactional volume. Inventory closing closes the settled inventory transactions, thereby excluding the closed transactions from further inventory processes. Inventory recalculation isn't a mandatory process. You can execute it according to your business requirements either daily, weekly, or monthly to adjust the on-hand and inventory transactions for reporting the accurate cost of the items based on the valuation method. We recommend closing your inventory monthly for better performance.

### What is inventory pre-closing?

Preclosing replaces the *activate closing of non-financial transfer* functionality that was available in older versions of Supply Chain Management. Pre-closing closes the *non-financial transfers* so that the inventory closing procedure can ignore them as closing and recalculation only impact the financial transactions. *Non-financial transfers* are inventory transactions that have no effect on inventory costing, like inventory movement journal between two warehouses in the same site if warehouse isn't a financial dimension. You can explicitly execute pre-closing if required as per the business requirements. Moreover, the closing and recalculation procedure always implicitly executes pre-closing.

### What is inventory reversal? How is it different from cancellation of closing?

If you need to revert the settlements or adjustments made by a closing or recalculation voucher, select the respective voucher and then select **Reverse**. This action posts equal but opposite settlements or adjustments in the ledger, balancing the changes made by the respective closing or recalculation voucher.  

Inventory reversal is also used when you need to post any transaction in an already closed inventory period. In that case, the closing voucher is reversed, which opens the period and allows you to post transactions.

Inventory reversal and cancellation refer to the same operation and can be used interchangeably.  

### What is inventory revaluation?

For perpetual valuation models like moving average or standard cost, use inventory revaluation to revalue the on-hand inventory. Inventory revaluation works similarly to inventory recalculation. Use inventory revaluation to adjust the recorded value of inventory items to reflect changes in cost, market conditions, accounting corrections, or policy updates. This adjustment can either increase (appreciate) or decrease (depreciate) the value of inventory on hand in the system and general ledger.

### What is the typical duration required to complete the Inventory Closing and Recalculation process, and what factors impact the execution time?

The duration required to complete the Inventory Closing/Recalculation process can vary widely depending on several factors and could ranges from a few minutes to several hours for most environments. Overall time for execution depends on:

- Volume of inventory transactions (issues vs receipts)
- Type of inventory transactions (source documents)
- Length of the period
- Number of Items and Inventory Dimensions (site, warehouse, location, etc.)
- Real time resource utilization and availability,
- Parallel processes being executed at the same time, number of active sessions, etc.

Since Closing process could run from few minutes to several hours, it is recommended to schedule the process at off peak hours to avoid any business disruptions.

### Why is my inventory closing or recalculation executing for a prolonged duration? Can I improve the execution speed?

As discussed previously, there's no fixed duration for inventory closing or recalculation. The overall execution depends on the count of open or unsettled transactions, the nature of source documents, resource availability, parallel processing, parallel user sessions, and other factors. The following recommendations help you analyze the closing process:

1. **Track progress of the execution** – You can always track the progress of the closing or recalculation voucher from the **Closing and adjustment** page. Select the specific voucher and go to *Progress details*. You can find the bundles that have completed execution and the ones that are still pending.

1. **Execute inventory closing regularly** – If you have a high volume of transactions and don't execute inventory closing regularly at periodic intervals, you might experience performance issues as the count of open or unsettled transactions gradually increases in the system. Hence, execute inventory closing regularly (preferably at monthly intervals) for customers with a high volume of transactions for better performance. You can check the time stamp for the most recent closing executed. You can view this information from the **Closing and adjustment** page by filtering the **Type** as *Closing*. If you didn't execute closing recently and have items that use any periodic valuation methods in your inventory, proceed with closing the inventory for the period nearest to your recalculation period.

1. **Circularity in inventory transactions** – Overall execution time largely depends on your inventory transactions and the nature of source documents. BOM journals are one of the source documents that consume a considerable amount of time in calculating the cost of the final product when the BOM structure is quite complicated, with lots of depth, consumption of scrap products, circular links in production and consumption, and other factors. If you have inventory transactions that pertain to any BOM journal, you can perform a basic BOM circularity check and eliminate any circular link. BOM circularity doesn't throw errors in the closing or recalculation process because the process has a specific design to handle such scenarios. However, BOM circularity increases the overall execution time to a large extent. The same situation applies to transfer order circularity. Consider the scenario when there's a transfer from site 1 to site 2 and then again from site 2 to site 1. To improve performance, reduce and eliminate the possibility of any such circularity in BOM journals or transfer orders. For more information about BOM circularity check strategies, refer to the other FAQs in this article.

1. **Review inventory performance parameters** – You can configure a few parameters to control the performance of closing and recalculation.

    Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters** and open the **Inventory accounting** tab. In the**Closing** section, make the following settings:

    - **Extra Batch Helpers** – Set the number of extra threads to spawn based on thread pool availability to aid the execution of the respective batch job. The default value for this parameter is *8*. You can increase this value based on the availability of your system resources. Learn more in [batch capacity](../../fin-ops-core/dev-itpro/sysadmin/batch-capacity).

    - **Number of items per bundle** – Set the maximum number of items to keep in a bundle. The default value is *40*. An item is always present in a single bundle, and a single thread or task always processes a bundle. If your transactions have many items and a relatively comparable number of transactions per item, keep this value at *40*. If your inventory transactions don't have many items or instead have a large number of transactions for only a few items, set this value to *10*. Modify these values before the commencement of the closing or recalculation process, not somewhere in between the execution process.

    In the **Closing** or **Recalculation** dialog, make the Following settings:

    - **Maximum number of iterations allowed per item** – Pertains to cost calculations for circular links and is a trade-off between performance and accuracy. It determines the number of iterations for which the closing or recalculation process executes. Every iteration adjusts the cost of the item involved in the circular BOM. Hence, the more iterations, the better the cost accuracy for those items in the circular BOM. But you can't practically execute this process infinitely, so the default iteration value is *100*. If your business transactions don't have many circular inventory transactions, or if you're fine with some approximate cost adjustments, consider reducing this value to reduce the overall execution time.

    - **Minimum amount allowed to be expensed** – Determines the minimum adjustment amount to be expensed while processing inventory transactions in every iteration. This parameter is again a tradeoff, like the previous one, but instead, performance is reversely proportional to the value. A lower value contributes to poorer performance but more accurate results. The default value is *1.00* in the accounting currency. Most companies don't modify this value, but it's up to your business requirements to determine an optimized value.

    To improve the closing or recalculation performance, eliminate any circular links from your inventory transactions.

If you feel that the operation is executing for an unusual amount of time, contact Microsoft Support or your partner to monitor the real-time execution status and resource utilization.  

### How do I check circularity in BOM journals?

Navigate to **Inventory Management** > **Setup** > **Inventory and warehouse management parameters** > **Bill of materials**. Enter the required values in **Level of circularity** and **Circularity check strategy**. The **Circularity check strategy** option works in conjunction with the **Level of circularity** option, so the first thing to look at is selection made for the **Level of Circularity** option.  

The **Level of circularity** field has three options: *Never*, *BOM*, and *Line*. This setting determines when the system checks for circularity in BOM structures. A circular BOM exists when an item is defined as a component of itself within a BOM structure. A BOM is considered circular regardless of whether it is a first-level component or a lower-level component in the BOM structure that is referenced.

1. **Line:** The circularity check occurs when you save the BOM line. This setting prevents you from adding a BOM line when the component item causes BOM circularity.

1. **Never:** The system doesn't check for circularity. You can manually check for circularity errors by using the **Check** function on the **BOM line** page. If circularity exists, the error is also reported when you perform cost rollup calculations and planning calculations.

1. **BOM:** The circularity check occurs when you do any of the following activities: close the **Bills of materials** page, use the **Check** function on the **Bills of materials** page, or associate a BOM with a BOM version.

Note that the controls preventing a circular BOM don't apply to a production BOM on a production order. You can manually add a component or consume a component that creates BOM circularity. When the component consumption reflects BOM circularity, the inventory closing process might not calculate a sensible cost for a manufactured item that has an inventory valuation method using actual cost. In such an occurrence, the use of a manufacturing indirect cost of the surcharge type can also cause problems in inventory closing, because the calculated cost can grow exponentially.

For the **Circularity check** field, two selections are available: *Optimize for low complexity* and *Optimize for high complexity*.

1. The *Optimize for low complexity* option requests data from storage as it's needed for the circularity check. For single-level or simple BOM structures, performance is better when you select this option.

1. When you select *Optimize for High complexity*, the system caches the BOM structure and all its dependencies before processing the circularity check. When processing a BOM with many lines, it might take a moment for the processing to start since it's loading the information into cache. However, the Optimize for High complexity option can significantly improve overall performance of the circularity check. This improvement is especially true if you're running a task that performs a circularity check on multiple BOMs or if you're doing a consistency check on the Bills of materials.

For more details, see this guide. <!-- KFM: Is a link missing here? What guide do you mean? -->

You can also use the following SQL query to fetch the items with circular links directly from the database. You can also convert this query to an X++ script and execute it.

``` sql
select p.itemid, c.itemid, p.REFERENCECATEGORY, c.REFERENCECATEGORY, c.REFERENCEID, p.REFERENCEID, *  
from INVENTTRANSORIGINASSEMBLYCOMPONENT a, INVENTTRANSORIGIN p, INVENTTRANSORIGIN c  
where a.ASSEMBLYINVENTTRANSORIGIN=p.RECID  
  and a.COMPONENTINVENTTRANSORIGIN=c.RECID  
  and p.ITEMID=c.ITEMID  
  and p.DATAAREAID=c.DATAAREAID  
  and p.DATAAREAID = 'abc'; 
```

### What are the best practices for executing inventory closing and recalculations?

Run inventory closing and recalculation during off-peak business hours when the overall system load is lower. This schedule increases the availability of resources.  

Always run inventory closings, recalculations, and resume calculations as batch processes for better performance and error tracing.  

Verify the inventory closing parameters to ensure they fit your business operations.  

If you have a high transactional volume for a period that might prolong the closing run, divide the period into smaller time intervals and close those periods consecutively.  

If recalculation takes a long time, check when you last ran closing. You can view this information on the **Closing and adjustment** page by filtering the **Type** as *Closing*. If you didn't run closing recently and your inventory includes items that use periodic valuation methods, run inventory closing for the period nearest to your recalculation period.  

Closing the inventory closes the transactions and reduces the scope and volume for further inventory operations. Recalculation runs based on your business requirements to report the accurate costs of the items.

### How can I analyze the issue and receipt transactions as part of the inventory closing and recalculation process?

Inventory closing and recalculation settle and adjust issue transactions to receipt transactions. If there aren't enough receipt transactions, the process temporarily stores many issue transactions in memory while processing closing and recalculation. Run inventory closing or recalculation when the number of issue and receipt transactions is comparable. You can view the summarized view of issue versus receipt transactions in the inventory value report.  

You can also view this information directly from the database by running the following query:

``` sql
select ITEMID, STATUSISSUE, count(*) countOfOpenTrans 
from InventTrans 
where PARTITION = 5637144576 
  and DATAAREAID = 'abc' 
  and STATUSISSUE <= 1 
  and STATUSRECEIPT <= 1 
  and VALUEOPEN = 1 
  and DATEFINANCIAL <= 'closing_trans_date' 
group by ITEMID, STATUSISSUE 
order by ITEMID, STATUSISSUE, countOfOpenTrans desc;
```

### What are the best practices for executing inventory reversals?

Run inventory reversals during off-peak business hours to make better use of system resources.  

Always run inventory reversals one at a time. Running multiple reversals at the same time might lead to errors or even ledger data corruption.

The **Extra batch helpers** field on the **Inventory and warehouse closing parameters** page <!-- KFM: I can't find this page, Please add navitagion info. --> decides the number of parallel threads to use for the reversal task, based on thread pool availability. The recommended and default number of extra batch helpers is *8*. If your reversal execution is very slow, consider increasing this value based on the real-time system resources availability.  

### Why did my inventory closing or recalculation end in an error? What should I do?

Several issues can cause inventory closing, recalculation, or reverse to end in an error. To find the exact error message, check the **Batch jobs** pagefor the related batch job and the **Closing and adjustment** page after you select the specific voucher, then view log details. If you can't fix these issues, contact Microsoft Support or your partner.

Possible reasons for errors include:  

- Overutilization of system resources

- SQL deadlock or availability issues

- Business data corruption and inconsistencies like rounding or currency issues

- Incorrect business practices  

- Configuration issues like ledger, account, project, or warehouse setup

- And many more

### When should I use the on-hand inventory adjustment on the Closing and adjustments page?

You can run the on-hand inventory adjustment only after you complete an inventory close. Typically, you run it for the date after the last close. The on-hand adjustment can adjust only inventory that's still on hand as of the date when you run the adjustment.

### When should I use the inventory transaction adjustment on the Closing and adjustments page?

Use the inventory transaction adjustment before you run an inventory close. Typically, use it to correct an incorrect receipt. You can't post the inventory transaction adjustment after you run an inventory close and settle the transaction.

### Are purchase order returns treated like other issues during the inventory close?

Yes. A purchase order receipt is an issue that the heuristic model you select for the item settles to a receipt. If you use a periodic costing model, you can use marking to override the heuristic cost.

### What happens to sales order returns during the inventory close?

When you run the inventory close, the system treats a sales order return as a receipt into inventory. The system settles issues against the inventory based on the heuristic model that you select for the item.

### What cost price is used on a sales order return?

When you create a return that relates to a sales order, the system copies the value of the **Unit price** field from the original sales order. The system sets the **Return cost price** field on the return to the adjusted cost price from the original inventory transaction for the sales order line that you're returning. If you set the **Value open** option for the related inventory transaction to *Yes*, the inventory close can update the issue cost on the original sales order. The **Return cost price** field isn't updated in this scenario. However, when you post a return order packing slip, the system checks the cost price and uses the updated cost on the return inventory transaction.

For a return of a standard cost item that relates to a sales order, the system uses the standard cost from the time of the original sales order, even if a new standard cost is active for the item.

When you create a return that doesn't relate to a sales order, the system sets the **Return cost price** field to the active item price that you have for the item in the site that you're creating the return order for. If you don't have an active cost price in a costing version for the item, the value is 0 (zero). If you leave the value as 0 (zero), you receive a warning that states that the return lot ID or return cost price isn't specified.

## Costing sheet and indirect costs

### Which costing models support the costing sheet?

Although organizations that use standard costing typically use the costing sheet, you can use it with any costing model that's available in Supply Chain Management.

### Can I have multiple costing sheets for various parts of my organization?

No. You can have only one costing sheet per legal entity.

### Can I have different costing sheets for each site?

No, you can't have a different costing sheet for each site. You can create only one costing sheet for each legal entity. However, you can configure total nodes, cost groups, or indirect cost nodes per site. This configuration is a manual process, and you must maintain the hierarchy and item assignments on the costing sheet when organizational or operational changes occur. If a single item is produced or purchased in more than one site, there's no mechanism that lets you treat the item differently on the costing sheet for each site. All indirect cost codes have a rate or surcharge that is defined in your costing version. The costs that you define are always site specific.

### Can I deactivate and activate versions of the costing sheet?

Although the system doesn't keep detailed version history for the costing sheet, you can make changes to the costing sheet and then, when you're ready, save and validate it. There's no mechanism that lets you go back to an older version of the costing sheet or view the changes that you made to the costing sheet. If you start changes and don't want them to take effect, you can close the page without saving and validating the changes. You're prompted to discard the changes.

### Can I create indirect costs for each item?

On your costing sheet, you can create indirect cost codes where the **Node type** field is set to *Surcharge*, *Rate*, or *Output unit based*. You can then define the rate or surcharge so that it's specific to an item number. On the **Rate** or **Surcharge** FastTab, add a row to the grid. Set the **Valid for** field to *Table* and the **Relation** field to the specific item number.

### Can I create an indirect cost that isn't related to a specific item?

Yes. You can create an indirect cost code where the **Node type** field is set to *Output unit based*. You can then set the **Subtype** field to *Quantity*, *Weight*, or *Volume* to specify the quantity, weight, or volume of the item that you're producing. The rate that you specify on the **Rate** FastTab is applied to the subtype that you selected. For example, you set the **Subtype** field to *Quantity* and the **Rate** field to *1.00 USD*, and then create a production or batch order for a quantity of 10. In this case, the indirect cost that is added to the finished good is 10.00 USD.

### Can I use the costing sheet to split my production costs by hours and materials?

Yes. You can create **Total** nodes on your costing sheet to separate the costs by any grouping that you choose. For example, you can create one **Total** node that is named *Hours* and another that is named *Materials*. Under the **Hours** node, add each code group that is related to your hours. Under the **Materials** node, add each cost group that is related to your materials.

## Dimension groups

### Can I manage cost at the batch or serial number level?

Yes, if you're using a periodic costing model such as FIFO, LIFO, LIFO date, weighted average, or weighted average date, you can enable the **Financial inventory** option for the **Batch** or **Serial number** dimension in the tracking dimension group to track costs at a detailed level.

### Can I manage costs at the location level?

No, you can't enable the **Financial inventory** option for the **Location** dimension in the storage dimension group. If your organization must track costs at a more detailed level, consider whether you can create virtual warehouses, and then select the **Financial inventory** option for the **Warehouse** dimension in your storage dimension group.

### Should I enable the Use warehouse management processes option for the storage dimension group?

If you think that you might want to use the warehouse management processes (WMS) features in the future, you should enable the **Use warehouse management processes** option. After you save a storage dimension group, you can no longer change the setting of the **Use warehouse management processes** option for it. If you decide to use warehouse management processes later, you'll have to create a new warehouse where the option is enabled. There's no automated process that you can use to move all the inventory from one warehouse to another warehouse, or to copy related configurations to a new warehouse.

### Can I enable the Use warehouse management processes for the storage dimension group even if I'm not planning to use warehouse management processes (WMS)?

Yes, even if you don't plan to use the warehouse management processes (WMS) features, you can enable the **Use warehouse management processes** option for the storage dimension group. To create and process transactions, you need to complete the minimum configuration, such as reservation hierarchies and unit sequence groups. However, the settings for WMS are generally ignored when you manually process picking lists, packing slips, and product receipts (for example, on the sales order and purchase order pages).

### When should I enable the Physical inventory option for a storage or tracking dimension group?

Enable the **Physical inventory** option for storage and tracking dimension groups when you need to keep detailed inventory records based on that dimension. Typically, any dimension that is active is also physically tracked. Therefore, the system tracks any receipt, issue, or movement of the inventory by the selected dimension. If a dimension isn't mandatory (for example, the license plate), you can enable the **Blank receipt allowed** and **Blank issue allowed** options to let users receive, issue, or move inventory even when the dimension isn't specified.

### When should I enable the Financial inventory option for a storage or tracking dimension group?

Enable the **Financial inventory** option for storage and tracking dimension groups when you need to keep detailed financial records based on that dimension. The **Site** dimensions are always financially tracked, whereas other dimensions are optional for financial tracking. If you use a periodic costing model such as FIFO, LIFO, or weighted average, enabling the **Financial inventory** option for a dimension indicates that you make settlements only in cases where the receipt and issue have the same dimension values. For example, if you enable the **Financial inventory** option for the **Warehouse** dimension, you have a different cost in each warehouse, and receipts and issues from different warehouses can't be settled.

### Can I make changes to a product, storage, or tracking dimension group after transactions exist?

After you create an item model group, you can change the setting of the **Coverage plan by dimension**, **For purchase prices**, and **For sales prices** fields if you select the **Active** checkbox for a dimension in the item model group. You can't make any other changes. For example, you can't enable or disable the **Active**, **Blank issue allowed**, **Blank receipt allowed**, **Physical inventory**, and **Financial inventory** options.

### Can I change the product, storage, or tracking dimension group for a released product?

If the on-hand inventory for a product is 0 (zero), and you set the **Value open** option to *No* for all the inventory transactions, you can change the storage and tracking dimension groups on the released production page. You can't change the product dimension group after the record is created.

## Item model groups

### When should I enable the Stocked product option?

Enable the **Stocked product** option for any item that you want to track in your inventory. When you enable this option, the system keeps detailed inventory transactions that track the receipt and issue of the item. Typically, you enable this option for any tangible item that you keep in your warehouse. You should also enable this option if you plan to add a non-tangible item such as a service item to your bills of materials (BOMs) or formulas. If you don't enable the **Stocked product** option, the system doesn't track any inventory transactions in the inventory subledger, and the cost of the items is typically expensed into your general ledger. For example, you might use this option for shop supplies or services that aren't included in your BOMs or formulas.

### When should I enable the Post physical inventory option?

Typically, you enable the **Post physical inventory** option when you also enable the **Stocked product** option. When you enable this option, the system tracks the physical update to the item on the inventory transaction. Use this option in coordination with parameters in Accounts payable, Accounts receivable, and Production control that specify that the physical update should create a voucher. You typically enable this option when you want the ledger to be updated whenever you physically update the inventory. If Supply Chain Management isn't your system of record for financials, you might want to disable this option.

### When should I enable the post Financial inventory option?

Typically, you enable the **Post financial inventory** option when you also enable the **Stocked product** option. Use this option in coordination with parameters in Accounts payable, Accounts receivable, and Production control that specify that the financial update should create a voucher. You typically enable this option when you want the ledger to be updated whenever you financially update the inventory (for example, by invoicing sales orders and purchase orders, or ending a production order). If Supply Chain Management isn't your system of record for financials, you might want to disable this option.

### When should I enable the Post to Deferred Revenue Account on Sales Delivery option?

Use the **Post to Deferred Revenue Account on Sales Delivery** option to indicate whether you want to recognize revenue in the general ledger when you post a packing slip for a sales order. Use this option when there's a long delay between the packing slip and invoice on a sales order, or when it's not possible to invoice all sales orders in the period. Typically, disable this option if you post your sales order invoices immediately after you post the packing slip. In this way, you avoid generating extra general ledger postings that are immediately reversed when you invoice a sales order.

### When should I enable the Accrue liability on product receipt option?

In most organizations, enable the **Accrue liability on product receipt** option for all item model groups, regardless of whether you have a stocked product or a not-stocked product. Use this option to post an accrual to the general ledger, based on product receipt price. Because there's typically a delay between posting of the product receipt for a purchase order and posting of the invoice, most organizations must recognize the liability on the balance sheet to comply with local regulations such as Generally Accepted Accounting Practices (GAAP). If Supply Chain Management isn't your system of record for financials, you might want to disable this option. If your organization uses procurement categories on purchase orders, you can control the accrual requirement by enabling the **Accrue purchase expense on receipt** option for the category policy rule on the **Purchasing policies** page.

### How can I prevent a user from posting a purchase order product receipt if a receipt registration isn't yet posted?

You can prevent a user from posting a purchase order product receipt if a purchase order registration isn't yet posted by enabling the **Registration requirements** option for the item model group. Use this option in organizations that use a two-step receiving process, or in scenarios where you must register a batch or serial number, for example, on the items that you're receiving. The **Registration requirement** option applies to *all* inventory receipts for an item, not just to purchase orders. For example, it applies to an inventory journal that has a positive quantity and a production order report as finished journal.

### How can I prevent a user from posting a purchase order invoice if a product receipt isn't yet posted?

You can prevent a user from posting a purchase order product invoice if a purchase order product receipt isn't yet posted by enabling the **Receiving requirements** option for the item model group. Use this option in organizations that require that receipts be physically recognized in the general ledger for accruals. The **Receiving requirement** option applies to *all* inventory receipts for an item, not just to purchase orders. For example, it applies to an inventory journal that has a positive quantity and a production order report as finished journal. If your organization uses procurement categories on purchase orders, you can control the requirement for a receipt by enabling the **Receiving requirements** option for the category policy rule on the **Purchasing policies** page.

### How can I prevent a user from posting a sales order packing slip if a sales order picking list isn't yet posted?

You can prevent a user from posting a sales order packing slip or invoice if a sales order picking list isn't yet posted by enabling the **Picking requirements** option for the item model group. Use this option in organizations that perform a physical picking process in the warehouse (for example, by using the warehouse mobile device to do picking). The **Picking requirement** option applies to *all* inventory issues for an item, not just to sales orders. For example, it applies to an inventory journal that has a negative quantity and a production order picking list journal.

### How can I prevent a user from posting a sales order invoice if the sales order packing slip isn't yet posted?

You can prevent a user from posting a sales order invoice if a sales order packing slip isn't yet posted by enabling the **Deduction requirements** option for the item model group. Use this option in organizations that perform a physical packing process in the warehouse (for example, by using the Warehouse Management mobile app to do packing or by generating a document that will be included with the items that are shipped). The **Deduction requirement** option applies to *all* inventory issues for an item, not just to sales orders. For example, it applies to an inventory journal that has a negative quantity and a production order picking list journal.

### Can I prevent items that are registered from being sold?

When you register an item in your inventory in Supply Chain Management, the quantity is physically available to be issued in the system. If items that you registered but didn't yet receive shouldn't be available to be issued to sales orders or production orders, for example, consider using the inventory status, inventory blocking, quality orders, quarantine orders, or reservations features to manage the business process.

## Production costing

### Can I use one costing model for raw materials and a different costing model for finished goods?

Yes, you can use different costing models for each item. It's common for manufacturers to use a periodic costing model for raw materials and standard cost for semi-finished and finished goods.

### How can I drive overhead off machine costs?

To drive overhead off your machine costs, you must create resources and resource groups for each machine, according to your business requirements. You can assign each resource or resource group to cost categories to control the cost of the machine. You can link each cost category to a cost group, and use each cost group as the basis for calculating indirect costs on the costing sheet.

### How do I recognize cost that is related to energy consumption (for example, water, energy, or gas consumption) on the costing sheet?

You can generally recognize costs related to energy consumption in one of two ways:

- Create a line in your BOM or formula. Typically, you create this line as a service item, and you can specify the unit of measure that you're consuming in relationship to the quantity you're producing. In this way, the user can consume a different amount during the production process. You can automatically consume the items based on the value that you select in the **Flushing principle** field.
- Create an indirect cost on your costing sheet. Typically, you use this approach to allocate the total cost of your energy consumption across your production process. You can use the cost group and the absorption basis to scale the consumption based on materials or labor in your route, for example.

Select the best option based on your reporting, reconciliation, and operational requirements.

### Can I capture resource details in the BOM or formula?

You can capture resource details only in a route operation. Although you can create a service item to represent a resource and assign a cost to increase the cost calculation for a finished good, we don't typically recommend this approach. Instead, create a simple route that has one line to track the resource costs, and configure the operation so that it's automatically consumed at either the start or the end of the production order.

### Can I view the calculation details if I manually enter the cost?

No. If you manually enter the price on the **Item price** page, the **View calculation details** and **Report calculation details** buttons aren't available. If you select the **Cost rollup by cost group** button for a cost price that you manually enter, a summarized line is shown, and all costs roll up to the finished good item.

### Does the system calculate variances on a production order when I manually enter the cost?

Yes, the system calculates variances when you manually enter a standard cost. However, when you manually enter a standard cost instead of calculating it, all material, route, and indirect cost consumptions in the production order are considered a substitution variance. If there are additional variances, such as consumption of extra materials or labor, the system also records them as variances from the production BOM. Therefore, always run a calculation for items that have a BOM, route, or indirect costs.

### How can I carry the variances from a subproduction order to the parent production order?

When you use a periodic costing model such as FIFO, LIFO, or weighted average, the costs from a subproduction are recognized in the heuristic model that you select for the items. If you require actual costing, use the marking principle to indicate which subproduction is issued to a parent production order. Alternatively, use the **Financial inventory** option for the **Batch** or **Serial number** dimension in the tracking dimension group.

### How does the flushing principle affect consumption?

The flushing principle on a BOM, formula, or route line controls the timing and technique that the system uses to consume the item or labor. If you select *Start*, the system automatically consumes the item or labor when you start the production order. If you select *Finish*, the system automatically consumes the item or labor when you report the production order as finished. If you select *Manual*, a user must manually pick materials or record the time in a job or route card journal. BOMs and formulas also have an *Available on location* option. If you select this option, the system automatically consumes the items after it transfers them to the production floor location.

### How should I run cost calculations if I have multilevel BOMs or formulas?

In general, start at the lowest level of your BOMs or formulas for the calculation. To make filtering easier when you mass-run cost calculations, use calculation groups to help segregate products. Run the *Recalculate BOM levels* periodic job before you start to mass-run cost calculations. Each organization should consider the mix of products and define a strategy that meets the specific needs of your product and BOM or formula structures.

## Transfer order costing

### Is there a way to allocate freight to a transfer order cost?

Add charges to a transfer order to add costs. The charges code defines the debit and credit for the charge that you're adding. First, create charges codes in the **Inventory management** module. To add a charge to a transfer order, select **Charges** on the transfer order line that you want to add a charge to.

## Variances

### Can I treat variances differently, based on the site or warehouse?

There's no option to configure variance accounts by site. When you use standard costing for a released product, you can select the main account that is used for standard cost variance postings on the **Posting** page. You can select to configure the accounts for one item, a group of items, or all items. You can also configure one cost group, a group of cost groups, or all cost groups.

### Can I separate variances that are the result of currency exchange rates from other types of variances?

If a variance results from a currency exchange rate difference between the purchase order price and the standard cost for an item, you can't separate the exchange rate difference from other variances.

## Reporting

### How many inventory value report configurations can I create and use?

You can create unlimited inventory value report configurations. Evaluate your specific reporting requirements and create the number of configurations that you need to meet those requirements. You need at least one inventory value report configuration to run the report or the report storage option.

### Can I use the inventory value report to analyze the cost of an item in each warehouse?

Yes. You can enable the **View** or **Total** option for each **Warehouse** dimension in the inventory value report configuration. However, the report shows values only for dimensions where the **Financial inventory** option is enabled for the storage dimension group. For other dimensions, it shows blank columns. Learn more in [Inventory value report examples and logic](inventory-value-report-examples.md).

### How can I view the inventory quantity as of a specific date with the weighted average?

You can use the **Inventory aging** report, which includes an **Average unit cost** column that shows the value of inventory as of a specific date. Learn more in [Inventory aging report examples and logic](inventory-aging-report.md).

### How can I view which receipt transactions are settled against an issue transaction?

You can view the settlements for an inventory transaction by selecting **Settlements** or **Cost explorer** on the **Inventory** tab on the Action Pane of the **Inventory transaction** or **Inventory transaction details** page. If you select a receipt to view the issues that are related to the transaction, the cost explorer doesn't show the details. Details are shown only if you select an issue transaction.

### How does the inventory value report show items that have a positive physical quantity and a negative financial value?

The inventory value report separates the physical and financial amounts and quantities into their own columns. The values that are shown on the report are as of the date range that you selected when you ran the report. The level of summarization that is shown depends on the settings that you selected. If an item has transactions that are physically received and financially issued, the quantities and values are summed independently. If you select to view the detail level as transactions, rows for each receipt and issue are shown separately, and the physical and financial quantities and amounts, respectively, are shown. Learn more in [Inventory value report examples and logic](inventory-value-report-examples.md).

### What is the impact of storage and tracking dimension groups on the inventory value report?

If you enable the **Financial value** option for a dimension in a storage or tracking dimension group, you can select the **View** or **Total** option for the dimension in the inventory value report configuration. If you select the **View** or **Total** option for a dimension where the **Financial value** option isn't selected, the column is blank in the report output. If you enable the **Financial value** option for a dimension in a storage or tracking dimension group, and you don't select the **View** or **Total** option on the inventory value report configuration, the system summarizes the values for the selected dimensions where they are financially tracked.

### Can I customize the Power BI embedded reports for costing?

Yes, users who have the correct security permissions can update the report design canvas for any Power BI embedded report in Supply Chain Management. Learn more in [Customize embedded reports in analytical workspaces](../../fin-ops-core/dev-itpro/analytics/customize-analytical-workspace.md).

### Where can I view the variance analysis statement?

You can access the variance analysis statement by going to **Cost management \> Inquiries and reports \> Inventory accounting – analysis reports** or **Cost management \> Inquiries and reports \> Manufacturing accounting – analysis reports**. Both options open the same report, and the report has the same behavior.

## Item prices and default costs

### Can I maintain the cost for each product variant?

Yes. You can enable the **Use cost price by variant** option on the **Manage cost** FastTab of the **Released product** page to enable pricing by product variant. (This option is available only for product masters.) Then, on the **Item price** page (which you can open from either the **Costing version** page or the **Released product** page), you can select **Dimensions display** to specify whether you want to show the **Configuration**, **Size**, **Color**, or **Style** dimension. To save the setup and use the selected dimensions every time that you open the page, enable the **Save setup** option, and then select **OK**. You can enter the dimensions only for items where the dimensions are active in the product dimension group.

### Can I maintain the cost for each warehouse?

No, you can't maintain the item price by warehouse. However, you can maintain trade agreements for purchase prices or sales prices by warehouse. First, select the **For purchase prices** or **For sales prices** option for the dimension on the **Storage dimension group** page. Then, when you create the trade agreement journal and open the lines for the dimensions, select **Inventory \> Display dimensions** to select which dimension should be shown in the grid. To save the setup and use the selected dimensions every time that you open the page, enable the **Save setup** option, and then select **OK**. You can enter the dimensions only for items where the dimensions are active in the product dimension group.

### What are price charges?

Price charges provide a way to add a fixed amount to the unit price of the item price or trade agreement. When you enter an amount in the **Price charges** field, you can also enter a value in the **Charges quantity** field. The price charges are amortized over the charges quantity that you specify. Enable the **Incl. in unit price** option if you want to include the price charges in the unit price for the item. This option is always enabled for a standard cost.

### How should I configure prices for items that are procured in multiple currencies?

If you enter a default price in the **Purchase price** field on the **Released product** page, the system assumes the price is in the accounting currency of the ledger for the legal entity that you're in. Likewise, if you enter a purchase price in a costing version where the **Price type** field is set to *Purchase*, you assume the price is in the accounting currency of your legal entity. When you create a purchase order for a vendor that has a different currency, the system automatically converts the currency from the accounting currency amount to the transaction currency by using the exchange rate that you specify in the **Accounting currency exchange rate type** field in your ledger.

When you create a trade agreement journal, you can specify the currency that you're expressing the price in on each line. You can create trade agreements for multiple currencies, specific vendors, and many other combinations of factors. If you create a purchase order where a trade agreement exists for the currency that you selected, the system uses the trade agreement that has the matching currency. When you post transactions such as product receipts or invoices, the amount is converted to the ledger's accounting currency by using the accounting currency exchange rate that you specify in the ledger.

### How should I configure costs for items that are procured in multiple currencies?

You can't configure costs in more than one currency. The cost that you specify for the item price or default costs that you enter in the **Price** field on the **Manage cost** FastTab of the **Released product** page are always expressed in the accounting currency of the ledger for the legal entity that you select.

If your organization uses standard costing, you should define a strategy for defining the costs when there are multiple currencies. You should also define a process for regularly updating the cost to help reduce the number of variances that are posted.

### Can I use the Profit setting on the Cost group page to calculate sales prices?

Yes, you can use the **Profit** setting on the **Cost group** page to add a percentage when sales prices are calculated by using a cost calculation. Learn more in [BOM calculations](bom-calculations.md).

## Marking

### How does marking affect periodic costing models?

If you use a periodic costing model such as FIFO, LIFO, or weighted average, and you mark a receipt transaction against an issue transaction, the inventory close process ignores the heuristic model of the item. Instead, the system uses the actual cost of the receipt for the cost of the issue.

### What happens during the inventory close when I use marking?

When you mark receipts and issues, the inventory close settles the marked transactions together. When marking is used to create the settlement, the **Principle** field on the **Settlement** page is set to *Marking*. If you mark a transaction before physically or financially updating it, the issue uses the marked receipt's cost instead of the running average cost. If you mark the transactions after the financial update, the inventory close and adjustment process adjusts the issue cost so that it matches the receipt cost.

### Can I manually mark transactions when I use standard costing or moving average?

No, you can't manually mark receipts or issues when you use standard costing or moving average. If transactions (for example, direct delivery or intercompany orders) are automatically marked, the marking record remains and acts as a hard reservation. However, when you use standard costing or moving average, the marking of records has no effect on the cost of the items.

### How does marking affect the profit and loss statement?

When you mark an issue transaction against a receipt, the cost for the issue matches the selected receipt. When you physically and financially post the issue, the posting affects the **Cost of goods sold, delivered** and **Cost of goods sold, invoiced** accounts that you specify in the inventory posting profile. If you mark a transaction after the physical or financial update, the *Inventory close and adjustment* process creates an adjustment that has a matching voucher that adjusts the **Cost of goods sold, invoiced** account and offsets to the account that you specify for **Cost of units, invoiced** (inventory).

### How does marking affect master planning?

The **Standard update** tab on the **Master planning parameters** page includes a field named **Update marking**. The option that you select is used when you firm a planned order that master planning generates. The following options are available:

- *No* – The system doesn't perform any marking.
- *Standard* – The system marks receipts against issues according to the pegging. A requirement order is marked against a fulfillment order. If some quantity remains on the fulfillment, the fulfillment order isn't marked.
- *Extended* – The system marks both the requirement orders and fulfillment orders, regardless of whether any quantity remains open on the fulfillment order.

## <a name="negative-inventory"></a>Negative inventory

### When should I allow physical negative inventory?

In general, don't allow physical negative inventory, because you can't have less than zero of a tangible item in your warehouse. However, some industries and business scenarios require physical negative inventory. For example, retailers might not want to prevent the sale of an item that a customer brings to the register, even when the system indicates that no items are available. Process manufacturers provide another example. For these manufacturers, the amount that is consumed can exceed what is recommended in the formula. Alternatively, the consumption might be estimated instead of precise, so that the consumption exceeds the amount in a specific location, such as a tank.

Whenever possible, evaluate your business process and try to improve it to ensure that inventory can't be negative. If you must allow negative inventory, establish a clear business process for correcting the negative inventory, because it can adversely affect costing.

### When should I allow financial negative inventory?

In general, allow financial negative inventory. (In most cases, the system doesn't process purchase order invoices before you can ship the items.) Enable this option when you have specific business processes that require the sales price to reflect the final cost of a purchase order. For example, this requirement might apply in a make-to-order industry or in specific regions where it's dictated by law.

### What happens to the cost of my issues when the inventory is negative?

When the inventory for your item is negative, and you issue more items than you physically have, the system uses the default item price to calculate the running average if you use a periodic costing model such as FIFO, LIFO, or weighted average. If you don't specify a default price for the item, the system issues the inventory with a value of zero. This behavior can cause future calculations of your running average or moving average to be inaccurate.

### Can I prevent items from being picked, packed, or sold on sales orders and production orders if there isn't enough on-hand inventory?

Yes. Disable the **Physical negative** option for the item model group to prevent items from being picked, packed, or sold on sales orders and production orders.

### Can I prevent items from being invoiced on a sales order if no purchase orders have been invoiced for the same item?

Yes. Disable the **Financial negative** option for the item model group to prevent items from being invoiced on a sales order if no purchase orders are invoiced for the same item.

### How does negative inventory affect financial ratios such as gross profit margin?

When you allow your inventory to go negative, the inventory value in your balance sheet and the cost of goods sold in your profit and loss statement can be understated, especially if you don't configure a default price for your items. Therefore, financial reporting and ratios such as gross profit margins can be overstated, because the cost is incorrect. If you use a periodic costing model such as FIFO, LIFO, or weighted average, you can adjust the value of the issues when you run the inventory close and adjustment process after the negative inventory quantities are corrected. However, if you use moving average, there's no way to revalue the individual transactions.

### How do I correct negative inventory?

Frequently monitor and correct negative inventory when your organization or business requirements dictate that you allow your inventory to go negative. You can correct the inventory values by performing a cycle count, posting an adjustment, or posting a movement journal. If you must recognize the unexpected gains in inventory in a specific general ledger account, plan to use a movement journal. Otherwise, when you use the cycle counting or inventory adjustment process, the system posts the inventory adjustment to the **Inventory receipt** account and offsets to the **Inventory expenditure, profit** accounts that you specify on the inventory posting profile.

### Do I have to create a new item if my inventory goes negative and I use moving average?

No. If your organization allows inventory to go physically negative, and you're using moving average as your inventory model, the system uses the fallback cost sequence that you assign on the **Inventory and warehouse management parameters** page to determine how the system assigns cost to your issues. In general, avoid allowing your inventory to go physically negative. For more information, see the other questions in the [Negative inventory](#negative-inventory) section of this article.

## Not-stocked products

### Can I post sales order picking lists for not-stocked products?

When you generate a picking list for a sales order that includes items in an item model group that isn't stocked, you don't see any lines for those not-stocked items. You can't use the Warehouse Management mobile app to process not-stocked items.

When you generate a packing slip for a sales order that includes items in an item model group that isn't stocked, set the **Quantity** field to *Picked quantity and not stocked products* to include the not-stocked items in the document generation. If you select *All*, only stocked items are included in the packing slip.

### Should I use a not-stocked product or a category (sales category or procurement category)?

The choice between a not-stocked product and a category depends on your specific business requirements. Not-stocked products generally offer more control over default values, such as quantities and prices on purchase orders and sales orders. Therefore, use not-stocked products in scenarios where you purchase or sell the same product or service more than once. Categories are useful in scenarios where the price, items, descriptions, and so on are inconsistent from transaction to transaction. You can also use categories on any product to help classify the type of product that you're selling or purchasing.

## Service items

### What is the difference between a service item and a not-stocked product?

A service item is a product type. When you create a newly released product, you can set the **Product type** field to either *Item* or *Service*. Typically, select *Item* to indicate that the item is tangible, and select *Service* to indicate that the item is intangible.

Any released product, regardless of whether it's an item or service product, can be stocked or not-stocked. The stocked or not-stocked setting is controlled by the item model group that you select for the released product. When you select an item group that isn't stocked, the system doesn't create inventory transactions for the related sales order or purchase order, for example.

### Can I include not-stocked items in a BOM?

No, you can't include a released product that is linked to an item model group where the **Stocked** option is disabled in a BOM or formula. It doesn't matter whether the **Product type** field is set to *Item* or *Service*. You can only include stocked items on BOM or formula lines.

## Costing model–specific questions

### Which costing model should I use?

The costing model you select depends on your business requirements. Before you select a costing model to use in Supply Chain Management, validate that your local regulations allow the model. We recommend that you validate your selection with a certified accountant in your region.

### Can I use more than one costing model in my organization?

Yes. There's no limit to the number of item model groups or costing models that you can select in Supply Chain Management.

### Can I use more than one costing model for each item?

No. You can select only one costing model for each released product. The item model group controls this behavior. If you must use more than one costing model to report on inventory values, consider using the Global Inventory Accounting add-in.

### When I use manufacturing execution, which costing methodology should I use?

The costing model you select depends on your business requirements. There's no specific advantage or disadvantage to using any costing model when your organization also uses manufacturing execution.

### When is FEFO used?

First expired, first out (FEFO) isn't a costing methodology. Instead, it's a reservation technique that's often used in manufacturing organizations. You can enable FEFO reservations for an item model group by enabling the **FEFO date-controlled** option and then selecting a value in the **Pick criteria** field.

### Are there performance benefits to selecting one costing model over another?

In general, the costing model that you select for an item has minimal impact on the overall performance of the system. However, the inventory costing model that you select might affect the amount of time required to run the inventory close or recalculation process. For example, if you use standard cost or moving average, the inventory close process has minimal impact on the system, because it doesn't update each inventory transaction and create settlements. However, a periodic costing model such as FIFO, LIFO, or weighted average can increase the amount of time required to complete the inventory close process. Specifically, the close process can be longer when you enter a high number in the **Maximum number of iterations allowed per item** field or a low number in the **Minimum amount allowed** field for the *Close inventory* process.

### When should I use the Fixed receipt price option?

When you select the **Fixed receipt price** checkbox on the **Item model group** page for an item, the system uses the receipt price as the standard cost for the inventory receipt. If there's a difference between the purchase price and the default item cost price that you configure for a product, the system posts the difference to the **Fixed receipt price profit** or **Fixed receipt price loss** account, and offsets it to the **Fixed receipt price offset** account. (You specify all these accounts on the **Posting** page.)

Select the **Fixed receipt price** checkbox when you use a periodic costing model such as FIFO, LIFO, or weighted average, and you want to track a purchase price variance in the ledger if the price of a receipt differs from the default item cost.

### Moving average

### Is moving average the same as a floating average?

The terms moving average, floating average, and running average are often used synonymously. Of these terms, moving average is the only official costing model that's available in Supply Chain Management. Although running average isn't an official costing model, it's the technique that is used when you use a periodic costing model such as FIFO, LIFO, or weighted average. The term floating average isn't used in Supply Chain Management and might have different connotations in other systems.

### How can I accommodate the difference between the product receipt price and invoice price when I use moving average?

When you use moving average, the physical cost (receipt price) is used to calculate the moving average for all issue transactions. If there's a difference between the physical cost (receipt price) and the financial cost (invoice price), the system automatically posts the difference to the main account that you specify for the **Price difference for moving average** posting type on the **Inventory** tab of the **Inventory posting profile** page.

### Where is the price difference for moving average presented in the general ledger?

When there's a price difference between the posting of a physical update and a financial update for a receipt, the system posts the difference to the main account that you specify for the **Price difference for moving average** posting type on the **Inventory** tab of the **Inventory posting profile** page. Learn more in [Moving average](moving-average.md).

### When I use moving average, what happens if there's an issue before the receipt?

Typically, there might be an issue before the receipt either because you allow physical negative inventory for the item model group or because the issue is backdated. Learn more in the [Negative inventory](#negative-inventory) section of this article.

If you backdate transactions, carefully consider your business process and operations to determine whether there's a way to avoid this scenario. If you backdate a transaction for an item that uses moving average, the system assigns the current moving average to the transaction. Later issues aren't adjusted. Learn more about moving average with backdated transactions in [Moving average](moving-average.md).

### Standard costing

### What is the difference between standard costing and fixed receipt price?

Standard costing requires that you define an item price and activate the cost in a costing version. The system uses that cost for all receipts and issues. The system records variances for the receipts to inventory in the general ledger by using the standard cost variance accounts that you specify on the **Standard cost** tab of the **Inventory posting profile** page.

However, when you use fixed receipt price, only the cost for receipts is fixed. The system uses the cost that you specify on the **Manage costs** FastTab of the **Released product** page. Differences between the default cost and the purchase order price cause the purchase price variance to be posted to the fixed receipt price profit and loss accounts. Issues don't use fixed receipt price. Instead, issues are valued at the running average at the time of posting (unless you use marking), and they're revalued to the heuristic model that you select when you run the inventory close.

### Can I use FEFO reservations with standard costing?

Yes, you can use FEFO reservations on an item model group when you select standard costing. FEFO reservations control the reservation logic that's used for the physical handling of the items, whereas standard costing controls the physical and financial cost for an item.

### Can I upload pending prices?

Yes, you can use the Excel add-in or the Data Management Framework to upload a pending price. Use the following entities:

- Pending item prices (V2)
- Pending route cost category unit costs
- Costing sheet node calculation factors (V2)

### How often can I update the standard cost for an item?

You can activate a new standard cost as often as you want. If you activate a new cost for an item on the same day that you activated the last cost, the system uses the most recent activated cost on new transactions or updates (such as updates to existing transactions).

### Can I deactivate or delete an activated cost?

No, you can't deactivate or delete an activated cost. If you incorrectly activate a cost, you can activate a new cost that has the correct cost.

### Are calculation groups used with standard costing?

You can use calculation groups with any item, regardless of the item model group that you choose. The cost rollup or cost calculation process uses the calculation groups to determine the settings for the items that you're running the calculation for. Learn more about calculation groups in [BOM calculations groups](bom-calculation-groups.md).

### When should I use a planned costing version?

Costing versions can have a type of *Standard cost* or *Planned cost*. Use the *Standard cost* type for costs that are active in the system and that you post in transactions. Use the *Planned cost* type for running simulations on costs. This type doesn't affect the cost of transactions.

### Can I transfer the total cost from one entity to another entity as the selling cost?

There's no automated way to copy costs from one company to another. Additionally, there's no automated way to copy costs from a purchase price to a sales price. If your organization must complete one of these tasks, consider whether you can use the Data Management Framework to export the data out of your costing version and upload it into a different company, either as a sales price in the costing version or as a trade agreement. You might need to manually manipulate the files.

### What's the best way to copy planned costs to a standard costing version?

You can use the **Copy** button on the **Costing versions** page to copy item prices, cost category prices, or indirect costs from one costing version to another.
