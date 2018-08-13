---
# required metadata

title: Cancel a vendor fiscal document 
description: This topic provides information about how to cancel a vendor fiscal document for Brazil. 
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

# Cancel a vendor fiscal document 

You can cancel incorrect vendor fiscal documents that are generated and issued by a legal entity for nontaxpayer vendors. When you cancel an incorrect vendor fiscal document, a negative purchase order is created. When you post a negative purchase order and run the fiscal book integration process, all of the tax, ledger, and financial transactions that are related to the purchase order are reversed in the fiscal books.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

2.  Select a purchase order that has a purchase type of **Returned order** and an approval status of **Approved** or **Confirmed**.

3.  On the **Action Pane**, on the **Purchase** tab, click **Cancel fiscal document** to open the **Cancel fiscal document** form.

4.  In AX 2012 R3 and cumulative update 6 or later for AX 2012 R2: In the **Reason code** field, select the identification code of the reason to cancel the vendor fiscal document.

5.  In AX 2012 R3 and cumulative update 6 or later for AX 2012 R2: In the **Reason comment** field, enter or update the reason to cancel the vendor fiscal document.
    

    > [!NOTE]
    > The reason for the cancellation must contain a minimum of 15 characters.



6.  Select the vendor invoices that you want to cancel.

7.  Click **OK** to create negative purchase orders for the selected vendor invoices.

8.  On the **Action Pane**, click **Invoice** \> **Invoice**.

9.  In the **Vendor invoice** form, click **Post** \> **Post** to post the invoice.

## See also

[Cancel a purchase complementary fiscal document](https://github.com/MicrosoftDocs/DynamicsAX2012-technet/blob/master/dynamicsax2012-technet/bra-cancel-a-purchase-complementary-fiscal-document.md)

[Cancel a customer fiscal document](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/bra-cancel-cus-fis-doc/articles/financials/localizations/latam-bra-cancel-customer-fiscal-documents.md)
