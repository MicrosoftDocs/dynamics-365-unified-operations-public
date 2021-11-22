---
# required metadata

title: Skip "change due" dialog box in POS
description: This topic describes how to skip the "Change due" dialog box in the point of sale (POS) when a transaction is paid in full and there is no change due.
author: BrianShook
ms.date: 10/27/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Skip "change due" dialog box in POS

[!include [banner](../includes/banner.md)]

This topic describes how to skip the **Change due** dialog box in the point of sale (POS) when a transaction is paid in full and there's no change due.

For payments at the POS, there is now a greater prevalence of credit usage, as most transactions don't require change to be provided to the customer. In Dynamics 365 Commerce, you can configure POS so that the  **Change due** dialog is skipped unless there's actually change due back to the customer. The **Change due** dialog box will also be shown if the receipt format for gift receipts is configured to print **As required**. When gift receipts are configured to print **As required**, the option to print a gift receipt is included in the **Change due** dialog box, overriding the **Skip change due** configuration.

## Configure property to skip **Change due** dialog box

The property you need to configure to skip the **Change due** dialog box is found in the **Functionality profile** level, which is a store-level setting. 

To configure the property, follow these steps.

1. Search for the **Functionality profile** for the store where the dialog box should be skipped.
1. Open the functionality profile for the target store and select **Edit**. 
1. Expand the **Functions** FastTab. Under the **Terminal** subheading, in the **Change due** field, select **Skip when zero**. 
1. Select **Save**, and then run the **1070** channel configuration distribution schedule.
1. After the changes are synchronized, sign out of the POS and then sign back in. Make a transaction that has no change due to the customer to verify that the **Change due** dialog box isn't displayed.  

## Additional resources

[Payment methods](../payment-methods.md)

[Credit card setup, authorization, and capture](../../finance/accounts-receivable/credit-card-authorizations.md)

[Configure cash denominations for the point of sale (POS)](../cash-denominations.md)

[Configure credit card processing](../tasks/configure-credit-card-processing.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]