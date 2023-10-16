---
title: Transfer transactions to the Intrastat
description: This article provides information about how to set up Intrastat parameters and transfer transactions to Intrastat.
author: AdamTrukawka
ms.date: 08/01/2023
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - EcoResCategoryHierarchyListPage, EcoResCategory, UnitOfMeasureLookup, ProcCategoryAddCommodityCode, EcoResProductDetailsExtended, IntrastatCommodityLookup, IntrastatTransactionCode, IntrastatParameters, DeliveryMode, MarkupTable, SalesTableListPage, SalesCreateOrder, SalesTable, MarkupTrans, SalesEditLines
  - Intrastat, SysQueryForm, DeliveryReason, DeliveryTerms, DestinationCode
---
# Transfer transactions to the Intrastat

[!include [banner](../../includes/banner.md)]

This aticle explains how to set up Intrastat parameters and transfer transactions to Intrastat. 

## Create new and update existing commodity code
1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
2. In the list, find or select the record **Intrastat commodity codes** and then select the link.
3. In the tree, select a record. For example, select **Intrastat\Speaker**.  
4. Select **Edit** and then expand the **Foreign trade** FastTab.
5. In the **Additional units** field, enter or select a value. For example, choose **pcs**.  
6. In the **Weight not applicable** field, select **Yes**.
7. In the tree, select **Intrastat**.
8. Select **New category node** and in the **Name** field, enter the name of commodity. For example, type **Other commodity**.  
9. In the **Code** field, enter the commodity code. For example, type **995 00 00**.  
10. In the **Friendly name** field, enter a value. For example, type **Other**.  
11. Select **Save** and close the page.

## Assign commodity code to product hierarchy and released product
1. Use the quick filter to find records. For example, filter on the **Name** field with a value of **sales**.
2. In the list, select the link on the row you want to work with.
3. In the tree, expand a category node. For example, expand **Sales hierarchy\Home audio**.  
4. In the tree, select the category to assign to the commodity code.  
5. Expand the **Commodity codes** FastTab and select **Add**.
6. In the **Select hierarchy** field, select **Intrastat**.
7. In the list, find and select the commodity code. 
8. Select the right arrow to select the code and then select **OK**.
9. Go to **Product information management** > **Products** > **Released products**.
10. In the list, select the released product that you will assign to the commodity code and select **Edit**. 
11. Expand the **Foreign trade** FastTab, and in the **Commodity** field, enter the commodity code. 
12. In the **Charges percentage** field, enter a number. 
13. In the **Country/region** field, enter or select a country or region of origin. 
14. Expand the **Manage inventory** FastTab and in the **Net weight** field, enter a weight in kg. 
15. Select **Save**.

## Set up Intrastat transaction codes and foreign trade parameters
1. Go to **Tax** > **Setup** > **Foreign trade** > **Transaction codes** and select **New**.
2. In the **Transaction code** field, enter a value.  
3. In the **Name** field, enter the name of transaction code.
4. In the **Statistical amount** field, select an option. For example, select **Empty** which indicates that the Statistical value to be reported for transactions with Transaction code of **21** will always be zero.  
5. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
6. In the **Transaction code** field, enter or select a value. 
7. In the **Credit note** field, enter or select a value. This value also identifies the physical return. The credit note for the physical return will be transferred in the Intrastat journal with opposite direction. For example, the return of arrival is transferred as dispatch. Otherwise, the credit note is considered a correction and is transferred with the same direction and opposite sign. For example, the correction of arrival is transferred as an arrival with negative amount and the active flag is set to **Correction**.  
8. Expand the **Transfer** FastTab and in the **Items with commodity code** field, select **Yes**. Select this option to transfer only the transactions with a commodity code assigned. Transactions without a commodity code won't be transferred to Intrastat.  
9. In the **Transfer when meeting criterion for** field, select an option.  
10. Expand the **Commodity code hierarchy** section and on the **Country/region properties** tab, select **New**.
11. In the **Country/region** field, enter or select a value. 
12. In the **Intrastat code** field, enter the ISO code for the country/region.
13. In the **Country/region type** field, select **EU**.

## Set up Modes of delivery and rules for including charges in Intrastat
1. Go to **Sales and marketing** > **Setup** > **Distribution** > **Modes of delivery**.
2. In the list, find and select the record you want to update.  
3. Expand the **Foreign trade** FastTab and then select **Edit**.
4. In the **Transport** field, enter or select a value.  
5. Go to **Accounts receivable** > **Charges setup** > **Charges code**.
6. Use the quick filter to find records. 
7. Expand the **Foreign trade** FastTab and select **Edit**
8. Select **Yes** in the **Intrastat invoice value** field. The amount will be transferred to the **Invoice charges** field and will be summarized with the amount transferred in the Invoice amount field. If the amount of changes need to be transferred to the **Statistical charges** field and summarized with **Statistical amount** field, select **Yes** in the **Intrastat statistical value** field .  

## Sell products for EU customers
1. Go to **Accounts receivable** > **Orders** > **All sales orders** and select **New**.
2. In the **Customer account** field, select an EU customer.  
3. Expand the **Delivery** FastTab and in the **Mode of delivery** field, enter or select a value. For example, select **20 Air**. Select **OK**.
4. Select the first row of sales order lines and in the **Item number** field, enter or select a value. For example, select **D001**.  
5. Expand the **Line details** FastTab. On the **Foreign trade** tab, you can see the transport is filled automatically from the selected mode of delivery.  
6. In the **Port** field, enter or select a value.
7. Select **Financials**. Based on the settings, this amount is included in **Intrastat invoice value**.  
8. Select **Maintain charges** and in the **Charges code** field, enter or select a value. .  
9. Select the **Keep** check box.
10. In the **Charges value** field, enter a number, select **Save**, and then close the page.
11. On the Action Pane, select **Invoice** > **Invoice**.
12. Expand the **Parameters** section and in the **Quantity** field, select **All**.
13. Expand the **Setup** FastTab and in the **Invoice date** field, enter a date. 
14. Select **OK**, select **OK** again, and then close the page.
15. Select **New**, and in the  **Customer account** field, select an EU customer. 
16. Select **OK**.
17. In the **Item number** field, enter or select a value and then select **Save**.
18. Select **Invoice** and in the **Invoice date** field, enter a date. 
19. Select **OK** and select **OK** again.


## Transfer transactions to the Intrastat
1. Go **Tax** > **Declarations** > **Foreign trade** > **Intrastat** and select **Transfer**.
2. In the **Customer invoice** field, select **Yes**.
3. Select **Filter** and in the list, mark the row with **Date**.
4. In the **Criteria** field, enter a value. For example, enter the filter for the period January 2015 (the exact value depends on your date format): 1/1/2015..1/31/2015  
5. Select **OK** and then select **Ok** again.
6. In the list, find and select the transferred record.
7. On the **General** tab, review the transferred data. Modify data as necessary.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
