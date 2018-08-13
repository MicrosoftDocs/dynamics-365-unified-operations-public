---
# required metadata

title: Cancel a customer fiscal document 
description: This topic provides information about cancelling a customer fiscal document for Brazil. 
author: ShylaThompson
manager: AnnBe
ms.date: 6/5/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Cancel a customer fiscal document 

You can cancel an incorrect customer fiscal document by using the **Cancel fiscal document** form. When you cancel a fiscal document, the fiscal document is marked as canceled, and all of the ledger transactions and financial transactions are reversed.

1.  Click **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.
    
    –or–
    
    Click **Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders**.

2.  Select a sales order to cancel.

3.  On the **Action Pane**, click the **Sell** tab, and then click **Cancel fiscal document** to open the **Cancel fiscal document** form. 

4.  In AX 2012 R3 and cumulative update 6 or later for AX 2012 R2: In the **Reason code** field, select the identification code of the reason that is used to cancel the customer fiscal document.

5.  In AX 2012 R3 and cumulative update 6 or later for AX 2012 R2: In the **Reason comment** field, enter or update the reason to cancel the fiscal document.
    

    > [!NOTE]
    > The reason for the cancellation must contain a minimum of 15 characters.



6.  On the **Invoice** tab, select the **Mark** check boxes to select individual sales order lines. Alternatively, you can select the **Select all** check box to select all of the sales order lines.

7.  Click **OK** to create transactions that have negative quantities.

8.  On the **All sales orders** list page, select the transactions that have negative quantities.

9.  On the **Action Pane**, click the **Invoice** tab, and then click **Invoice** to open the **Posting invoice** form.

10. Select the **Posting** and **Print invoice** check boxes to post and print the invoice.

11. Click **OK** to cancel the sales order, and to reverse all of the ledger and financial transactions.

## See also

[Cancel a vendor fiscal document](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/bra-cancel-ven-fis-doc/articles/financials/localizations/latam-bra-cancel-vendor-fiscal-documents.md)
