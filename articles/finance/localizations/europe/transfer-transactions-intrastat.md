---
title: Transfer transactions to the Intrastat
description: Learn about how to set up Intrastat parameters and transfer transactions to Intrastat in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - EcoResCategoryHierarchyListPage, EcoResCategory, UnitOfMeasureLookup, ProcCategoryAddCommodityCode, EcoResProductDetailsExtended, IntrastatCommodityLookup, IntrastatTransactionCode, IntrastatParameters, DeliveryMode, MarkupTable, SalesTableListPage, SalesCreateOrder, SalesTable, MarkupTrans, SalesEditLines
  - Intrastat, SysQueryForm, DeliveryReason, DeliveryTerms, DestinationCode
ms.dyn365.ops.version: Version 7.0.0
---

# Transfer transactions to the Intrastat

[!include [banner](../../includes/banner.md)]

This article explains how to set up Intrastat parameters and transfer transactions to Intrastat in Microsoft Dynamics 365 Finance, including a process for creating new and updating existing commodity code. 

## Create new and update existing commodity code

To create new and update existing commodity code, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management \> Setup \> Categories and attributes \> Category hierarchies**.
1. In the list, find or select the record **Intrastat commodity codes**, and then select the link.
1. In the tree, select a record. For example, select **Intrastat\Speaker**.  
1. Select **Edit**, and then expand the **Foreign trade** FastTab.
1. In the **Additional units** field, enter or select a value. For example, select **pcs**.  
1. In the **Weight not applicable** field, select **Yes**.
1. In the tree, select **Intrastat**.
1. Select **New category node**.   
1. In the **Name** field, enter the name of commodity. For example, enter "Other commodity".
1. In the **Code** field, enter the commodity code. For example, enter "995 00 00".  
1. In the **Friendly name** field, enter a value. For example, enter "Other".  
1. Select **Save**, and close then the page.

## Assign commodity code to product hierarchy and released product

To assign commodity code to product hierarchy and released product, follow these steps:

1. Use the quick filter to find records. For example, filter on the **Name** field with a value of "sales".
1. In the list, select the link on the row you want to work with.
1. In the tree, expand a category node. For example, expand **Sales hierarchy\Home audio**.  
1. In the tree, select the category to assign to the commodity code.  
1. Expand the **Commodity codes** FastTab, and then select **Add**.
1. In the **Select hierarchy** field, select **Intrastat**.
1. In the list, find the commodity code. Select the right arrow to select the code, and then select **OK**.
1. Go to **Product information management \> Products \> Released products**.
1. In the list, select the released product that you will assign to the commodity code, and then select **Edit**. 
1. Expand the **Foreign trade** FastTab, and in the **Commodity** field, enter the commodity code. 
1. In the **Charges percentage** field, enter a number. 
1. In the **Country/region** field, enter or select a country or region of origin. 
1. Expand the **Manage inventory** FastTab.
1. In the **Net weight** field, enter a weight in kilograms. 
1. Select **Save**.

## Set up Intrastat transaction codes and foreign trade parameters

To set up Intrastat transaction codes and foreign trade parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> Transaction codes**.
1. Select **New**.
1. In the **Transaction code** field, enter a value.  
1. In the **Name** field, enter the name of the transaction code.
1. In the **Statistical amount** field, select an option. For example, select **Empty**, which indicates that the statistical value to be reported for transactions with a transaction code of "21" will always be zero.  
1. Go to **Tax \> Setup \> Foreign trade \> Foreign trade parameters**.
1. In the **Transaction code** field, enter or select a value. 
1. In the **Credit note** field, enter or select a value. This value also identifies the physical return. The credit note for the physical return is transferred in the Intrastat journal in the opposite direction. For example, the return of arrival is transferred as dispatch. Otherwise, the credit note is considered a correction and is transferred with the same direction and opposite sign. For example, the correction of arrival is transferred as an arrival with a negative amount and the active flag is set to **Correction**.  
1. Expand the **Transfer** FastTab and in the **Items with commodity code** field, select **Yes**. Select this option to transfer only the transactions with a commodity code assigned. Transactions without a commodity code won't be transferred to Intrastat.  
1. In the **Transfer when meeting criterion for** field, select an option.  
1. Expand the **Commodity code hierarchy** section and on the **Country/region properties** tab, select **New**.
1. In the **Country/region** field, enter or select a value. 
1. In the **Intrastat code** field, enter the ISO code for the country/region.
1. In the **Country/region type** field, select **EU**.

## Set up modes of delivery and rules for including charges in Intrastat

To set up modes of delivery and rules for including charges in Intrastat, follow these steps:

1. In Dynamics 365 Finance, go to **Sales and marketing \> Setup \> Distribution \> Modes of delivery**.
1. In the list, find and select the record you want to update.  
1. Expand the **Foreign trade** FastTab, and then select **Edit**.
1. In the **Transport** field, enter or select a value.  
1. Go to **Accounts receivable \> Charges setup \> Charges code**.
1. Use the quick filter to find records. 
1. Expand the **Foreign trade** FastTab, and then select **Edit**
1. In the **Intrastat invoice value** field, select **Yes**. The amount is transferred to the **Invoice charges** field and is summarized with the amount transferred in the **Invoice amount** field. If the amount of changes need to be transferred to the **Statistical charges** field and summarized using **Statistical amount** field, in the **Intrastat statistical value** field, select **Yes**.  

## Sell products for EU customers

To sell products for EU customers, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders** and select **New**.
1. In the **Customer account** field, select an EU customer.  
1. Expand the **Delivery** FastTab.
1. In the **Mode of delivery** field, enter or select a value. For example, select **20 Air**.
1. Select **OK**.
1. Select the first row of sales order lines.  
1  In the **Item number** field, enter or select a value. For example, select **D001**.
1. Expand the **Line details** FastTab. On the **Foreign trade** tab, you can see the transport is filled automatically from the selected mode of delivery.  
1. In the **Port** field, enter or select a value.
1. Select **Financials**. Based on the settings, this amount is included in **Intrastat invoice value**.  
1. Select **Maintain charges**. 
1. In the **Charges code** field, enter or select a value.
1. Select the **Keep** checkbox.
1. In the **Charges value** field, enter a number.
1. Select **Save**, and then close the page.
1. On the Action Pane, select **Invoice \> Invoice**.
1. Expand the **Parameters** section, and in the **Quantity** field, select **All**.
1. Expand the **Setup** FastTab, and in the **Invoice date** field, enter a date. 
1. Select **OK**, select **OK** again, and then close the page.
1. Select **New**, and in the **Customer account** field, select an EU customer. 
1. Select **OK**.
1. In the **Item number** field, enter or select a value, and then select **Save**.
1. Select **Invoice**, and in the **Invoice date** field, enter a date. 
1. Select **OK**, and then select **OK** again.

## Transfer transactions to the Intrastat

To transfer transactions to the Intrastat, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Foreign trade \> Intrastat** and select **Transfer**.
1. In the **Customer invoice** field, select **Yes**.
1. Select the **Filter** button near the bottom of the pane, then in the list, mark the row with **Date**.
1. In the **Criteria** field, enter a value. For example, enter the filter for the period January 2015 (the exact value depends on your date format). 
1. Select **OK**, and then select **OK** again.
1. In the list, find and select the transferred record.
1. On the **General** tab, review the transferred data. Modify data as necessary.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
