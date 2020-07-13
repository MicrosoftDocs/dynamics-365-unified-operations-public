---
# required metadata

title: Calculation of tax exemption
description: This topic describes functionality for tax exempt calculations in the point of sale and call center. 
author: rubendel
manager: annbe
ms.date: 07/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Calculation of tax exemption


[!include [banner](../includes/banner.md)]

This topic describes functionality for tax exempt calculations in the point of sale (POS) and call center.

## Key terms

| Term | Description |
|---|---|
| B2B | An abbreviation for "business to business" used to indicate sales between businesses, as opposed to sales between a retailer and an individual. |
| VAT | Value-added tax that is included in the price of a product. |


## Adjust prices for tax exemptions when price includes tax

In Commerce versions 10.0.13 and later, you can set a parameter in Commerce that adjusts prices in tax-inclusive scenarios when the transaction or certain taxes within the transaction should be exempted. When store-based taxes are in use, you can apply these exemptions using tax overrides. When customer-based taxes are in use at the store, the exemptions are applied automatically based on customer tax settings.  

This parameter setting is also supported for orders created in the call center and stores.

![Setting to adjust prices in tax exempt scenarios](media/CalcPriceInc.png)



## Set up price reductions for tax exemptions

The steps below are provided for testing this capability in demo data scenarios. Setup steps for other data sets are similar. 

1. Go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
2. Select **San Francisco**. To display the details, select **Retail Channel Id** for the store.
3. Select **Edit**.
4. In the **General** fasttab, set **Calculate price inclusive tax exempt** to **Yes**.
5. Set **Price includes tax** to **Yes**. 
6. Select **Save**.
7. Search **Sales tax groups** to view the sales tax groups form. 
8. Select **New** and enter a name for the sales tax group. 
9. In the **Setup** fasttab, select **Add**. 
10. Select **RP_CAST** in the dropdown, then select the **Exempt** checkbox.
11. Click **Save**. 
12. Search **Sales tax overrides**. 
13. Select **New** and enter a name for the the sales tax override.
14. Set status to **Enable**.
15. In the **Override Type** field, select **Sales tax group**.
16. In the **From** field, select **Any tax group**.
17. In the **To** field, select **Specified tax group**.
18. In the **From tax group** field, select **CA**.
19. In the **To tax group** field, select the sales tax group created in steps 7-11.
20. Select **Save**. 
21. Search **Sales tax override groups**. Select **Default** and then select **Edit**. 
22. Select **Add**, and then select the sales previously-created tax override. 
23. Select **Save**
24. Enter **Distribution schedules** in the search box. Select schedule job **9999** and then select **Run now**.
25. Once the jobs finish synchronizing, launch the POS.

> [!NOTE]
> Tax details for the channel may be cached. If a shift was open, close the shift and reactivate the POS if the changes don't appear right away. 

26. Add item **91050** to the transaction. 
27. Select **Tax overrides**, and then select **Override transaction tax**. 
28. Select the previously-created tax override. The tax is reduced to zero and the price for the line items is reduced to reflect the tax exemption. 

An alternative scenario is to set **Use customer based tax** for the store to **Yes**, then assign the sales tax group created in steps 7-11 above directly on the customer. When the customer is added to the transaction, the prices are reduced to reflect that customer's exempt status. 

### Check customer for exemptions when tax is exclusive of price

Certain retail verticals, such as liquor stores, sell goods to individuals and other businesses in cash and carry transactions. In many cases, however, transactions involving those different customer segments have different requirements for taxation purchases. When a liquor store sells goods to certain businesses, sales taxes associated with the items being sold may be exempt for those particular businesses. In all other cases, normal sales tax should apply. 

To support this scenario, enable **Calculate customer tax exempt** in the settings for the retail store. When this setting is enabled, and a customer is added to the transaction, the POS checks the taxes applicable to that customer. If the customer's tax settings have a tax code which is marked as **Exempt**, but the tax is applicable for the transasction, the tax is treated as exempt for the transaction and won't be added to the transaction. 

This setting applies to stores in which the price doesn't include tax and the exemption calculation is also supported if the **Use destination based tax** setting for the store is set to **Yes**.

### Set up calculation of tax exemption for a customer

The steps below are provided for testing this capability in demo data scenarios. Setup steps for other data sets are similar. 

1. Go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
2. Select **San Francisco**. To display the details, select **Retail Channel Id** for the store.
3. Select **Edit**.
4. In the **General** fasttab, set **Calculate customer tax exempt** to **Yes**.
5. Select **Save**.
6. Search **Sales tax groups** to display the sales tax groups form. 
7. Click **New** and enter a name for the sales tax group. 
8. In the setup fasttab, select **Add**. 
9. Select **RP_CAST** in the dropdown, then select the **Exempt** checkbox.
10. Select **Save**. 
11. Go to **Retail and Commerce** > **All customers**, and select the **004009** account ID for **Matthew Tolley**.
12. Select **Edit**. Expand the **Invoice and delivery** fasttab. 
13. In the **Sales tax group** field, select the sales tax group created in steps 7-10. 
14. Select **Save**.
15. Enter **Distribution schedules** in the search box. Select schedule job **9999**, and the select **Run now**.
16. Once the jobs finish synchronizing, launch the POS.
17. In the POS, add item **91050**. The total due is **$75.06**.
18. Add **Matthew Tolley** to the transaction. When **Matthew Tolley** is added, taxes are recalculated to take into account his exemption.


