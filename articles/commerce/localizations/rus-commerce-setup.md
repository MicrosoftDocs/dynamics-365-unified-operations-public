---
# required metadata

title: Set up the Dynamics 365 Commerce localization for Russia
description: This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.
author: akviklis@microsoft.com
ms.date: 07/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 07/01/2021
ms.dyn365.ops.version: 

---
# Set up the Dynamics 365 Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.

For more information about the Commerce localization for Russia, see [Russian localization scope](../../finance/localizations/russia.md) and [Commerce localization for Russia](rus-commerce-localization.md).

## Enable Russia-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Russia. For more information, see the [Commerce home page](../index.md).

To enable and use the Russia-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **RUS** (Russia).
1. In the POS functionality profile of every store that is located in Russia, set the **ISO** field to **RU** (Russia).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - (Russia) Customer information management in Retail POS
    - Enable Russian simplified customer address format

## Customer information management

**(Russia) Customer information management in Retail POS** feature impacts the Retail POS functionality for Russia. It enables the inquiry of customer information (such as email address or phone number) in sales transactions.

## Set up aggregation parameters for registering POS sales and return transactions
You can set up the aggregation parameters that are used to aggregate the point of sale (POS) sales and return transactions when the transactions are registered in Microsoft Dynamics 365 Commerce. 
When you select the aggregation parameters, Microsoft Dynamics 365 Commerce aggregates the positive sales quantities and negative return quantities for items that have identical inventory dimensions.

Use this procedure to set up the aggregation parameters that are used to aggregate POS sales and return transactions in Microsoft Dynamics 365 Commerce.

1.  Click **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce parameters**.

1.  Click **Posting** tab, and then in the **Aggregation** field group, select the **Voucher transactions** check box to aggregate voucher transactions.

1.  Select the **Sales and returns** check box to aggregate POS sales and return transactions.
    
    > [!NOTE]
    > This check box is available only if you select the **Voucher transactions** check box.


## Additional resources

[Commerce localization for Russia](rus-commerce-localization.md) 

[Prepaymants in Retail for Russia](rus-commerce-prepayments.md)
