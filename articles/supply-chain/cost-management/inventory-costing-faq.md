---
title: Inventory costing frequently asked questions
description: This topic outlines frequently asked questions about inventory costing in Dynamics 365 Supply Chain Management.
author: rachel-profitt
ms.date: 05/03/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: raprofit
ms.search.validFrom: 2022-05-03
ms.dyn365.ops.version: 10.0.27
---

# Inventory costing frequently asked questions

[!include [banner](../includes/banner.md)]

This topic outlines frequently asked questions about inventory costing in Dynamics 365 Supply Chain Management.

## Inventory close, adjustments, and recalculation

**Is the inventory close required?**

Yes, if you plan to use the inventory archiving feature, the inventory close is required. If you don't plan to use the inventory archiving feature, we strongly recommend that you run the inventory close regardless of the costing model(s) that you use.

**How frequently should the inventory close be run?**

The inventory close should be run at least once per ledger period. For example, if your ledger is set to a calendar month-based fiscal calendar, you should run the close once per month.

**Is inventory recalculation required?**

No, the inventory recalculation isn't required. If you use a periodic costing model such as FIFO, LIFO, or weighted average, you should consider carefully if you run the inventory recalculation. Running the recalculation can provide more accurate costing in the heuristic model(s) you've selected.

**How frequently should the inventory recalculation be run?**

If you're planning to run the inventory recalculation, we recommend that you consider running it daily as a batch process. If your organization doesn't require frequent reporting of the inventory values for periodic costing models, you can consider running this calculation less frequently.

**When should I use the on-hand inventory adjustment on the Closing and adjustments page?**

The on-hand inventory adjustment can only be run after an inventory close is completed. It's typically run for the date after the last close. The on-hand adjustment can only adjust inventory that is still on-hand as of the date you run the adjustment.

**When should I use the inventory transaction adjustment on the Closing and adjustments page?**

You should use the inventory transaction adjustment before you run an inventory close. This process is typically used to correct an incorrect receipt. You can't post an inventory transaction adjustment after an inventory close is run and the transaction is settled.

**Are purchase order returns treated like other issues during inventory close?**

Yes, a purchase order receipt is an issue that is settled to a receipt in the heuristic model that you select for the item. If you're using a periodic costing model, you can use marking to override the heuristic cost.

**What happens to sales order returns during inventory close?**

When you run the inventory close, a sales order return is treated as a receipt into inventory and issues are settled against the inventory based on the heuristic model you select for the item.

**What cost price is used on a sales order return?**

When you create a return related to sales order, the **Unit price** field is copied from the original sales order, and the **Return cost price** field on the return is populated with the adjusted cost price from the original inventory transaction for the sales order line that is being returned. If the related inventory transaction isn't **Value open** = *No*, the inventory close can cause updates to the issue cost on the original sales order. The **Return cost price** field isn't updated in this scenario. However, when you post a return order packing slip, the system will check the cost price and use the update cost on the return inventory transaction.

For a return on standard cost item that is related to sales order, the system will use the standard cost from the time of the original sales order, even if a new standard cost is active for the item.

When you create a return that isn't related to a sales order, the **Return cost price** is populated from the active **Item price** that you have for the item in the **Site** you're creating the return order for. If you don't have an active cost price in a costing version for the item, the value will be zero. If you leave the value as zero, a warning will be presented that the **Return lot ID** or **Return cost price** aren't specified.

**What is the expected performance of the inventory close?**

Many factors can affect the performance of the inventory close, including the total number of items, the total number of transactions in the period, the inventory model(s) you use, and the number of batch helpers you configure in the inventory and warehouse management parameters. You can expect that the closing may take as little as a few minutes to as many as several hours to complete. There's no specific guidance on the length of time the close should take to run. You should define your nonfunctional business requirements for performance of the inventory close and work closely with your partner to define the schedule for running the inventory close process. If you're experiencing unexpectedly deficient performance of the inventory closing process, you should open a support ticket.

## Costing sheet and indirect costs

**Which costing models support the costing sheet?**

While the costing sheet is most typically used in organizations that use standard costing, you can use the costing sheet with any costing model available in Supply Chain Management.

**Can I have multiple costing sheets for various parts of my organization?**

You can only have one costing sheet per legal entity.

**Can I have different costing sheets for each site?**

You can't have a different costing sheet for each site. You can only create one costing sheet for each legal entity. You can, however, configure total nodes, cost groups, or indirect cost nodes per site. This process would be manual, and you would need to maintain the hierarchy and item assignments into the costing sheet when you have organizational or operational changes. If a single item is produced or purchased into more than one site, there's no mechanism to treat the item differently on the costing sheet for each site. Note also that all indirect cost codes have a rate or surcharge defined in your costing version. The costs that you define are always site specific.

**Can I deactivate and activate versions of the costing sheet?**

While the costing sheet doesn't keep a detailed version history, you can make changes to the costing sheet and when you're ready, save and validate the costing sheet. There's no mechanism to go back to an older version of a costing sheet or see the changes that are made to the costing sheet. If you start changes and don't want the changes to be effective, you can close the screen without saving and validating. You'll be prompted to discard the changes.

**Can I create indirect costs for each item?**

You can create indirect cost codes in your costing sheet that are of **Node type** *Surcharge*, *Rate*, or *Output unit based* and define the rate or surcharge to be specific to an item number. You do this by creating a new row in either the **Rate** FastTab or **Surcharge** FastTab. In the **Valid for** field, you can select Table, and in the **Relation** field, you can select the specific item number.

**Can I create an indirect cost that isn't related to a specific item?**

Yes, you can create an indirect cost code with the **Node type** set to *Output unit based*. The **Subtype** field can be set to the *Quantity*, *Weight*, or *Volume* of the item you're producing. The rate that you specify on the **Rate** FastTab will be applied to the subtype you selected. For example, if you set **Subtype** to *Quantity* and **Rate** to *1.00 USD*, then you'll create a production or batch order for a quantity of 10, the indirect cost added to the finished good is 10.00 USD.

**Can I use the costing sheet to split my production costs by hours and materials?**

Yes, you can create **Total** nodes in your costing sheet to separate the costs by any grouping you choose. For example, you can create one **Total** node called Hours, and another **Total** row called Materials. Under each total node, you would add each cost group that related to your hours and materials respectively.

## Dimension groups

**Can I manage cost at a batch or serial number level?**

Yes, if you're using a periodic costing model such as FIFO, LIFO, LIFO Date, weighted average, or weighted average date, you can select the **Financial inventory** option for **Batch** or **Serial number** on the **Tracking dimension group** to track costs at the detailed level.

**Can I manage costs at a location level?**

No, you can't select the **Financial inventory** option for the **Location** dimension in the **Storage dimension group**. If your organization needs to track costs at a more granular level, consider if you can create virtual warehouses and select the option for **Financial inventory** on the **Warehouse** dimension in your **Storage dimension group**.

**Should I enable the Use warehouse management processes option on the Storage dimension group?**

Yes, if you think that you might want to use the advanced warehouse management features in the future, you should enable this option. Once you save the **Storage dimension group**, you can no longer make any changes to the **Use warehouse management processes** option on the **Storage dimension group**. If you decide to use warehouse management processes later, you'll be required to create a new warehouse with the option enabled. There's no automated process to move all the inventory from one warehouse to another warehouse or to copy related configurations to a new warehouse.

**Can I enable the Use warehouse management processes on the Storage dimension group even if I am not planning to use advanced warehousing?**

Yes, even if you don't plan to use the advanced warehouse management options, you can enable the **Use warehouse management processes** option on the **Storage dimension group**. You'll need to complete the minimum configuration (such as reservation hierarchies, unit sequence groups, and so on) to create and process transactions. However, the settings for advanced warehousing are generally ignored when you manually process picking lists, packing slips, and product receipts (for example, on the sales order and purchase order pages).

**When should I enable the Physical inventory option on a storage or tracking dimension group?**

You should select the **Physical inventory** option on storage and tracking dimension groups when you need to keep detailed inventory records by that dimension. Typically, any dimension that is active, will also be tracked physically. This means that any receipt, issue, or movement of the inventory will be tracked at the dimension you've selected. If a dimension isn't mandatory, for example the license plate, you can select the **Blank receipt allowed** and **Blank issue allowed** options to allow users to receive, issue, or move inventory without the dimension specified.

**When should I enable the Financial inventory option on a storage or tracking dimension group?**

You should select **Financial inventory** option on a storage and tracking dimension groups when you need to keep detailed financial records by that dimension. The **Site** dimensions are always tracked financially, while other dimensions are optional for tracking financially. If you use a periodic costing model such as FIFO, LIFO, or weighted average, selecting the financial inventory option for a dimension indicates that you'll only make settlements where the receipt and issue have the same dimension values. For example, if you select **Financial inventory** for the **Warehouse** dimension, then you'll have a different cost in each warehouse and receipts and issues from different warehouses can't be settled.

**Can I make changes to a product, storage, or tracking dimension group after transactions exist?**

The only changes you can make to an item model group after you create it are to the **Coverage plan by dimension**, **For purchase prices**, and **For sales prices** fields where the **Active** check box is selected on a dimension in the item model group. Any other changes including selecting or deselecting the **Active**, **Blank issue allowed**, **Blank receipt allowed**, **Physical inventory**, and **Financial inventory** options aren't allowed.

**Can I change the product, storage, or tracking dimension group on a released product?**

If the on-hand inventory for a product is zero and all the inventory transactions are **Value open** = *No*, you can change the storage and tracking dimension groups on the released production page. You can't change the **Product dimension group** after the record is created.

## Item model groups

**When should I select the option for Stocked product?**

You should select the **Stocked product** option for any item that will be tracked in your inventory. When this option is selected, detailed inventory transactions are kept tracking the receipt and issue of the item. This option is typically selected for any tangible item that you keep in your warehouse, for example. You should also select this option if you plan to add a non-tangible item such as a service item into your BOM or formulas. When you don't select the **Stocked product** option, no inventory transactions are tracked in the inventory sub ledger and the cost of the items are typically expensed into your general ledger. This option is often used for shop supplies or services, for example that aren't included in your BOMs or Formulas.

**When should I select the option for post physical inventory?**

The **Post physical inventory** option is typically selected when the **Stocked product** option is selected. When you select this option, the system will track the physical update to the item on the inventory transaction. This option is used in coordination with parameters in Accounts payable, Accounts receivable, and Production control that indicate the physical update should create a voucher. You'll typically select this option when you want to update the ledger when you physically update the inventory. If Supply Chain Management isn't your system of record for financials, you may choose to disable this option.

**When should I select the option for post financial inventory?**

The **Post financial inventory** option is typically selected when the **Stocked product** option is selected. This option is used in coordination with parameters in Accounts payable, Accounts receivable, and Production control that indicate the financial update should create a voucher. You'll typically select this option when you want to update the ledger when you financially update the inventory (such as invoicing sales orders and purchase orders or ending a production order. If Supply Chain Management isn't your system of record for financials, you may choose to disable this option.

**When should I select the option for Post to Deferred Revenue Account on Sales Delivery?**

The **Post to Deferred Revenue Account on Sales Delivery** is used to indicate if you want to recognize revenue in the general ledger when you post a packing slip for a sales order. This option is typically used when you have a long delay between the packing slip and invoice on a sales order or when it isn't possible to invoice all sales orders in the period. It's common to leave this option blank if you post your sales order invoices immediately after you post the packing slip, which avoids generating extra general ledger postings that will immediately be reversed when you invoice a sales order.

**When should I select the option for Accrue liability on product receipt?**

In most organizations, you'll want to select the **Accrue liability on product receipt** option for all item model groups whether you have a stocked product or a not-stocked product. This option is used to post an accrual to the general ledger based on product receipt price. Because there's typically a delay between posting the product receipt for a purchase order and posting the invoice, most organization need to recognize the liability in the balance sheet to be compliant with local regulations such as Generally Accepted Accounting Practices (GAAP). If Supply Chain Management isn't your system of record for financials, you may choose to clear this option. If your organization uses **Procurement categories** on purchase orders, you can control the accrual requirement in the **Purchasing policies** page on the **Category policy rule** by selecting the **Accrue purchase expense on receipt** option.

**How can I prevent a user from posting a purchase order product receipt if a receipt registration isn't yet posted?**

You can prevent a user from posting a purchase order product receipt if a purchase order registration hasn't yet occurred by selecting the **Registration requirements** option on the **Item model group**. This option is typically used in organizations that use a two-step receiving process or in scenarios when you need to register a batch or serial number, for example, on the items you're receiving. The **Registration requirement** option applies to all inventory receipts for an item and not just purchase orders. For example, an inventory journal that has a positive quantity, or a production order report as finished journal.

**How can I prevent a user from posting a purchase order invoice if a product receipt isn't yet posted?**

You can prevent a user from posting a purchase order product invoice if a purchase order product receipt hasn't yet occurred by selecting the **Receiving requirements** option on the **Item model group**. This option is typically used in organizations that require receipts to be physically recognized in the general ledger for accruals. The **Receiving requirement** option applies to all inventory receipts for an item and not just purchase orders. For example, an inventory journal that has a positive quantity, or a production order report as finished journal. If your organization uses **Procurement categories** on purchase orders, you can control the requirement of a receipt in the **Purchasing policies** page on the **Category policy rule** by selecting the **Receiving requirements** option.

**How can I prevent a user from posting a sales order packing slip if a sales order picking list isn't yet posted?**

You can prevent a user from posting a sales order packing slip or invoice if a sales order picking list hasn't yet occurred by selecting the **Picking requirements** option on the **Item model group**. This option is typically used in organizations that perform a physical picking process in the warehouse, for example picking with the warehouse mobile device. It's important to note that the **Picking requirement** option applies to all inventory issues for an item and not just sales orders. For example, an inventory journal that has a negative quantity, or a production order picking list journal.

**How can I prevent a user from posting a sales order invoice if the sales order packing slip isn't yet posted?**

You can prevent a user from posting a sales order invoice if a sales order packing slip hasn't yet occurred by selecting the **Deduction requirements** option on the **Item model group**. This option is typically used in organizations that perform a physical packing process in the warehouse, for example packing with the Warehouse Management mobile app or generating a document to include with the items being shipped. The **Deduction requirement** option applies to all inventory issues for an item and not just sales orders. For example, an inventory journal that has a negative quantity, or a production order picking list journal.

**Can I prevent items that are registered from being sold?**

When an item is registered in your inventory in Supply Chain Management, the quantity is physically available for issuing in the system. If you require items that are registered but not yet received to *not* be available for issuing to sales orders or production orders (for example), consider using the inventory status, inventory blocking, quality orders, quarantine orders, or reservations features to manage the business process.

## Production costing

**Can I use one costing model for raw materials, and a different costing model for finished goods?**

Yes, you can use different costing models for each item. It isn't uncommon for manufacturers to use a periodic costing model for raw materials, and standard cost for semi-finished and finished goods.

**How can you drive overheads off machine costs?**

To drive overheads off your machine costs, you'll need to create resources groups and resources for each machine according to your business requirements. Each resource or resource group can be assigned to **Cost categories** to control the cost of the machine. Each **Cost category** can be linked to a **Cost group**, and each **Cost group** can be used for the basis of calculating indirect costs in the **Costing sheet**.

**How do I recognize cost related to energy consumption such as consuming water, energy, or gas on the costing sheet?**

You can generally recognize costs related to energy consumption in one of two ways:

1. Create a line in your **BOM** or **Formula**. Typically, this is done as a service item, and you can specify the unit of measure that you're consuming in relationship to the quantity you're producing. This allows the user to consume a different amount during the production process. You can automatically consume the items based on the value you select in the **Flushing principle**.

2. Create an indirect cost in your **Costing sheet**. Typically, this is done to allocate the total cost of your energy consumption across your production process. You can use the **Cost group** and the **Absorption basis** to scale the consumption based on materials or labor in your route, for example.

You should select the best option based on your reporting, reconciliation, and operational requirements.

**Can I capture resource details in the BOM or Formula?**

Resource details can only be captured in a route operation. While you can create a service item to represent a resource and assign a cost to increase the cost calculation for a finished good, we don't typically recommend this approach. It would instead be recommended to create a simple route with one line to track the resource costs and configure the operation to be automatically consumed at either the start or the finish of the production order.

**Can you view the calculation details if the cost is entered manually?**

No, if you manually enter the price in the **Item price** page, the **View calculation details** and **Report calculation details** buttons aren't available. If you select the **Cost rollup by cost group** button for a cost price that is entered manually, you'll receive a summarized line and all costs are rolled up to the finished good item.

**Does the system calculate variances on a production order when you enter the cost manually?**

Yes, the system calculates variances when you manually enter a standard cost. However, it's important to note that all material, route, and indirect cost consumption in the production order is considered a substitution variance when you manually enter the standard cost instead calculating the standard cost. If there are additional variances such as consumption of extra materials or labor, these will also be recorded as variances from the production BOM. For this reason, it's strongly recommended to always run a calculation for items that have a BOM, Route, or Indirect costs.

**How can I carry the variances from a sub production order to the parent production order?**

When you use a periodic costing model such as FIFO, LIFO, or weighted average, the costs from a subproduction will be recognized in the heuristic model you have selected for the items. If you need actual costing, consider using the **Marking** principle to indicate which subproduction is issued to a parent production order, or you can consider using the **Financial inventory** option on the **Tracking dimension group** for **Batch** or **Serial number**, for example.

**How does the flushing principle affect consumption?**

The **Flushing principle** on a BOM, Formula, or Route line are used to control the timing and technique that is used for the consumption of the item or labor. When you select **Start**, the item or labor is consumed automatically when you start the production order. When you select **Finish**, the item or labor is consumed automatically when you report as finished the production order. When you select **Manual**, a user must manually pick materials, or record the time in a job or route card journal. BOM and Formulas also have another option available for **Available on location** which means the items will be consumed automatically once they are transferred to the production floor location.

**How should you run cost calculations if you have multi-level BOMs or Formulas?**

In general, it's recommended to start at the lowest level of your BOM or Formulas for the calculation. You can use Calculation groups to help segregate products for ease of filtering when you mass run cost calculations. It's also recommended to ensure that you run the Recalculate BOM levels periodic job before you start to run cost calculations in mass. Each organization should consider the mix of products and define a strategy that meets the specific needs of your product and BOM or Formula structures.

## Transfer order costing

**Is there a way to allocate freight to a transfer order cost?**

You can add charges to a transfer order to add costs. The **Charges code** defines the debit and credit for the charge you are adding. You must first create **Charges codes** in the **Inventory management** module. To add a charge to a **Transfer order**, select the **Charges** button on the **Transfer order line** you want to add a charge to.

## Variances

**Can you treat variances differently based on site or warehouse?**

There's no option to configure the variance accounts by site. When you use standard costing for a released product, you can select the **Main account** to be used for **Standard cost variance** posting in the **Posting** page. You can select to configure the accounts for one item, a group of items or all items as well as one cost group, a group of cost groups, or all cost groups.

**Can you delineate variances from currency exchange rates to other types of variances?**

If a variance is a result from a currency exchange rate difference between the purchase order price and the standard cost for an item, there's no way to separate the exchange rate differences from other variances.

## Reporting

**How many inventory value report configurations can you create and use?**

There's no limit to the number of inventory value report configurations you can create. You should evaluate your specific reporting requirements and create the number of configurations needed to meet those business requirements. You'll need at least one inventory value report configuration to run the report or the report storage option.

**Can you use the inventory value report to analyze the cost of an item in each warehouse?**

Yes, you can select the option for **View** or **Total** on the **Warehouse dimension** in the **Inventory value report** configuration. However, it's critical to note that only dimensions where the **Financial inventory** option is enabled on the **Storage dimension group** will show values on the report. Other dimensions will show only blank columns. For more information, see [Inventory value report examples and logic](inventory-value-report-examples.md).

**How can I view the inventory quantity as of a specific date with the weighted average?**

You can use the **Inventory aging report** which includes an **Average unit cost** column to see the value of inventory as of a specific date. For more information, see [Inventory aging report examples and logic](inventory-aging-report.md).

**How can you view which receipt transactions are settled against an issue transaction?**

You can view the settlements for an inventory transaction by selecting **Settlements** or **Cost explorer** in the **Inventory** tab of the Action Pane on the **Inventory transaction** or **Inventory transaction details** page. If you select a receipt to view the issues related to the transaction, the Cost explorer doesn't show the details, only if you select an issue transaction.

**How does the inventory value report display items with a positive physical quantity and a negative financial value?**

The inventory value report separates the physical and financial amounts and quantities into their own columns. The values displayed on the report are as of the date range you have selected when running the report. The level of summarization displayed is dependent on the settings you choose. If an item has transactions that have been physically received and financially issued, you'll see the quantities and values summed independently. If you select to view the detail level as Transactions, you'll see the rows for each receipt and issue separately with the physical and financial quantities and amounts respectively. For more information, see [Inventory value report examples and logic](inventory-value-report-examples.md).

**What is the impact of storage and tracking dimension groups on the inventory value report?**

If you select the **Financial value** option for a dimension on **Storage** or **Tracking dimension group**, you can select to **View** the dimension or the **Total** for the dimension in the **Inventory value report** configuration. If you select the **View** or **Total** option for a dimension where the **Financial value** option for a dimension isn't selected, the column will display with blank values on the report output. If you have enabled the **Financial value** option for a dimension on a **Storage** or **Tracking dimension group**, and you don't select the **View** or **Total** option on the **Inventory value report** configuration, the system will summarize the values for the dimensions you have selected where they are financially tracked.

**Can you customize the Power BI embedded reports for costing?**

Yes, users with the correct security can make updates to the report design canvas for any Power BI embedded report in Supply Chain Management. For more information, see [Customize embedded reports in analytical workspaces](../../fin-ops-core/dev-itpro/analytics/customize-analytical-workspace.md).

**Where can you view the variance analysis statement?**

You can access the **Variance analysis statement** by navigating to **Cost management &gt; Inquiries and reports &gt; Inventory accounting – analysis reports** or **Cost management &gt; Inquiries and reports &gt; Manufacturing accounting – analysis reports**. Both options open the same report with the same behavior.

## Item prices and default costs

**Can I maintain the cost for each product variant?**

Yes, you can select the **Use cost price by variant** option on the **Manage cost** FastTab of the **Released product** page to enable pricing by product variant. (This option is only available for product masters.) Then you can use the **Dimension display** button in the **Item price** page (accessed from either the **Costing version** page or the **Released product** page) to select if you want to display **Configuration**, **Size**, **Color**, or **Style**. To save the setup and persist the selected dimensions each time you open the page, select the **Save setup** option, and then select **OK**. You can only enter the dimensions for items that have the dimensions active in their **Product dimension group**.

**Can I maintain the cost for each warehouse?**

No, you can't maintain the **Item price** by warehouse. However, you can maintain trade agreements for purchase prices or sales prices by warehouse. To do this you must first select the **For purchase prices** or **For sales prices** option for the dimension in the **Storage dimension group** page. Then when you create the Trade agreement journal, and open the Lines the dimensions you can select **Inventory \> Display dimensions** to choose which dimension should be displayed in the grid. To save the setup and persist the selected dimensions each time you open the page, select the **Save setup** option, and then select **OK**. You can only enter the dimensions for items that have the dimensions active in their **Product dimension group**.

**What are the price charges?**

Price charges are a way to add a fixed amount to the unit price of the Item price or Trade agreement. When you enter an amount in the **Price charges** field, you can also enter a **Charges quantity**. The price charges are amortized over the charges quantity that you specify. You can also select the **Incl. in unit price** option to include the **Price charges** in the unit price for the item. This option is always selected for a standard cost.

**How should you configure prices for items that are procured in multiple currencies?**

If you enter a default price into the **Purchase price** field on the **Released product**, this amount is assumed to be the **Accounting currency** on the **Ledger** of the **Legal entity** you are in. Likewise, if you enter a purchase price into a **Costing version** with the **Price type** of Purchase, the price is assumed to be in the **Accounting currency** of your **Legal entity**. When you create a purchase order for a vendor with a different currency, the system will automatically convert the currency from the **Accounting currency** amount to the **Transaction currency** by using the exchange rate that you specify in your **Ledger** on the **Accounting currency exchange rate type** field.

When you create a **Trade agreement journal**, you can specify the currency you are expressing the price in on each line. You can create trade agreements for multiple currencies, specific vendors, and many other combinations of factors. If you create a purchase order where a trade agreement exists for the currency you have selected, the system will use the trade agreement with the matching currency. The amount will be converted to the ledger's **Accounting currency** when you post transactions such as **Product receipts** or **Invoices** by using the **Accounting currency exchange rate** that you specify on the **Ledger**.

**How should you configure costs for items that are procured in multiple currencies?**

Costs can't be configured in more than one currency. The cost that you specify on the Item price or default costs that you enter in the **Price** field on the **Manage cost** FastTab of the **Released product** page are always expressed in the **Accounting currency** of the **Ledger** for the **Legal entity** you have selected.

If your organization uses Standard costing, you should define a strategy for defining the costs when there are multiple currencies, and define a process for regularly updating the cost to reduce the number of variances that are posted.

**Can you use the Profit setting on the Cost group to calculate sales prices?**

Yes, you can use the Profit setting on the Cost group page to add a percentage when calculating sales prices by using a Cost calculation. For more information, see [BOM calculations](bom-calculations.md).

## Marking

**How does marking affect periodic costing models?**

When you use a periodic costing model such as FIFO, LIFO, or weighted average, and you have marked a receipt transaction against an issue transaction, the heuristic model of the item is ignored during the inventory closing process. Instead, the system will use the actual cost of the receipt for the cost of the issue.

**What happens during inventory close when I use marking?**

When you mark receipts and issues, the inventory close will settle the transactions that are marked together. The **Principle** field on the **Settlement** page will indicate **Marking** when marking is used to create the settlement. If a transaction is marked before it's physically or financially updated, the issue will use the marked receipt's cost instead of the running average cost. If the transactions are marked after the financial update, the inventory close and adjustment process will adjust the issue cost to match the receipt cost.

**Can you manually mark transactions when you use standard costing or moving average?**

No, you can't manually mark receipts or issues when you use standard costing or moving average. If transactions are marked automatically, for example direct delivery or intercompany orders, the marking record will remain which acts as a hard reservation. However, when you use standard costing or moving average, marking of records has no effect on the cost of the items.

**How does marking affect the profit and loss statement?**

When you mark an issue transaction against a receipt, the cost for the issue will match the receipt selected. When you physically and financially post the issue, this will affect the **Cost of goods sold, delivered** and **Cost of goods sold, invoiced** accounts that you specify in the inventory posting profile. If a transaction is marked after the physical or financial update, the **Inventory close and adjustment** process will create an adjustment with a matching voucher that adjusts the **Cost of goods sold, invoiced** account and offsets to the account you specify for **Cost of units, invoiced** (inventory).

**How does marking affect master planning?**

You can optionally select an option in the Master planning parameters pate on the Standard update tab for the Update marking field. The option you select here is used when you firm a planned order that is generated by master planning. When you select the option for No, the system doesn't perform any marking. If you select Standard, the system will mark receipts against issues according to the pegging. A requirement order is marked against a fulfillment order. If some quantity remains on the fulfillment, the fulfillment order isn't marked. The final option you can select is Extended. This option marks both the requirement orders and fulfillment orders regardless of whether any quantity remains open on the fulfillment order.

## Negative inventory

**When should I allow physical negative inventory?**

In general, it not recommended to allow physical negative inventory. (It isn't possible to have less than zero of a tangible item in your warehouse). However, some industries and business scenarios may have business processes that restrict operations that require the system to allow the inventory to go negative physically. For example, retailers may not want to prevent the sale of an item at the point of sale if an item is brought to the register even if the system identifies that no items are available. Another example is process manufacturers who can consume more than what is recommended in the formula or the consumption is estimated rather than precise that causes the consumption to exceed the amount in a specific location such as a tank. When possible, you should evaluate your business process and try to make improvements to the business process to ensure that inventory can't be negative. If you need to allow negative inventory, you should have a clear business process for correcting the negative inventory as it can have a negative impact on costing.

**When should I allow financial negative inventory?**

In general, it's recommended that most organizations allow financial negative inventory. (In most cases purchase order invoices aren't processed before you can ship the items.) You should select this option when you have specific business processes that require the final cost of the purchase order to be reflected in the sales price. This may be required, for example, in a make-to-order industry or in certain regions where it's required by law.

**What happens to the cost of my issues when the inventory is negative?**

When the inventory for your item is negative, and you issue more items than what you physically have, the system will use the default item price for calculating the running average when you use a periodic costing model such as FIFO, LIFO, or weighted average. If no default price is specified for the item, the system will issue the inventory with a value of zero. This can cause future calculations of your running average or moving average to be inaccurate.

**Can I prevent items from being picked, packed, or sold on sales orders and production orders if there isn't enough on-hand inventory?**

Yes, it's recommended to ensure that the **Physical negative** option on the **Item model group** is NOT selected to prevent items from being picked, packed, or sold on sales orders and production orders.

**Can I prevent items from being invoiced on a sales order if there are no purchase orders invoiced for the same item?**

Yes, when you have this requirement, it's recommended that you clear the **Financial negative** option on the **Item model group**.

**How does negative inventory impact financial ratios such as gross profit margin?**

When you allow your inventory to go negative, the inventory value in your balance sheet and cost of goods sold in your profit and loss statement can be understated. This is especially true if you don't have a default price configured for your items. Therefore, financial reporting and ratios such as gross profit margins can be overstated because the cost is incorrect. If you use a periodic costing model such as FIFO, LIFO, or weighted average the value of the issues can be adjusted when you run the inventory close and adjustment process after the negative inventory quantities have been corrected. However, if you use moving average, there's no way to revalue the individual transactions.

**How should I correct negative inventory?**

It's recommended that you monitor and correct negative inventory on a frequent basis when your organization or business requirements dictate that you allow your inventory goes negative. You can correct the inventory values by performing a cycle count, posting an adjustment, or movement journal. If you need to recognize the unexpected gains in inventory into a specific general ledger account, you should plan to use the movement journal. Otherwise, when you use the cycle counting process or inventory adjustment process the system will post the adjustment to inventory into the Inventory receipt and offset to the Inventory expenditure, profit accounts that you specify on the Inventory posting profile.

**Do I need to create a new item when my inventory has gone negative and I use moving average?**

No, if your organization allows the inventory to go physically negative and you are using moving average as your inventory model, the system will use the Fallback cost sequence in the Inventory and warehouse management parameters to determine how the cost will be assigned to your issues. In general, we recommend that you avoid allowing your inventory to go physically negative. For more information, see the [Negative inventory](#negative-inventory) section of this topic.

## Not-Stocked products

**Can I post sales order picking lists for not-stocked products?**

When you generate a picking list for a sales order that includes items that are in an item model group that isn't stocked, you don't see any lines for those not-stocked items. You can't use the warehouse mobile device to process not-stocked items by using the warehouse mobile device.

When you generate a packing slip for a sales order that includes items that are in an item model group that isn't stocked, you can set the **Quantity** parameter to **Picked quantity and not stocked products** to include the not-stocked items in the document generation. If you select **All** only stocked items will be included in the packing slip.

**Should I use a not-stocked product or a category (sales category or procurement category)?**

The choice to use a not-stocked product or a category depends on your specific business requirements. Not-stocked products generally offer more control over default values such as quantities and prices on purchase orders and sales orders. Therefore, not-stocked products are preferred in scenarios where the same product or service is purchased or sold more than one. Categories are useful in scenarios where the price, items, descriptions, and so on are inconsistent from transaction to transaction. Categories can also be used on any product to help classify the type of product that is being sold or purchases.

## Service items

**What is the difference between a Service item and a Not-Stocked product?**

A service item is a product type. When you create a newly released product, you can select the product type is either Item or Service. Item is typically used to indicate the item is tangible, while Service it typically used to indicate the item isn't tangible.

Any released product, whether it's an Item or Service type can be stocked or not-stocked. The stocked or not-stocked setting is controlled by the Item model group that you select for the released product. When you select an item group that isn't stocked, the system doesn't create inventory transactions for the related sales order or purchase order, for example.

**Can you include not-stocked items in a BOM?**

No, you can't include a released product that is linked to an Item model group where the Stocked option isn't selected in a BOM or Formula. It doesn't matter if you mark the Product type as Item or Service. Only items that are Stocked can be included in the BOM or Formula lines.

## Costing model specific questions

**Which costing model should I use?**

The costing model(s) you should select are dependent on your business requirements. Before selecting a costing model to use in Supply Chain Management, you should validate that the model is allowed by your local regulations. We recommend that you validate your selection with a certified account in your region.

**Can I use more than one costing model in my organization?**

Yes, there's no limit to the number of item model groups or costing models you select in Supply Chain Management.

**Can I use more than one costing model on each item?**

No, you can only select one costing model for each released product. This is controlled by the item model group. If you have requirements to report on inventory values using more than one costing model, you should consider using the Global Inventory Accounting add-in.

**When I use Manufacturing execution, which costing methodology should I use?**

The costing model(s) you should select are dependent on your business requirements. There's no specific advantage or disadvantage to using any costing model when your organization also uses manufacturing execution.

**When is FEFO used?**

FEFO or first expired, first out isn't a costing methodology. Instead, it's a reservation technique that is commonly used in manufacturing organizations. You can enable FEFO reservations on the Item model group by selecting the **FEFO date-controlled** option in the **Reservation** group, and then selecting the **Pick criteria** and **Validate batch expiration on** parameters.

**Are there performance benefits to selecting one costing model over another?**

In general, the costing model you select for an item has a minimal impact on the overall performance of the system. However, the amount of time that is required to run the inventory close or recalculation process may be affected by the inventory costing model you select. For example, if you use Standard cost or Moving average, the inventory close process has minimal impact on the system as it doesn't update each inventory transaction and create settlements. While using a periodic costing model such as FIFO, LIFO, or weighted average can increase the amount of time the inventory closing takes to complete. Specifically, the close process can be longer when you enter a high number for the **Maximum number of iterations allowed per item** or a low number for the **Minimum amount allowed** parameter on the **Close inventory** process.

**When should I use the Fixed receipt price option?**

When you select the **Fixed receipt price** check box on the **Item model group** page for an item, the system will use receipt price as a standard cost for the inventory receipt. If there's a difference between the purchase price and the default item cost price configured for a product, the difference will be posted to the **Fixed receipt price profit** or **Fixed receipt price** **loss** account and offset to the **Fixed receipt price offset** account that you specify on the **Inventory posting profile** page.

You should select this option when you use a periodic costing model such as FIFO, LIFO, or weighted average and you have a requirement to track a purchase price variance in the ledger when the price of a receipt is different than the default item cost.

### Moving average

**Is moving average the same as a floating average?**

The terms moving average, floating average, and running average are often used synonymously. Of these terms, Moving average is the only official costing model available in Supply Chain Management. While the term running average isn't an official costing model, it's the technique that is used when you use a periodic costing model such as FIFO, LIFO, or weighted average. The term floating average isn't used in Supply Chain Management and may have different connotations in other systems.

**How can I accommodate the difference between the product receipt price and invoice price when I use moving average?**

When you use moving average, the physical cost (receipt price) is used to calculate the moving average for all issue transactions. If there's a difference between the physical cost (receipt price) and the financial cost (invoice price), the system will automatically post the difference to the Main account that you specify on the **Price difference for moving average** posting type found in the **Inventory** tab of the **Inventory posting profile** page.

**Where is the price difference for moving average presented in the general ledger?**

When there's a price difference between posting a physical update and a financial update for a receipt, the difference is posted to the **Main account** that you specify in the **Price difference for moving average** posting type on the **Inventory** tab of the **Inventory posting profile** page. For more information, see [Moving average](moving-average.md).

**When I use moving average, what happens if there's an issue before the receipt?**

This is typically the result of either allowing **Physical negative inventory** on the **Item model group**, or the backdating of an issue. For more information, see the [Negative inventory](#negative-inventory) section of this topic.

If you're backdating transactions, we recommend that you carefully consider your business process and operations to determine if there's a way you can avoid this scenario. When you backdate a transaction for an item that is using moving average, they system will assign the current moving average to the transaction. Later issues aren't adjusted. For more information about moving average with backdated transactions, see [Moving average](moving-average.md).

### Standard costing

**What is the difference between standard costing and fixed receipt price?**

Standard costing requires that you define an item price and activate the cost in a costing version. This cost is used for all receipts and issues. Variances for the receipts to inventory are recorded in the general ledger using the Standard cost variance accounts that you specify on the Inventory posting profile in the Standard cost tab.

However, when you use Fixed receipt price, only the cost for receipts is fixed and the system used the cost that you specify on the Manage costs FastTab of the Released product. Differences between the default cost and the purchase order price will cause the purchase price variance to post into the Fixed receipt price profit and loss accounts. Issues don't use the fixed receipt price. Instead, issues will be valued at the running average at the time of posting (unless you use marking) and revalued to the heuristic model you select when you run inventory closing.

**Can you use FEFO reservations with standard costing?**

Yes, you can use FEFO reservations on an Item model group when you select Standard costing. FEFO reservations control the reservation logic that is used for the physical handling of the items, while Standard costing controls the physical and financial cost for an item.

**Can you upload pending prices?**

Yes, you can use the Excel add-in or the Data Management Framework to upload a pending price. The current entities that are recommended to use are as follows:

- Pending item prices (V2)
- Pending route cost category unit costs
- Costing sheet node calculation factors (V2)

**How frequently can you update the standard cost for an item?**

There's no limit to the frequency that you can activate a new standard cost. If you activate a new cost for an item on the same day that last cost was activated, the system will use the most recent activated cost on new transactions or updates (such as to existing transactions

**Can you deactivate or delete an activated cost?**

No, you can't deactivate or delete an activated cost. If you've incorrectly activated a cost, you can activate a new cost with the correct cost.

**Are calculation groups used with Standard costing?**

Yes, calculation groups can be used with any item regardless of the item model group you choose. The calculation groups are used during the cost rollup or cost calculation process to determine the settings that should be used for the item(s) you're running a calculation for. For more information about calculation groups, see [BOM calculations groups](bom-calculation-groups.md).

**When should I use a planned costing version?**

Costing versions can have a type of standard cost or planned cost. The standard cost type is used for the costs that are active in the system and will be posted in transactions. The planned cost type is used for running simulations on costs and doesn't affect the cost of transactions.

**Can the total cost from one entity be transferred to another entity as the selling cost?**

No automated way exists to copy costs from one company to another. Additionally, there's no automated way to copy costs from a purchase price to a sales price. If your organization needs to do this, consider whether you can use the Data Management Framework to export the data out of your costing version and upload into a different company as either a sales price in the costing version or as a trade agreement. Manual manipulation of the files may be necessary.

**What is the best way to copy planned costs into a standard costing version?**

You can use the **Copy** button on the **Costing versions** page to copy item prices, cost category prices, or indirect costs from one costing version to another.
