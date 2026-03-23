--- 
title: Payment configurations for Retail statements
description: Learn how to set up payment configurations for Retail statements in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 02/11/2026
ms.topic: how-to 
ms.search.form: RetailStoreTable, RetailStoreTenderTypeTable   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Payment configurations for Retail statements

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to set up payment configurations for Retail statements in Microsoft Dynamics 365 Commerce.

The following procedure demonstrates configurations for Commerce store payment methods, which affect how statements get created and posted. The procedure uses the USRT demo company.

To set up a payment configuration, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. On the **Action Pane**, select **Set up**.
1. Select **Payment methods**.
1. Expand or collapse the **Posting** section.
1. Select **Edit**.
1. Select whether the amounts received for this payment method should be posted to a ledger account or bank account.  
1. Select the account that amounts received for this payment method should be posted to.  
1. Select an account to post possible differences between the total transaction amount received and the amount counted for this payment method.  
1. Enter an amount to control when the difference amount should be posted to another difference account. You can use this value to track large differences.  
1. Select an account to post possible differences between the total transaction amount received and the amount counted, when it exceeds the value that is defined in the **Maximum difference amount** field.  
1. Select **Yes** to post bank drop amounts to a separate account.  
1. Select whether bank drop amounts should be posted to a ledger account or a bank account.  
1. Select the account to post bank drop amounts into.  
1. Select the bank transaction type to use when posting bank drop amounts to the bank account.  
1. Select **Yes** to post safe drop amounts to a separate account.  
1. Select whether safe drop amounts should be posted to the ledger account or the bank account.  
1. Select the account to post safe drop amounts into.  
1. Select **Save**.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
