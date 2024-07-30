---
title: Cancel a customer fiscal document (Brazil)
description: Learn about canceling a customer fiscal document for Brazil, which marks the fiscal document as canceled and reverses all ledger and financial transactions.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/05/2018
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Cancel a customer fiscal document (Brazil)

[!include [banner](../../includes/banner.md)]

You can cancel an incorrect customer fiscal document by using the **Cancel fiscal document** page. When you cancel a fiscal document, the fiscal document is marked as canceled, and all of the ledger transactions and financial transactions are reversed.

1.  Click **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.
    
    –or–
    
    Click **Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Select a sales order to cancel.

3.  On the Action Pane, click the **Sell** tab, and then click **Cancel fiscal document** to open the **Cancel fiscal document** page. 

4.  In the **Reason code** field, select the identification code of the reason that is used to cancel the customer fiscal document.

5.  In the **Reason comment** field, enter or update the reason to cancel the fiscal document.

    > [!NOTE]
    > The reason for the cancellation must contain a minimum of 15 characters.

6.  On the **Invoice** tab, select the **Mark** check boxes to select individual sales order lines. Alternatively, you can select the **Select all** check box to select all of the sales order lines.

7.  Click **OK** to create transactions that have negative quantities.

8.  On the **All sales orders** list page, select the transactions that have negative quantities.

9.  On the **Action Pane**, click the **Invoice** tab, and then click **Invoice** to open the **Posting invoice** page.

10. Select the **Posting** and **Print invoice** check boxes to post and print the invoice.

11. Click **OK** to cancel the sales order, and to reverse all of the ledger and financial transactions.

## Additional resources

[Cancel vendor fiscal documents](latam-bra-cancel-vendor-fiscal-documents.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
