---
title: Cancel a customer fiscal document (Brazil)
description: This article describes how to cancel a customer fiscal document that marks the fiscal document as canceled and reverses all ledger and financial transactions in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# Cancel a customer fiscal document (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to cancel a customer fiscal document that marks the fiscal document as canceled and reverses all ledger and financial transactions in Brazil with Microsoft Dynamics 365 Finance.

You can cancel an incorrect customer fiscal document by using the **Cancel fiscal document** page. When you cancel a fiscal document, the fiscal document is marked as canceled, and all of the ledger transactions and financial transactions are reversed.

To cancel a customer fiscal document, follow these steps:

1. In Dynamics 365 Finance, go to either **Accounts receivable \> Common \> Sales orders \> All sales orders** or **Sales and marketing \> Common \> Sales orders \> All sales orders**.
1. Select a sales order to cancel.
1. On the Action Pane, select the **Sell** tab, and then select **Cancel fiscal document** to open the **Cancel fiscal document** page. 
1. In the **Reason code** field, select the identification code of the reason used to cancel the customer fiscal document.
1. In the **Reason comment** field, enter or update the reason to cancel the fiscal document.

    > [!NOTE]
    > The reason for the cancellation must contain a minimum of 15 characters.

1. On the **Invoice** tab, select the **Mark** checkboxes to select individual sales order lines, or select the **Select all** checkbox to select all of the sales order lines.
1. Select **OK** to create transactions that have negative quantities.
1. On the **All sales orders** list page, select the transactions that have negative quantities.
1. On the Action Pane, select the **Invoice** tab, and then select **Invoice** to open the **Posting invoice** page.
1. Select the **Posting** and **Print invoice** checkboxes to post and print the invoice.
1. Select **OK** to cancel the sales order and reverse all of the ledger and financial transactions.

## More information

[Cancel vendor fiscal documents](latam-bra-cancel-vendor-fiscal-documents.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
