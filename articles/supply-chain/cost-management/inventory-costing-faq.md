---
title: Inventory costing FAQ
description: Access answers some frequently asked questions about inventory costing in Microsoft Dynamics 365 Supply Chain Management.
author: rachel-profitt
ms.author: raprofit
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 06/07/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Inventory costing FAQ

[!include [banner](../includes/banner.md)]

This article answers some frequently asked questions about inventory costing in Microsoft Dynamics 365 Supply Chain Management.

## Inventory close, adjustments, and recalculation

### Is the inventory close required?

If you plan to use the inventory archiving feature, the inventory close is required. If you don't plan to use the inventory archiving feature, we strongly recommend that you still run the inventory close, regardless of the costing models that you use.

### How often should the inventory close be run?

The inventory close should be run at least once per ledger period. For example, if your ledger is set to a calendar month–based fiscal calendar, you should run the inventory close once per month.

### Is the inventory recalculation required?

No, the inventory recalculation isn't required. If you use a periodic costing model such as first in, first out (FIFO), last in, first out (LIFO), or weighted average, you should carefully consider whether you'll run the inventory recalculation. It can provide more accurate costing in the heuristic models that you've selected.

### How often should the inventory recalculation be run?

If you're planning to run the inventory recalculation, we recommend that you consider running it daily as a batch process. If your organization doesn't require frequent reporting of the inventory values for periodic costing models, you can consider running the inventory calculation less often.

### When should I use the on-hand inventory adjustment on the Closing and adjustments page?

The on-hand inventory adjustment can be run only after an inventory close is completed. It's typically run for the date after the last close. The on-hand adjustment can adjust only inventory that is still on hand as of the date when you run the adjustment.

### When should I use the inventory transaction adjustment on the Closing and adjustments page?

You should use the inventory transaction adjustment before you run an inventory close. It's typically used to correct an incorrect receipt. You can't post the inventory transaction adjustment after an inventory close is run and the transaction is settled.

### Are purchase order returns treated like other issues during the inventory close?

Yes. A purchase order receipt is an issue that is settled to a receipt in the heuristic model that you select for the item. If you're using a periodic costing model, you can use marking to override the heuristic cost.

### What happens to sales order returns during the inventory close?

When you run the inventory close, a sales order return is treated as a receipt into inventory. Issues are settled against the inventory, based on the heuristic model that you select for the item.

### What cost price is used on a sales order return?

When you create a return that is related to a sales order, the value of the **Unit price** field is copied from the original sales order, and the **Return cost price** field on the return is set to the adjusted cost price from the original inventory transaction for the sales order line that is being returned. If the **Value open** option for the related inventory transaction is set to *Yes*, the inventory close can cause updates to the issue cost on the original sales order. The **Return cost price** field isn't updated in this scenario. However, when you post a return order packing slip, the system will check the cost price and use the updated cost on the return inventory transaction.

For a return of a standard cost item that is related to a sales order, the system will use the standard cost from the time of the original sales order, even if a new standard cost is active for the item.

When you create a return that isn't related to a sales order, the **Return cost price** field is set to the active item price that you have for the item in the site that you're creating the return order for. If you don't have an active cost price in a costing version for the item, the value will be 0 (zero). If you leave the value as 0 (zero), you'll receive a warning that states that the return lot ID or return cost price isn't specified.

### What is the expected performance of the inventory close?

Many factors can affect the performance of the inventory close. These factors include the total number of items, the total number of transactions in the period, the inventory models that you use, and the number of batch helpers that you configure in the inventory and warehouse management parameters. You can expect that the closing might take as little as a few minutes or as much as several hours. There's no specific guidance about the amount of time that the close should take to run. You should define your nonfunctional business requirements for the performance of the inventory close and work closely with your partner to define the schedule for running the inventory close process. If you experience unexpectedly low performance of the inventory close process, you should open a support ticket.

## Costing sheet and indirect costs

### Which costing models support the costing sheet?

Although the costing sheet is most typically used in organizations that use standard costing, you can use it with any costing model that is available in Supply Chain Management.

### Can I have multiple costing sheets for various parts of my organization?

No. You can have only one costing sheet per legal entity.

### Can I have different costing sheets for each site?

No, you can't have a different costing sheet for each site. You can create only one costing sheet for each legal entity. However, you can configure total nodes, cost groups, or indirect cost nodes per site. This configuration is a manual process, and you must maintain the hierarchy and item assignments on the costing sheet when organizational or operational changes occur. If a single item is produced or purchased in more than one site, there's no mechanism that lets you treat the item differently on the costing sheet for each site. All indirect cost codes have a rate or surcharge that is defined in your costing version. The costs that you define are always site specific.

### Can I deactivate and activate versions of the costing sheet?

Although no detailed version history is kept for the costing sheet, you can make changes to the costing sheet and then, when you're ready, save and validate it. There's no mechanism that lets you go back to an older version of the costing sheet or view the changes that were made to the costing sheet. If you start changes and don't want them to take effect, you can close the page without saving and validating the changes. You'll be prompted to discard the changes.

### Can I create indirect costs for each item?

On your costing sheet, you can create indirect cost codes where the **Node type** field is set to *Surcharge*, *Rate*, or *Output unit based*. You can then define the rate or surcharge so that it's specific to an item number. On the **Rate** or **Surcharge** FastTab, add a row to the grid. Set the **Valid for** field to *Table* and the **Relation** field to the specific item number.

### Can I create an indirect cost that isn't related to a specific item?

Yes. You can create an indirect cost code where the **Node type** field is set to *Output unit based*. You can then set the **Subtype** field to *Quantity*, *Weight*, or *Volume* to specify the quantity, weight, or volume of the item that you're producing. The rate that you specify on the **Rate** FastTab will be applied to the subtype that you selected. For example, you set the **Subtype** field to *Quantity* and the **Rate** field to *1.00 USD*, and then create a production or batch order for a quantity of 10. In this case, the indirect cost that will be added to the finished good is 10.00 USD.

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

Yes, even if you don't plan to use the warehouse management processes (WMS) features, you can enable the **Use warehouse management processes** option for the storage dimension group. To create and process transactions, you'll have to complete the minimum configuration, such as reservation hierarchies and unit sequence groups. However, the settings for WMS are generally ignored when you manually process picking lists, packing slips, and product receipts (for example, on the sales order and purchase order pages).

### When should I enable the Physical inventory option for a storage or tracking dimension group?

You should enable the **Physical inventory** option for storage and tracking dimension groups when you must keep detailed inventory records based on that dimension. Typically, any dimension that is active will also be physically tracked. Therefore, any receipt, issue, or movement of the inventory will be tracked by the selected dimension. If a dimension isn't mandatory (for example, the license plate), you can enable the **Blank receipt allowed** and **Blank issue allowed** options to let users receive, issue, or move inventory even when the dimension isn't specified.

### When should I enable the Financial inventory option for a storage or tracking dimension group?

You should enable the **Financial inventory** option for storage and tracking dimension groups when you must keep detailed financial records based on that dimension. The **Site** dimensions are always financially tracked, whereas other dimensions are optional for financial tracking. If you use a periodic costing model such as FIFO, LIFO, or weighted average, enabling the **Financial inventory** option for a dimension indicates that you'll make settlements only in cases where the receipt and issue have the same dimension values. For example, if you enable the **Financial inventory** option for the **Warehouse** dimension, you'll have a different cost in each warehouse, and receipts and issues from different warehouses can't be settled.

### Can I make changes to a product, storage, or tracking dimension group after transactions exist?

After you create an item model group, you can change the setting of the **Coverage plan by dimension**, **For purchase prices**, and **For sales prices** fields if the **Active** checkbox is selected for a dimension in the item model group. No other changes are allowed. For example, you can't enable or disable the **Active**, **Blank issue allowed**, **Blank receipt allowed**, **Physical inventory**, and **Financial inventory** options.

### Can I change the product, storage, or tracking dimension group for a released product?

If the on-hand inventory for a product is 0 (zero), and the **Value open** option is set to *No* for all the inventory transactions, you can change the storage and tracking dimension groups on the released production page. You can't change the product dimension group after the record is created.

## Item model groups

### When should I enable the Stocked product option?

You should enable the **Stocked product** option for any item that will be tracked in your inventory. When this option is enabled, detailed inventory transactions are kept that track the receipt and issue of the item. This option is typically enabled for any tangible item that you keep in your warehouse, for example. You should also enable this option if you plan to add a non-tangible item such as a service item to your bills of materials (BOMs) or formulas. If you don't enable the **Stocked product** option, no inventory transactions are tracked in the inventory subledger, and the cost of the items is typically expensed into your general ledger. This option is often used, for example, for shop supplies or services that aren't included in your BOMs or formulas.

### When should I enable the Post physical inventory option?

The **Post physical inventory** option is typically enabled when the **Stocked product** option is enabled. When you enable this option, the system will track the physical update to the item on the inventory transaction. This option is used in coordination with parameters in Accounts payable, Accounts receivable, and Production control that specify that the physical update should create a voucher. You'll typically enable this option when you want the ledger to be updated whenever you physically update the inventory. If Supply Chain Management isn't your system of record for financials, you might want to disable this option.

### When should I enable the post Financial inventory option?

The **Post financial inventory** option is typically enabled when the **Stocked product** option is enabled. This option is used in coordination with parameters in Accounts payable, Accounts receivable, and Production control that specify that the financial update should create a voucher. You'll typically enable this option when you want the ledger to be updated whenever you financially update the inventory (for example, by invoicing sales orders and purchase orders, or ending a production order). If Supply Chain Management isn't your system of record for financials, you might want to disable this option.

### When should I enable the Post to Deferred Revenue Account on Sales Delivery option?

You use the **Post to Deferred Revenue Account on Sales Delivery** option to indicate whether you want to recognize revenue in the general ledger when you post a packing slip for a sales order. This option is typically used when you have a long delay between the packing slip and invoice on a sales order, or when it isn't possible to invoice all sales orders in the period. Typically, you'll disable this option if you post your sales order invoices immediately after you post the packing slip. In this way, you avoid generating extra general ledger postings that will immediately be reversed when you invoice a sales order.

### When should I enable the Accrue liability on product receipt option?

In most organizations, you'll want to enable the **Accrue liability on product receipt** option for all item model groups, regardless of whether you have a stocked product or a not-stocked product. This option is used to post an accrual to the general ledger, based on product receipt price. Because there's typically a delay between posting of the product receipt for a purchase order and posting of the invoice, most organizations must recognize the liability on the balance sheet to comply with local regulations such as Generally Accepted Accounting Practices (GAAP). If Supply Chain Management isn't your system of record for financials, you might want to disable this option. If your organization uses procurement categories on purchase orders, you can control the accrual requirement by enabling the **Accrue purchase expense on receipt** option for the category policy rule on the **Purchasing policies** page.

### How can I prevent a user from posting a purchase order product receipt if a receipt registration isn't yet posted?

You can prevent a user from posting a purchase order product receipt if a purchase order registration hasn't yet occurred by enabling the **Registration requirements** option for the item model group. This option is typically used in organizations that use a two-step receiving process, or in scenarios where you must register a batch or serial number, for example, on the items that you're receiving. The **Registration requirement** option applies to *all* inventory receipts for an item, not just to purchase orders. For example, it applies to an inventory journal that has a positive quantity and a production order report as finished journal.

### How can I prevent a user from posting a purchase order invoice if a product receipt isn't yet posted?

You can prevent a user from posting a purchase order product invoice if a purchase order product receipt hasn't yet occurred by enabling the **Receiving requirements** option for the item model group. This option is typically used in organizations that require that receipts be physically recognized in the general ledger for accruals. The **Receiving requirement** option applies to *all* inventory receipts for an item, not just to purchase orders. For example, it applies to an inventory journal that has a positive quantity and a production order report as finished journal. If your organization uses procurement categories on purchase orders, you can control the requirement for a receipt by enabling the **Receiving requirements** option for the category policy rule on the **Purchasing policies** page.

### How can I prevent a user from posting a sales order packing slip if a sales order picking list isn't yet posted?

You can prevent a user from posting a sales order packing slip or invoice if a sales order picking list hasn't yet occurred by enabling the **Picking requirements** option for the item model group. This option is typically used in organizations that perform a physical picking process in the warehouse (for example, by using the warehouse mobile device to do picking). The **Picking requirement** option applies to *all* inventory issues for an item, not just to sales orders. For example, it applies to an inventory journal that has a negative quantity and a production order picking list journal.

### How can I prevent a user from posting a sales order invoice if the sales order packing slip isn't yet posted?

You can prevent a user from posting a sales order invoice if a sales order packing slip hasn't yet occurred by enabling the **Deduction requirements** option for the item model group. This option is typically used in organizations that perform a physical packing process in the warehouse (for example, by using the Warehouse Management mobile app to do packing or by generating a document that will be included with the items that are shipped). The **Deduction requirement** option applies to *all* inventory issues for an item, not just to sales orders. For example, it applies to an inventory journal that has a negative quantity and a production order picking list journal.

### Can I prevent items that are registered from being sold?

When an item is registered in your inventory in Supply Chain Management, the quantity is physically available to be issued in the system. If items that have been registered but not yet received should *not* be available to be issued to sales orders or production orders, for example, consider using the inventory status, inventory blocking, quality orders, quarantine orders, or reservations features to manage the business process.

## Production costing

### Can I use one costing model for raw materials and a different costing model for finished goods?

Yes, you can use different costing models for each item. It isn't uncommon for manufacturers to use a periodic costing model for raw materials, and standard cost for semi-finished and finished goods.

### How can I drive overhead off machine costs?

To drive overhead off your machine costs, you must create resources and resource groups for each machine, according to your business requirements. Each resource or resource group can be assigned to cost categories to control the cost of the machine. Each cost category can be linked to a cost group, and each cost group can be used as the basis for calculating indirect costs on the costing sheet.

### How do I recognize cost that is related to energy consumption (for example, water, energy, or gas consumption) on the costing sheet?

You can generally recognize costs that are related to energy consumption in one of two ways:

- Create a line in your BOM or formula. Typically, this line is created as a service item, and you can specify the unit of measure that you're consuming in relationship to the quantity you're producing. In this way, the user can consume a different amount during the production process. You can automatically consume the items based on the value that you select in the **Flushing principle** field.
- Create an indirect cost on your costing sheet. Typically, this approach is used to allocate the total cost of your energy consumption across your production process. You can use the cost group and the absorption basis to scale the consumption based on materials or labor in your route, for example.

You should select the best option, based on your reporting, reconciliation, and operational requirements.

### Can I capture resource details in the BOM or formula?

Resource details can be captured only in a route operation. Although you can create a service item to represent a resource and assign a cost to increase the cost calculation for a finished good, we don't typically recommend this approach. Instead, we recommend that you create a simple route that has one line to track the resource costs, and configure the operation so that it's automatically consumed at either the start or the end of the production order.

### Can I view the calculation details if the cost is manually entered?

No. If you manually enter the price on the **Item price** page, the **View calculation details** and **Report calculation details** buttons aren't available. If you select the **Cost rollup by cost group** button for a cost price that is manually entered, a summarized line is shown, and all costs are rolled up to the finished good item.

### Does the system calculate variances on a production order when I manually enter the cost?

Yes, the system calculates variances when you manually enter a standard cost. However, when you manually enter a standard cost instead of calculating it, all material, route, and indirect cost consumptions in the production order are considered a substitution variance. If there are additional variances, such as consumption of extra materials or labor, they'll also be recorded as variances from the production BOM. Therefore, we strongly recommend that you always run a calculation for items that have a BOM, route, or indirect costs.

### How can I carry the variances from a subproduction order to the parent production order?

When you use a periodic costing model such as FIFO, LIFO, or weighted average, the costs from a subproduction will be recognized in the heuristic model that you've selected for the items. If you require actual costing, consider using the marking principle to indicate which subproduction is issued to a parent production order. Alternatively, consider using the **Financial inventory** option for the **Batch** or **Serial number** dimension in the tracking dimension group, for example.

### How does the flushing principle affect consumption?

The flushing principle on a BOM, formula, or route line controls the timing and technique that is used to consume the item or labor. If you select *Start*, the item or labor is automatically consumed when you start the production order. If you select *Finish*, the item or labor is automatically consumed when you report the production order as finished. If you select *Manual*, a user must manually pick materials, or record the time in a job or route card journal. BOMs and formulas also have an *Available on location* option. If you select this option, the items are automatically consumed after they are transferred to the production floor location.

### How should I run cost calculations if I have multi-level BOMs or formulas?

In general, we recommend that you start at the lowest level of your BOMs or formulas for the calculation. To make filtering easier when you mass-run cost calculations, you can use calculation groups to help segregate products. We also recommend that you run the *Recalculate BOM levels* periodic job before you start to mass-run cost calculations. Each organization should consider the mix of products and define a strategy that meets the specific needs of your product and BOM or formula structures.

## Transfer order costing

### Is there a way to allocate freight to a transfer order cost?

You can add charges to a transfer order to add costs. The charges code defines the debit and credit for the charge that you're adding. You must first create charges codes in the **Inventory management** module. To add a charge to a transfer order, select **Charges** on the transfer order line that you want to add a charge to.

## Variances

### Can I treat variances differently, based on the site or warehouse?

There's no option to configure variance accounts by site. When you use standard costing for a released product, you can select the main account that is used for standard cost variance postings on the **Posting** page. You can select to configure the accounts for one item, a group of items, or all items. You can also configure one cost group, a group of cost groups, or all cost groups.

### Can I separate variances that are the result of currency exchange rates from other types of variances?

If a variance is the result of a currency exchange rate difference between the purchase order price and the standard cost for an item, there's no way to separate the exchange rate difference from other variances.

## Reporting

### How many inventory value report configurations can I create and use?

There's no limit to the number of inventory value report configurations that you can create. You should evaluate your specific reporting requirements and create the number of configurations that you need to meet those requirements. You'll need at least one inventory value report configuration to run the report or the report storage option.

### Can I use the inventory value report to analyze the cost of an item in each warehouse?

Yes. You can enable the **View** or **Total** option for each **Warehouse** dimension in the inventory value report configuration. However, the report will show values only for dimensions where the **Financial inventory** option is enabled for the storage dimension group. For other dimensions, it will show blank columns. Learn more in [Inventory value report examples and logic](inventory-value-report-examples.md).

### How can I view the inventory quantity as of a specific date with the weighted average?

You can use the **Inventory aging** report, which includes an **Average unit cost** column that shows the value of inventory as of a specific date. Learn more in [Inventory aging report examples and logic](inventory-aging-report.md).

### How can I view which receipt transactions are settled against an issue transaction?

You can view the settlements for an inventory transaction by selecting **Settlements** or **Cost explorer** on the **Inventory** tab on the Action Pane of the **Inventory transaction** or **Inventory transaction details** page. If you select a receipt to view the issues that are related to the transaction, the cost explorer doesn't show the details. Details are shown only if you select an issue transaction.

### How does the inventory value report show items that have a positive physical quantity and a negative financial value?

The inventory value report separates the physical and financial amounts and quantities into their own columns. The values that are shown on the report are as of the date range that you selected when you ran the report. The level of summarization that is shown depends on the settings that you selected. If an item has transactions that have been physically received and financially issued, the quantities and values are summed independently. If you selected to view the detail level as transactions, rows for each receipt and issue are shown separately, and the physical and financial quantities and amounts, respectively, are shown. Learn more in [Inventory value report examples and logic](inventory-value-report-examples.md).

### What is the impact of storage and tracking dimension groups on the inventory value report?

If you enable the **Financial value** option for a dimension in a storage or tracking dimension group, you can select the **View** or **Total** option for the dimension in the inventory value report configuration. If you select the **View** or **Total** option for a dimension where the **Financial value** option isn't selected, the column will be blank in the report output. If you've enabled the **Financial value** option for a dimension in a storage or tracking dimension group, and you don't select the **View** or **Total** option on the inventory value report configuration, the system will summarize the values for the selected dimensions where they are financially tracked.

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

If you enter a default price in the **Purchase price** field on the **Released product** page, it's assumed to be in the accounting currency of the ledger for the legal entity that you're in. Likewise, if you enter a purchase price in a costing version where the **Price type** field is set to *Purchase*, the price is assumed to be in the accounting currency of your legal entity. When you create a purchase order for a vendor that has a different currency, the system will automatically convert the currency from the accounting currency amount to the transaction currency by using the exchange rate that you specify in the **Accounting currency exchange rate type** field in your ledger.

When you create a trade agreement journal, you can specify the currency that you're expressing the price in on each line. You can create trade agreements for multiple currencies, specific vendors, and many other combinations of factors. If you create a purchase order where a trade agreement exists for the currency that you've selected, the system will use the trade agreement that has the matching currency. When you post transactions such as product receipts or invoices, the amount will be converted to the ledger's accounting currency by using the accounting currency exchange rate that you specify in the ledger.

### How should I configure costs for items that are procured in multiple currencies?

Costs can't be configured in more than one currency. The cost that you specify for the item price or default costs that you enter in the **Price** field on the **Manage cost** FastTab of the **Released product** page are always expressed in the accounting currency of the ledger for the legal entity that you've selected.

If your organization uses standard costing, you should define a strategy for defining the costs when there are multiple currencies. You should also define a process for regularly updating the cost to help reduce the number of variances that are posted.

### Can I use the Profit setting on the Cost group page to calculate sales prices?

Yes, you can use the **Profit** setting on the **Cost group** page to add a percentage when sales prices are calculated by using a cost calculation. Learn more in [BOM calculations](bom-calculations.md).

## Marking

### How does marking affect periodic costing models?

If you use a periodic costing model such as FIFO, LIFO, or weighted average, and you've marked a receipt transaction against an issue transaction, the heuristic model of the item is ignored during the inventory close process. Instead, the system will use the actual cost of the receipt for the cost of the issue.

### What happens during the inventory close when I use marking?

When you mark receipts and issues, the inventory close will settle the transactions that are marked together. When marking is used to create the settlement, the **Principle** field on the **Settlement** page will be set to *Marking*. If a transaction is marked before it's physically or financially updated, the issue will use the marked receipt's cost instead of the running average cost. If the transactions are marked after the financial update, the inventory close and adjustment process will adjust the issue cost so that it matches the receipt cost.

### Can I manually mark transactions when I use standard costing or moving average?

No, you can't manually mark receipts or issues when you use standard costing or moving average. If transactions (for example, direct delivery or intercompany orders) are automatically marked, the marking record will remain and will act as a hard reservation. However, when you use standard costing or moving average, the marking of records has no effect on the cost of the items.

### How does marking affect the profit and loss statement?

When you mark an issue transaction against a receipt, the cost for the issue will match the selected receipt. When you physically and financially post the issue, the posting will affect the **Cost of goods sold, delivered** and **Cost of goods sold, invoiced** accounts that you specify in the inventory posting profile. If a transaction is marked after the physical or financial update, the *Inventory close and adjustment* process will create an adjustment that has a matching voucher that adjusts the **Cost of goods sold, invoiced** account and offsets to the account that you specify for **Cost of units, invoiced** (inventory).

### How does marking affect master planning?

The **Standard update** tab on the **Master planning parameters** page includes a field that is named **Update marking**. The option that you select there is used when you firm a planned order that is generated by master planning. The following options are available:

- *No* – The system doesn't perform any marking.
- *Standard* – The system marks receipts against issues according to the pegging. A requirement order is marked against a fulfillment order. If some quantity remains on the fulfillment, the fulfillment order isn't marked.
- *Extended* – The system marks both the requirement orders and fulfillment orders, regardless of whether any quantity remains open on the fulfillment order.

## <a name="negative-inventory"></a>Negative inventory

### When should I allow physical negative inventory?

In general, we don't recommend that you allow physical negative inventory, because it isn't possible to have less than 0 (zero) of a tangible item in your warehouse. However, the business processes of some industries and business scenarios might restrict operations that require that the inventory be allowed to go physically negative. For example, retailers might not want to prevent the sale of an item that is brought to the register, even when the system indicates that no items are available. Process manufacturers provide another example. For these manufacturers, the amount that is consumed can exceed what is recommended in the formula. Alternatively, the consumption might be estimated instead of precise, so that the consumption exceeds the amount in a specific location, such as a tank.

Whenever possible, you should evaluate your business process and try to improve it to ensure that inventory can't be negative. If you must allow negative inventory, you should have a clear business process for correcting the negative inventory, because it can adversely affect costing.

### When should I allow financial negative inventory?

In general, we recommend that most organizations allow financial negative inventory. (In most cases, purchase order invoices aren't processed before you can ship the items.) You should enable this option when you have specific business processes that require that the sales price reflect the final cost of a purchase order. For example, this requirement might apply in a make-to-order industry or in specific regions where it's dictated by law.

### What happens to the cost of my issues when the inventory is negative?

When the inventory for your item is negative, and you issue more items than you physically have, the system will use the default item price to calculate the running average if you use a periodic costing model such as FIFO, LIFO, or weighted average. If no default price is specified for the item, the system will issue the inventory with a value of 0 (zero). This behavior can cause future calculations of your running average or moving average to be inaccurate.

### Can I prevent items from being picked, packed, or sold on sales orders and production orders if there isn't enough on-hand inventory?

Yes. We recommend that you disable the **Physical negative** option for the item model group to prevent items from being picked, packed, or sold on sales orders and production orders.

### Can I prevent items from being invoiced on a sales order if no purchase orders have been invoiced for the same item?

Yes. We recommend that you disable the **Financial negative** option for the item model group to prevent items from being invoiced on a sales order if no purchase orders have been invoiced for the same item.

### How does negative inventory affect financial ratios such as gross profit margin?

When you allow your inventory to go negative, the inventory value in your balance sheet and the cost of goods sold in your profit and loss statement can be understated, especially if no default price is configured for your items. Therefore, financial reporting and ratios such as gross profit margins can be overstated, because the cost is incorrect. If you use a periodic costing model such as FIFO, LIFO, or weighted average, the value of the issues can be adjusted when you run the inventory close and adjustment process after the negative inventory quantities have been corrected. However, if you use moving average, there's no way to revalue the individual transactions.

### How should I correct negative inventory?

We recommend that you frequently monitor and correct negative inventory when your organization or business requirements dictate that you allow your inventory to go negative. You can correct the inventory values by performing a cycle count, posting an adjustment, or posting a movement journal. If you must recognize the unexpected gains in inventory in a specific general ledger account, you should plan to use a movement journal. Otherwise, when you use the cycle counting or inventory adjustment process, the system will post the inventory adjustment to the **Inventory receipt** account and offset to the **Inventory expenditure, profit** accounts that you specify on the inventory posting profile.

### Do I have to create a new item if my inventory has gone negative and I use moving average?

No. If your organization allows inventory to go physically negative, and you're using moving average as your inventory model, the system will use the fallback cost sequence that is assigned on the **Inventory and warehouse management parameters** page to determine how the cost will be assigned to your issues. In general, we recommend that you avoid allowing your inventory to go physically negative. For more information, see the other questions in the [Negative inventory](#negative-inventory) section of this article.

## Not-stocked products

### Can I post sales order picking lists for not-stocked products?

When you generate a picking list for a sales order that includes items that are in an item model group that isn't stocked, you won't see any lines for those not-stocked items. You can't use the Warehouse Management mobile app to process not-stocked items.

When you generate a packing slip for a sales order that includes items that are in an item model group that isn't stocked, set the **Quantity** field to *Picked quantity and not stocked products* to include the not-stocked items in the document generation. If you select *All*, only stocked items will be included in the packing slip.

### Should I use a not-stocked product or a category (sales category or procurement category)?

The choice between a not-stocked product and a category depends on your specific business requirements. Not-stocked products generally offer more control over default values, such as quantities and prices on purchase orders and sales orders. Therefore, not-stocked products are preferred in scenarios where the same product or service is purchased or sold more than once. Categories are useful in scenarios where the price, items, descriptions, and so on are inconsistent from transaction to transaction. Categories can also be used on any product to help classify the type of product that is being sold or purchased.

## Service items

### What is the difference between a service item and a not-stocked product?

A service item is a product type. When you create a newly released product, you can set the **Product type** field to either *Item* or *Service*. *Item* is typically selected to indicate that the item is tangible, whereas *Service* is typically selected to indicate that the item is intangible.

Any released product, regardless of whether it's an item or service product, can be stocked or not-stocked. The stocked or not-stocked setting is controlled by the item model group that you select for the released product. When you select an item group that isn't stocked, the system doesn't create inventory transactions for the related sales order or purchase order, for example.

### Can I include not-stocked items in a BOM?

No, you can't include a released product that is linked to an item model group where the **Stocked** option is disabled in a BOM or formula. It doesn't matter whether the **Product type** field is set to *Item* or *Service*. Only items that are stocked can be included on BOM or formula lines.

## Costing model–specific questions

### Which costing model should I use?

The costing models that you should select depend on your business requirements. Before you select a costing model to use in Supply Chain Management, you should validate that the model is allowed by your local regulations. We recommend that you validate your selection with a certified accountant in your region.

### Can I use more than one costing model in my organization?

Yes. There's no limit to the number of item model groups or costing models that you can select in Supply Chain Management.

### Can I use more than one costing model for each item?

No. You can select only one costing model for each released product. This behavior is controlled by the item model group. If you must use more than one costing model to report on inventory values, you should consider using the Global Inventory Accounting add-in.

### When I use manufacturing execution, which costing methodology should I use?

The costing models that you should select depend on your business requirements. There's no specific advantage or disadvantage to using any costing model when your organization also uses manufacturing execution.

### When is FEFO used?

First expired, first out (FEFO) isn't a costing methodology. Instead, it's a reservation technique that is often used in manufacturing organizations. You can enable FEFO reservations for an item model group by enabling the **FEFO date-controlled** option and then selecting a value in the **Pick criteria** field.

### Are there performance benefits to selecting one costing model over another?

In general, the costing model that you select for an item has minimal impact on the overall performance of the system. However, the amount of time that is required to run the inventory close or recalculation process might be affected by the inventory costing model that you select. For example, if you use standard cost or moving average, the inventory close process has minimal impact on the system, because it doesn't update each inventory transaction and create settlements. However, a periodic costing model such as FIFO, LIFO, or weighted average can increase the amount of time that is required to complete the inventory close process. Specifically, the close process can be longer when you enter a high number in the **Maximum number of iterations allowed per item** field or a low number in the **Minimum amount allowed** field for the *Close inventory* process.

### When should I use the Fixed receipt price option?

When you select the **Fixed receipt price** checkbox on the **Item model group** page for an item, the system will use receipt price as a standard cost for the inventory receipt. If there's a difference between the purchase price and the default item cost price that is configured for a product, the difference will be posted to the **Fixed receipt price profit** or **Fixed receipt price loss** account, and offset to the **Fixed receipt price offset** account. (All these accounts are specified on the **Posting** page.)

You should select the **Fixed receipt price** checkbox when you use a periodic costing model such as FIFO, LIFO, or weighted average, and you require that a purchase price variance be tracked in the ledger if the price of a receipt differs from the default item cost.

### Moving average

### Is moving average the same as a floating average?

The terms moving average, floating average, and running average are often used synonymously. Of these terms, moving average is the only official costing model that is available in Supply Chain Management. Although running average isn't an official costing model, it's the technique that is used when you use a periodic costing model such as FIFO, LIFO, or weighted average. The term floating average isn't used in Supply Chain Management and might have different connotations in other systems.

### How can I accommodate the difference between the product receipt price and invoice price when I use moving average?

When you use moving average, the physical cost (receipt price) is used to calculate the moving average for all issue transactions. If there's a difference between the physical cost (receipt price) and the financial cost (invoice price), the system will automatically post the difference to the main account that is specified for the **Price difference for moving average** posting type on the **Inventory** tab of the **Inventory posting profile** page.

### Where is the price difference for moving average presented in the general ledger?

When there's a price difference between the posting of a physical update and a financial update for a receipt, the difference is posted to the main account that is specified for the **Price difference for moving average** posting type on the **Inventory** tab of the **Inventory posting profile** page. Learn more in [Moving average](moving-average.md).

### When I use moving average, what happens if there's an issue before the receipt?

Typically, there might be an issue before the receipt either because you allow physical negative inventory for the item model group or because the issue is backdated. Learn more in the [Negative inventory](#negative-inventory) section of this article.

If you're backdating transactions, we recommend that you carefully consider your business process and operations to determine whether there's a way to avoid this scenario. If you backdate a transaction for an item that uses moving average, the system will assign the current moving average to the transaction. Later issues aren't adjusted. For more information about moving average with backdated transactions, see [Moving average](moving-average.md).

### Standard costing

### What is the difference between standard costing and fixed receipt price?

Standard costing requires that you define an item price and activate the cost in a costing version. That cost is used for all receipts and issues. Variances for the receipts to inventory are recorded in the general ledger by using the standard cost variance accounts that you specify on the **Standard cost** tab of the **Inventory posting profile** page.

However, when you use fixed receipt price, only the cost for receipts is fixed, and the system uses the cost that you specify on the **Manage costs** FastTab of the **Released product** page. Differences between the default cost and the purchase order price will cause the purchase price variance to be posted to the fixed receipt price profit and loss accounts. Issues don't use fixed receipt price. Instead, issues will be valued at the running average at the time of posting (unless you use marking), and they'll be revalued to the heuristic model that you select when you run the inventory close.

### Can I use FEFO reservations with standard costing?

Yes, you can use FEFO reservations on an item model group when you select standard costing. FEFO reservations control the reservation logic that is used for the physical handling of the items, whereas standard costing controls the physical and financial cost for an item.

### Can I upload pending prices?

Yes, you can use the Excel add-in or the Data Management Framework to upload a pending price. We recommend that you use the following entities:

- Pending item prices (V2)
- Pending route cost category unit costs
- Costing sheet node calculation factors (V2)

### How often can I update the standard cost for an item?

There's no limit on the frequency that you can activate a new standard cost at. If you activate a new cost for an item on the same day that the last cost was activated, the system will use the most recent activated cost on new transactions or updates (such as updates to existing transactions).

### Can I deactivate or delete an activated cost?

No, you can't deactivate or delete an activated cost. If you've incorrectly activated a cost, you can activate a new cost that has the correct cost.

### Are calculation groups used with standard costing?

Calculation groups can be used with any item, regardless of the item model group that you choose. The calculation groups are used during the cost rollup or cost calculation process to determine the settings that should be used for the items that you're running the calculation for. For more information about calculation groups, see [BOM calculations groups](bom-calculation-groups.md).

### When should I use a planned costing version?

Costing versions can have a type of *Standard cost* or *Planned cost*. The *Standard cost* type is used for the costs that are active in the system and will be posted in transactions. The *Planned cost* type is used for running simulations on costs and doesn't affect the cost of transactions.

### Can the total cost from one entity be transferred to another entity as the selling cost?

There's no automated way to copy costs from one company to another. Additionally, there's no automated way to copy costs from a purchase price to a sales price. If your organization must complete one of these tasks, consider whether you can use the Data Management Framework to export the data out of your costing version and upload into a different company, either as a sales price in the costing version or as a trade agreement. Manual manipulation of the files might be required.

### What is the best way to copy planned costs to a standard costing version?

You can use the **Copy** button on the **Costing versions** page to copy item prices, cost category prices, or indirect costs from one costing version to another.
