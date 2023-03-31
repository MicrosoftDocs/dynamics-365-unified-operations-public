---
title: Transfer transactions to the Intrastat
description: This procedure walks you through how to set up Intrastat parameters and transfer transactions to Intrastat.
author: AdamTrukawka
ms.date: 07/22/2019
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

This procedure walks you through how to set up Intrastat parameters and transfer transactions to Intrastat. This procedure was created using the demo data company DEMF.


## Create new and update existing commodity code
1. In the Navigation pane, go to **Modules > Product information management > Setup > Categories and attributes > Category hierarchies**.
2. In the list, find or select the record **Intrastat commodity codes.**
3. In the list, click the link in the selected row.
4. In the tree, select a record. For example, select **Intrastat\Speaker**.  
5. Click **Edit**.
6. Expand the **Foreign trade** fastTab.
7. In the **Additional units** field, enter or select a value. For example, choose **pcs**.  
8. Select **Yes** in the **Weight not applicable** field.
9. In the tree, select **Intrastat**.
10. Click **New category node**.
11. In the **Name** field, enter the name of commodity. For example, type **Other commodity**.  
12. In the **Code** field, enter the commodity code. For example, type **995 00 00**.  
13. In the Friendly name field, type a value. For example, type **Other**.  
14. Click **Save**.
15. Close the page.

## Assign commodity code to product hierarchy and released product
1. Use the quick filter to find records. For example, filter on the **Name** field with a value of **sales**.
2. In the list, click the link in the selected row.
3. In the tree, expand **a category node**. For example, expand **Sales hierarchy\Home audio**.  
4. In the tree, select **the category to assign to the commodity code**. For example, select **Sales hierarchy\Home audio\Speakers.  
5. Expand the **Commodity codes** fastTab.
6. Click **Add**.
7. In the **Select hierarchy** field, select **Intrastat**.
8. In the list, find and select the commodity code. For example, select **920 20 34 Speaker**.  
9. Click the right arrow to select code.
10. Click **OK**.
11. In the Navigation pane, go to **Modules > Product information management > Products > Released products**.
12. In the list, choose the released product that you will assign to the commodity code. For example, choose **D0001**.  
13. Click **Edit**.
14. Expand the **Foreign trade** fastTab.
15. In the **Commodity** field, enter the commodity code. For example, select value **920 20 34 Speaker**.    
16. In the **Charges percentage** field, enter a number. For example, enter **3**.  
17. In the **Country/region** field, enter or select a country or region of origin. For example, select **AUT**.  
18. Expand the **Manage inventory** fastTab.
19. In the **Net weight** field, enter a weight in kg. For example, enter **2.5**.  
20. Click **Save**.

## Set up Intrastat transaction codes and foreign trade parameters
1. In the Navigation pane, go to **Modules > Tax > Setup > Foreign trade > Transaction codes**.
2. Click **New**.
3. In the **Transaction code** field, type a value. For example, enter **21** for the transaction code used as return.  
4. In the **Name** field, type the name of transaction code. For example, enter **Return**.  
5. In the **Statistical amount** field, select an option. For example, select **Empty** which indicates that the Statistical value to be reported for transactions with Transaction code of **21** will always be zero.  
6. In the Navigation pane, go to **Modules > Tax > Setup > Foreign trade > Foreign trade parameters**.
7. In the **Transaction code** field, enter or select a value. For example, select **11**.  
8. In the **Credit note** field, enter or select a value. This value also identifies the physical return. The credit note for the physical return will be transferred in the Intrastat journal with opposite direction. For example, the return of arrival is transferred as dispatch.   Otherwise, the credit note is considered a correction and is transferred with the same direction and opposite sign. For example, the correction of arrival is transferred as an arrival with negative amount and the active flag is set to **Correction**.  
9. Expand the **Transfer** fastTab.
10. Select **Yes** in the **Items with commodity code** field. Select this option to transfer only the transactions with a commodity code assigned. Transactions without a commodity code won**t be transferred to Intrastat.  
11. In the **Transfer when meeting criterion for** field, select an option. For example, select **One of the selected**.  
12. Expand the **Commodity code hierarchy** section.
13. Click the **Country/region properties** tab.
14. Click **New**.
15. In the **Country/region** field, enter or select a value. For example, select the value **FRA**.  
16. In the **Intrastat code** field, enter the ISO code for the country.  For example, type **FR**.  
17. In the **Country/region type** field, select **EU**.
18. Click the Number sequences tab.

## Set up Modes of delivery and rules for including charges in Intrastat
1. In the Navigation pane, go to **Modules > Sales and marketing > Setup > Distribution > Modes of delivery**.
2. In the list, find and select the desired record. For example, select **20 Air**.  
3. Expand the **Foreign trade** fastTab.
4. Click **Edit**.
5. In the **Transport** field, enter or select a value. For example, select **02**.  
6. In the Navigation pane, go to **Modules > Accounts receivable > Charges setup > Charges code**.
7. Use the quick filter to find records. For example, filter on the Charges code field with a value of **freight**.
8. Expand the **Foreign trade** fastTab.
9. Click **Edit**.
10. Select **Yes** in the **Intrastat invoice value** field. The amount will be transferred to the **Invoice charges** field and will be summarized with the amount transferred in the Invoice amount field. Select **Yes** in the **Intrastat statistical value** field if the amount of changes need to be transferred to the **Statistical charges** field and summarized with **Statistical amount** field.  

## Sell products for EU customers
1. In the Navigation pane, go to **Modules > Accounts receivable > Orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, select an EU customer. For example, select **DE-012 Litware Retail**.  
4. Expand the **Delivery** fastTab.
5. In the **Mode of delivery** field, enter or select a value. For example, select **20 Air**.  
6. Click **OK**.
7. Select the first row of sales order lines.
8. In the **Item number** field, enter or select a value. For example, select **D001**.  
9. Expand the **Line details** fastTab.
10. Click the **Foreign trade** tab. The transport is filled automatically from the chosen Mode of delivery.  
11. In the **Port** field, enter or select a value.
12. Click **Financials**. As per the settings, this amount will be included in **Intrastat invoice value**.  
13. Click **Maintain charges**.
14. In the **Charges code** field, enter or select a value. For example, select **FREIGHT**.  
15. Select the **Keep** check box.
16. In the **Charges value** field, enter a number. For example, enter **10**.  
17. Click **Save**.
18. Close the page.
19. On the Action Pane, click **Invoice**.
20. Click **Invoice**.
21. Expand the **Parameters** section.
22. In the **Quantity** field, select **All**.
23. Expand the **Setup** fastTab.
24. In the **Invoice date** field, enter a date. For example, enter **2015-01-31**.  
25. Click **OK**.
26. Click **OK**.
27. Close the page.
28. Click **New**.
29. In the **Customer account** field, select an EU customer. For example, select **DE-013 Trey Wholesales**.
30. Click **OK**.
31. In the **Item number** field, enter or select a value. For example, select **D0001**.  
32. Click **Save**.
33. Click **Invoice**.
34. In the **Invoice date** field, enter a date. For example, enter the date **2015-01-31**.  
35. Click **OK**.
36. Click **OK**.

## Transfer transactions to the Intrastat
1. In the Navigation pane, go to **Modules > Tax > Declarations > Foreign trade > Intrastat**.
2. Click **Transfer**.
3. Select **Yes** in the **Customer invoice** field.
4. Click **Filter**.
5. In the list, mark the row with **Date**.
6. In the **Criteria** field, type a value. For example, enter the filter for the period January 2015 (the exact value depends on your date format): 1/1/2015..1/31/2015  
7. Click **OK**.
8. Click **OK**.
9. In the list, find and selected the transferred record.
10. Click the **General** tab.
    
Review transferred data, including country\region of destination/dispatch, country of origin, weight, quantity, quantity in additional units, commodity, transaction code, invoice amounts and statistical amounts. You can modify data if necessary.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
