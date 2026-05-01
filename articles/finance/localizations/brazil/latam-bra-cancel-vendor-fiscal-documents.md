---
title: Cancel vendor fiscal documents
description: Learn about how to cancel a vendor fiscal document for Brazil, which creates negative purchase orders and run the fiscal book integration process.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/03/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Cancel vendor fiscal documents

[!include [banner](../../includes/banner.md)]

You can cancel incorrect vendor fiscal documents that a legal entity generates and issues for vendors that aren't taxpayers. When you cancel an incorrect vendor fiscal document, you create a negative purchase order. When you post a negative purchase order and run the fiscal book integration process, all the tax, ledger, and financial transactions that are related to the purchase order are reversed in the fiscal books.

1. Select **Accounts payable** > **Common** > **Purchase orders** > **All purchase orders**.
1. Select a purchase order that has a purchase type of **Returned order** and an approval status of **Approved** or **Confirmed**.
1. On the Action Pane, on the **Purchase** tab, select **Cancel fiscal document** to open the **Cancel fiscal document** page.
1. In Microsoft Dynamics AX 2012 R3, and in cumulative update 6 or later for Microsoft Dynamics AX 2012 R2: In the **Reason code** field, select the identification code of your reason for canceling the vendor fiscal document.
1. In AX 2012 R3, and in cumulative update 6 or later for AX 2012 R2: In the **Reason comment** field, enter or update your reason for canceling the vendor fiscal document.

    > [!NOTE]
    > The reason for the cancellation must have a minimum of 15 characters.

1. Select the vendor invoices to cancel.
1. Select **OK** to create negative purchase orders for the selected vendor invoices.
1. On the **Action Pane**, select **Invoice** > **Invoice**.
1. On the **Vendor invoice** page, select **Post** > **Post** to post the invoice.

## See also

[Cancel a purchase complementary fiscal document](/dynamicsax-2012/appuser-itpro/bra-cancel-a-purchase-complementary-fiscal-document)

[Cancel a customer fiscal document](/dynamicsax-2012/appuser-itpro/bra-cancel-a-customer-fiscal-document)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
