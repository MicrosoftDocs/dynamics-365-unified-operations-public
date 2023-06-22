--- 
# required metadata 
 
title: Create a vendor bank account
description: This procedure shows you how to create a bank account for a vendor. 
author: GalynaFedorova
ms.date: 07/01/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendTable, VendBankAccounts, LogisticsPostalAddressSingle   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a vendor bank account

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a bank account for a vendor. You can use this procedure in demo data company USMF.

1. Go to **Procurement and sourcing > Vendors > All vendors**.
2. Select the vendor that you want to create a bank account for, and then click the link on the **Vendor account ID** field.
3. On the **Action Pane**, click **Vendor**.
4. Click **Bank accounts**.
5. On the **Action Pane**, click **New**.
6. In the **Bank account** field, type a value. This ID will be used to identify the bank account on the vendor record.  
7. In the **Name** field, type a value.
8. In the **Bank groups** field, enter or select a value.
9. In the **Routing number type** field, select an option. This is the type of routing number that's used for international payments.  
10. In the **Bank account number** field, type a value.
11. In the **SWIFT code** field, type a value.
12. In the **IBAN** field, type a value.
    - The IBAN number must be in the correct format. For example, you could use DE89370400440532013000.  
    - The status of the bank account is Active if the Active date has been reached, and the Expiration date has not been exceeded. It's also active if both the Active date and Expiration date fields are blank. If the dates in both the Active date and Expiration date fields are in the future electronic payments are not available. Other payment types are available and the bank account is active.  
13. Expand the **Setup** section.
14. In the **Text code** field, type a value. This field specifies a code that will appear on the bank statement of the recipient.  
15. In the **Message to bank** field, type a value.
16. In the **Exchange reference** field, type a value. This is the reference number for any forward-term or fixed-term rate of exchange.
17. In the **Currency** field, enter or select a value. When prenotes are issued, this section provides an overview of their status (pending or approved).  
18. Expand the **Address** section.
19. Expand the **Prenotes** section.
20. Expand the **Contact information** section.
21. In the **Telephone** field, type a value.
22. Close the page.
23. Click **Edit**.
24. Expand the **Payment** section.
25. In the **Bank account** field, select the account that you've just created.
26. Click **Save**. The address may be inherited from the bank group, if one is specified, or you can add it here.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]