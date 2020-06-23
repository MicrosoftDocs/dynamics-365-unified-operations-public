---
# required metadata

title: Enhancements to calculation of tax exemption
description: This topic describes enhancements to tax exempt calculations in the point of sale and Call Center. 
author: rubendel
manager: Tonya.Fehr
ms.date: 06/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
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

# Enhancements to calculation of tax exemption


[!include [banner](../includes/banner.md)]

This topic describes enhancements to tax exempt calculations in the point of sale and Call Center.

## Key terms

| Term | Description |
|---|---|
| B2B | An abbreviation for "Business to business" used to indicate sales between businesses, as opposed to sales between a retailer and an individual. 
| VAT | Value-added tax which is included in the price of a product. 

## Overview

This topice describes capabilities that have been added to support more robust tax calculation scenarios for cases where customers are tax exempt. 

**Calculate customer tax exempt** was added in 10.0.7 and introduced a new store-level setting to support using store based(non-customer based) tax calculations while also taking into account tax exemptions for specific customer. This scenario is important for retailers who may perform a mix of retail and B2B transactions in the point of sale and need to be able to have business customer exemptions handled in the point of sale automatically. 

**Calculate price inclusive tax exempt** will be added in 10.0.13 and introduces a new store-level setting to support tax inclusive scenarios which include customers for whom the prices should be reduced because their status makes them exempt from paying VAT. For that scenario, the default tax at the point of sale may be overridden to indicate the customer's exempt status with prices subsequently being reduced by the amount of tax that would normally be included. 


## Calculate customer tax exempt

Certain retail verticals, a primary example being liquor stores, sell goods to individuals and other businesses in cash and carry transactions. In many cases, however, transactions involving those different customer segments have different requirements for taxation purchases. When a liquor store sells goods to certain businesses, sales taxes associated with the items being sold may be exempt fof those particular businesses. In all other cases, normal sales tax should apply. 

To support this scenario, a property called **Calculate customer tax exempt** has been added to the settings for the retail store. Then this setting is enabled, typical store-based tax calculations are used. If a named customer is added to the transaction, the point of sale will check the taxes applicable to that customer. If the customer's tax settings have a tax code which is marked as "Exempt", but that tax is applicable for the transasction, that tax will be treated as "Exempt" for the transaction and will not be added to the transaction. 

This setting is applicable for stores in which the price does not include tax and the exemption calculation is also applicable if the **Use destination based tax** setting for the store is also set to "Yes".

### Calculate customer tax exempt setup

Steps provided are specific to testing this capability in demo data scenarios. Setup steps for other data sets will be similar. 

1. Navigate to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
2. Select the **San Francisco** and view its details by clicking on the **Retail Channel Id** for the store.
3. Click **Edit**.
4. In the **General** fasttab, change **Calculate customer tax exempt** to **Yes**.
5. Click **Save**
6. Search for **Sales tax groups** to view the sales tax groups form. 
7. Click **New** and provide a name for the sales tax group. 
8. In the setup fasttab, click **Add**. 
9. Select **RP_CAST** in the dropdown, then check the **Exempt** checkbox.
10. Click save. 
11. Navigate to **Retail and Commerce** > **All customers** and click on **Matthew Tolley**'s Account ID of **004009** to view details.
12. Click **Edit**, then scroll down to the **Invoice and delivery** fasttab and click on it to expand. 
13. In the **Sales tax group** field, click the dropdown and select the sales tax group created in step 7. 
14. Click **Save**
15. Search for **Distribution schedules**, then scroll down to schedule job **9999**, select it and click **Run now**.
16. Once the jobs have finished synchronizing, launch the point of sale.
17. In the point of sale, add item **91050** and observe the total due of **$75.06**.
18. Add **Matthew Tolley** to the transaction. 



## Related articles

