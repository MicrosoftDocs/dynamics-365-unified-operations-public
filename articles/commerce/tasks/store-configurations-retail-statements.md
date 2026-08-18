--- 
title: Store configurations for Retail statements
description: Learn about store configurations for Retail statements in Microsoft Dynamics 365 Commerce. 
author: Shajain
ms.date: 08/18/2026
ms.topic: how-to 
ms.search.form: RetailStoreTable   
ms.reviewer: mirao
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template 
---
# Store configurations for Retail statements

[!include [banner](../includes/banner.md)]

This article explains store configurations for Retail statements in Microsoft Dynamics 365 Commerce. It also explains how to configure bank transaction types for payments from Commerce channels.

The following procedure walks through store configurations that affect how Commerce statements are created and posted. This procedure uses the USRT demo company.

To set up a store configuration for a Retail statement, follow these steps:

1. In Commerce headquarters, go to **Modules** > **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. In the list, find and select the record that you want.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. The settings in the **Statement/closing** FastTab affect the statement creation, validation, and posting for the store. Expand the **Statement/closing** FastTab.  
1. In the **Statement method** field, select the method you want to use to group the statement lines by.  
1. Select **Yes** in **One statement per day** if there should only be one statement created per day when creating statements from the statement creation batch job.  
1. The **Tender declaration calculation** field defines whether tender declarations should be added together or if the last one should be used.  
1. In the **Rounding** field, select the ledger account to post rounding differences into.  
1. In the **Maximum rounding difference** field, enter the maximum rounding difference allowed.
1. In the **Posting** field, enter the maximum total posting difference allowed for a statement.
1. In the **Shift** field, enter the maximum total difference within a shift in a statement.  
1. In the **Transaction** field, enter the maximum total difference in a statement line.  
1. In the **Closing method** field, define whether transactions that are included in a statement should be part of a closed shift or if they can be any transactions within the defined date and time range.  
1. In the **End of business day** field, enter a time if transactions that happen after midnight should be posted with the previous day.  
1. Select **Yes** in **Post as business day** if transactions that happen after midnight should be posted as part of the previous day.  
1. Select **Yes** in **Split by Statement method** to get statements created for each statement method defined. This action can be useful if the performance of the posting needs to be improved for stores with high transaction volumes since it creates many smaller statements that can be processed in parallel.  
1. In the **General** FastTab, in the **Default customer** field, select the customer account to use for sales to walk-in customers.

## Set up bank transaction types for Commerce payments

Use the **Define bank transaction type for Commerce payments** feature to specify the bank transaction type for customer order payments from stores, online stores, and call centers. This feature is turned on by default in Feature management.

The payment method setup page for any channel now contains two fields named **Bank transaction type**. Commerce uses each field for different payment scenarios.

| Payment scenario | Field to configure |
| ---------------- | ------------------ |
| Customer order payments from stores, online stores, and call centers | **Bank transaction type** in the **Posting** > **Account** section |
| Transactional statement posting | **Bank transaction type** in the **Posting** > **Account** section |
| Financial statement posting, including bank drops | **Bank transaction type** in the **Posting** > **Bank transaction** section |

> [!NOTE]
> You can configure individual credit or debit cards to have their own bank transaction type if you configure the payment method for bank posting. To enable the **Bank transaction type** for the card type, use the **Electronic payment setup** section on the payment method.

To configure a bank transaction type for Commerce payments, follow these steps:

1. In Commerce headquarters, open the store, online store, or call center that you want to configure.
1. Open the channel's payment methods.
1. Select the payment method.
1. In the **Posting** > **Account** section, set the **Bank transaction type** field.
1. For a card payment method, expand the **Electronic payment setup** section.
1. For each card type configured for bank posting, set the corresponding **Bank transaction type** field.
1. Save your changes.

> [!NOTE]
> The **Bank transaction type** field in the **Bank transaction** section continues to apply to financial statement posting, including bank drops. It doesn't apply to customer order payments or transactional statement posting.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
