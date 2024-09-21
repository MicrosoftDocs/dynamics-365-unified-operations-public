---
title: Seamless Sync with the Supply Chain Management pricing engine
description: Learn about how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Microsoft Dynamics 365 Sales with seamless integration.
author: henrikan
ms.author: Henrikan
ms.topic: article
ms.date: 23/9/2024
ms.reviewer: karlmaybach
audience: Application User
ms.search.region: global
ms.search.validFrom: 2024-01-10
---

# Seamless sync with the Supply Chain Management pricing engine

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements for prices and discounts. This pricing engine uses complex rules to determine the best price for a given quotation or order. When it's integrated with Dynamics 365 Sales, you can choose either to sync on demand with Supply Chain Management pricing engine Sync on-demand with the Supply Chain Management pricing engine - Finance & Operations | Dynamics 365 | Microsoft Learn or to apply seamless sync. Seamless sync rely on calculations on sales quotations and sales orders from Supply Chain Management and having the result of these calculations applied in a seamless synchronization to Dynamics 365 Sales as part of the experience when a user works in the Dynamics 365 Sales creating and updating sales quotations and orders. Seamless sync removes the need for the user working in Dynamics 365 Sales to do additional clicks in Dynamics 365 Sales, in order to get price, discount and totals on the sales quotation and order reflected in Dynamics 365 Sales. 

## Benefits
This capability will significantly improve user scenarios where front end staff predominantly work in Dynamics 365 Sales creating and updating sales quotations and sales orders. As sales quotation and sales order lines are added or updated in Dynamics 365 Sales, updated line price, discount and totals calculated in Microsoft Dynamics 365 Supply Chain Management are immediately reflected in the Dynamics 365 Sales UI without additional clicks required. There will in most cases be no need for front end staff to click on Price quote or Price order in Dynamics 365 Sales to have the sales quotation and sales order in Dynamics 365 Sales updated with the line prices, discounts and totals from sales quotation and sales order in Microsoft Dynamics 365 Supply Chain Management. 

This new capability is controlled through a new feature available in feature management: Automatically synchronize line data and totals with Dynamics 365 Sales.
Feature can be enabled in feature management, when Make Supply Chain Management price master when integrated with Dynamics 365 Sales is enabled. See here for additional details: Work with added efficiency in quote-to-cash with Dynamics 365 Sales - Finance & Operations | Dynamics 365 | Microsoft Learn

> [!NOTE]
> Automatically synchronize line data and totals with Dynamics 365 Sales is available in Supply Chain Management version 10.0.42. To leverage the feature you must be running Dual-write Supply Chain solution version 2.3.X.XXX or later.  

In Supply Chain Management Feature management, once you have enabled the feature, you turn the functionality on by setting both the Auto sync line data to Sales and Auto sync totals to Sales parameters to “Yes” on the Accounts receivable parameters page in the Dynamics 365 Sales Integration fast tab. It is recommended to set both parameters to “Yes”. You can only set the parameters to “Yes”, when Make Supply Chain Management price master parameter is “Yes. 

## How it works
When both the Auto sync line data to Sales and Auto sync totals to Sales parameters are set to “Yes”, calculations and synchronizations otherwise performed in Price Quote and Price Order will be seamlessly applied from Supply Chain Management to Dynamics 365 Sales when lines are added or updated to the sales quotation and order in Dynamics 365 Sales, without having to click Price Quote/ Price Order in Dynamics 365 Sales. 

### Parameter: Auto sync line data to Sales
When set to “Yes”, sales quotation and sales order line data (including line price and discount) will automatically be synchronized from the sales quotation and sales order line in Supply Chain Management to Dynamics 365 Sales when the line is created or updated from Dynamics 365 Sales. 

Line data synchronized cover more than monetary data, such as unit price, line discounts, and net amounts. It covers all mapped line data in the respective quote and order line mapping set to sync from Supply Chain Management to Dynamics 365 Sales. This also includes data such as requested ship and requested receipt dates which are potentially recalculated upon line entry into Supply Chain Management through the Dynamics 365 Sales UI. The benefit of this is that the user creating and updating a sales quotation and order line in Dynamics 365 Sales UI will, after saving the line, see the same line values in the Dynamics 365 Sales UI as in Supply Chain Management. This ensures full transparency and no misalignment between the data in both systems, removing the need for additional synchronization to be triggered from Supply Chain Management. 

### Parameter: Auto sync totals to Sales
When set to “Yes”, sales quotation and sales order subtotals and totals will automatically be calculated and synchronized from Supply Chain Management when lines are added, deleted, changed in Dynamics 365 Sales.

It is recommended to set both Auto sync parameters to “Yes”. That will ensure the best user experience working in the Dynamics 365 Sales user interface on sales quotations and sales orders, ensuring that both line monetary data, subtotals, and totals are updated with the values from the corresponding document in from Supply Chain Management, whenever a change, such as changing a line quantity, is performed by the user in Dynamics 365 Sales. 

There may be business scenarios, where a company desires to deviate from the recommended settings. In order to cater for such cases, it remains a business decision to deviate from the recommended settings. Either setting both Auto sync parameters to No, or setting one to No and the other to yes. Scenarios may originate from cases where custom pricing logic has been built into Dynamics 365 Sales or where it is only required to for the front end staff working in Dynamics 365 Sales to have insight line unit prices upon quote and order creation, not discounts, charges, sales taxes, totals, and subtotals.

## Working with seamless sync with Supply Chain Management pricing engine
The following presents selective examples of the user experience in Dynamics 365 Sales when working with seamless sync with Supply Chain Management pricing engine. 

### Scenario: Create sales quotation in Dynamics 365 Sales and add lines
#### Prerequisite for the scenario 
Auto sync line data to Sales =Yes and Auto sync totals to Sales = Yes. Pricelists are not used in Dynamics 365 Sales. Alternatively pricelists are used in Dynamics 365 Sales and the base sales price for released products in Supply Chain Management is 0 (zero). 
#### User story
In Dynamics 365 Sales, the user creates a sales quotation, saves the quotation and adds one more lines. 
After adding and saving lines to the sales quotation, the user will be positioned in the Quote page in the Summary tab. The user presented with information “Syncing from F&O”. This indicates to the user, that data is synchronized from the resulting sales quotation created in Supply Chain Management to the sales quotation in Dynamics 365 Sales. Once the synchronization has completed, “Syncing from F&O” disappears. 

In Dynamics 365 Sales UI on the sales quotation, the user can now see the Products grid fields price per unit, discount, and extended amount correctly updated with the data from the sales quotation lines in Supply Chain Management. Note that the discount field includes all line discounts including any multi line discount applied in Supply Chain Management. Also note that additional line data is synchronized from Supply Chain Management such as requested ship and receipt dates. You will see this data on the integration tab for the sales quotation line in quote page in Dynamics 365 Sales
Also, In Dynamics 365 Sales, the user will see the subtotal and total amounts for Detail amount, Discount (total discount), Freight amount (sum of line and header charges added automatically in Supply Chain Management), Total tax (sum of line and header taxes added automatically in Supply Chain Management), and Total amount automatically having been synchronized from the sales  quotation in Supply Chain Management. 

In this scenario, there is no need for the user working in Dynamics 365 Sales to press “Price Quote”. The quotation in Dynamics 365 Sales is current and aligned with the values from the sales quotation in Supply Chain Management. 

> [!NOTE]
> This scenario equally applies to the user story of create sales order in Dynamics 365 Sales and add lines

Be aware that, if a unit price > 0 (zero) is used on the quotation line when created in Dynamics 365 Sales, then this unit price is synched and applied to the sales quotation line when created in Supply Chain Management. This behaviour is unaffected by the seamless sync as the seamless sync for line data does not add additional calculations to line data in Supply Chain Management. 
If you manually add a line discount amount to a quotation line in Dynamics 365 Sales, then ensure to have the Copy quotation data to sales orders set to Yes in Accounts receivable parameters page in the Dynamics 365 Sales Integration fast tab. Otherwise this value will not be copied onto the resulting sales order line created in  Supply Chain Management when the quotation is won in in Dynamics 365 Sales. 

### Scenario example: Edit sales quotation lines in Dynamics 365 Sales 
#### Prerequisite for the scenario 
Auto sync line data to Sales =Yes and Auto sync totals to Sales = Yes. Pricelists are not used in Dynamics 365 Sales. Alternatively pricelists are used in Dynamics 365 Sales and the base sales price for released products in Supply Chain Management is 0 (zero). 
#### User story
In Dynamics 365 Sales, the user edits a sales quotation line. 
Continuing from the previous scenario, the user working in Dynamics 365 Sales can edit values on the sales quotation line that will synchronize to the quotation line in Supply Chain Management and potentially trigger additional standard Supply Chain management calculations on the sales quotation line in Supply Chain Management. An example of such a change is a quantity change. 
In Dynamics 365 Sales on the Quote page, the user edits one of the quotation lines previously created. In the Order Product page for a specific line, the user edits the quantity; alternatively the line discount amount. Then the user clicks Save or Save and Close. Information is shortly presented to the user “Syncing from F&O”. This indicates to the user, that data is synchronized from the resulting sales quotation line update in Supply Chain Management to the sales quotation line in Dynamics 365 Sales. Once the synchronization has completed, “Syncing from F&O” disappears.
Similar to the previous scenario, there is no need for the user working in Dynamics 365 Sales to press “Price Quote” to get the changes from Supply Chain Management, as the quotation line in Dynamics 365 Sales is current and aligned with the values from the sales quotation line in Supply Chain Management.

When you create an order in Sales, that order is immediately synced to Supply Chain Management by using the values that you entered in Sales. When you select **Price order** or **Price quote** in Sales, Supply Chain Management calculates the price for each order line, and the total order, based on trade agreement rules that are defined in Supply Chain Management. The new calculated values are then synced back to Sales.

> [!NOTE]
> This scenario equally applies to the user story of edit sales order lines in Dynamics 365 Sales

### Scenario example: Create sales quotation in Dynamics 365 Sales and add lines
#### Prerequisite for the scenario 
Auto sync line data to Sales =Yes and Auto sync totals to Sales = No. Pricelists are not used in Dynamics 365 Sales. Alternatively pricelists are used in Dynamics 365 Sales and the base sales price for released products in Supply Chain Management is 0 (zero). 
#### User story
In Dynamics 365 Sales, the user creates a sales quotation header and after saving starts to add lines. 
Once lines are saved to the sales quotation, the user will be positioned in the Quote page in the Summary tab. The user is presented with information “Syncing from F&O”. This indicates to the user, that data is synchronized from the resulting sales quotation created in Supply Chain Management to the sales quotation in Dynamics 365 Sales. Once the synchronization has completed, “Syncing from F&O” disappears. 

In Dynamics 365 Sales UI on the sales quotation, the user can now see the Products grid fields price per unit and extended amount. However as line discount field in Dynamics 365 Sales is not updated with any line discount data the sales quotation lines in Supply Chain Management, this field will be blank. The extended amount presented in the Dynamics 365 Sales UI may therefore not be aligned with the actual value in Supply Chain Management.

Also, In Dynamics 365 Sales, the user will see the subtotal and total amounts only for Detail amount, Pre-Freight amount, and Total amount.  
There will however be no subtotals nor totals data for Discount (total discount), Freight amount (sum of line and header charges added automatically in Supply Chain Management) and Total tax (sum of line and header taxes added automatically in Supply Chain Management) synchronized from the sales  quotation in Supply Chain Management to Dynamics 365 Sales. The Detail amount is the sum of the line extended amounts. In cases where the extended amounts in Dynamics 365 Sales are not aligned with Supply Chain Management, then the offset for all the subtotal and totals calculations presented in Dynamics 365 Sales UI will be incorrect compared with Supply Chain Management.

To get the line discounts, subtotals, and total amounts calculated on the sales quotation in Supply Chain Management and synched to the sales quotation in Dynamics 365 Sales, the user will press “Price Quote”. Only then, will be monetary amounts in Dynamics 365 Sales be aligned and current with Supply Chain Management. 

> [!NOTE]
> This scenario equally applies to the user story of create sales order in Dynamics 365 Sales and add lines.

## Sync on-demand with the Supply Chain Management pricing engine required
A few cases exist where sync on demand will be required to click “Price Quote” or “Price Order” in Dynamics 365 Sales to get line prices and discounts recalculated on a sales quotation and sales order in Supply Chain Management and synched to Dynamics 365 Sales.
Those are cases where suggested prices are applied in Dynamics 365 Sales, but actual prices are stored in trade agreements in Supply Chain Management or where the date type used to retrieve the sales price is Today. 

Both cases are explained in the following. 

### Case: Price data type = Today
Consider a setup where a sales price exists with price USD 20 effective from 28/8, and a sales price exists with price USD 19 effective from 1/9. Pricelists are not applied in Dynamics 365 Sales.
Trade agreement price 28/8       20USD
Trade agreement price 1/9         19USD
A sales order is created in in Dynamics 365 Sales on 28/8. A line is added. Line unit price for line #1 =  USD 20.
A second order line is added on 1/9. Line unit price for line #2 =  USD 19.
Following standard Supply Chain Management behaviour the line price of USD 19 is only applied to the #2 line. There is no change to line #1. 
If the user in Dynamics 365 Sales clicks Price Order, then both lines are re-priced in accordance with the trade agreement evaluation policy. End result will be that both line #1 and line #2 will get unit price USD 19.

> [!NOTE]
> This case equally applies to sales quotation.

### Case: Dynamics 365 Sales pricelists co-exists with SCM trade agreements
In this simple case, suggested sales prices are stored in Dynamics 365 Sales pricelist, whereas actual agreed upon and customer specific prices are stored in trade agreements in Supply Chain Management. 

Consider a setup where a sales price exists in Dynamics 365 Sales pricelist USD = 25 and a sales price exists in Supply Chain Management trade agreement in USD = 19. Trade agreement evaluation policy in Supply Chain Management excludes Manual Entry. 

A sales order is created in in Dynamics 365 Sales. A line is added. Line unit price for line #1 =  USD 25 representing the suggested sales price is applied on the order line, saved and synched to the sales order line in Supply Chain Management. 
If the user in Dynamics 365 Sales clicks Price Order, then this line is re-priced in accordance with the trade agreement evaluation policy. The line unit price in Supply Chain Management will be updated to USD = 19, and synched to Dynamics 365 Sales. 

In scenarios where there is a business requirement for applying suggested prices, stored in pricelists in Dynamics 365 Sales, into the sales quotation and sales order entry process, while applying customer specific prices stored in trade agreements Supply Chain Management different from the suggested prices, then on demand pricing  is required: Price Order.

> [!NOTE]
> This case equally applies to sales quotation.

## Limitations

The limitations presented here Sync on-demand with the Supply Chain Management pricing engine - Finance & Operations | Dynamics 365 | Microsoft Learn equally applies to Seamless sync with Supply Chain Management pricing engine.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
