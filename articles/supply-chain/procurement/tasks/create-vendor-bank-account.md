---
title: Create a vendor bank account
description: Learn how to create a bank account for a vendor, including a step-by-step process for procedures in the USMF demo data company. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: VendTable, VendBankAccounts, LogisticsPostalAddressSingle 
ms.topic: how-to
ms.date: 05/28/2026
ms.custom: 
  - bap-template
---

# Create a vendor bank account

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a bank account for a vendor. You can use this procedure in demo data company USMF.

1. Go to **Procurement and sourcing** > **Vendors** > **All vendors**.
1. Select the vendor that you want to create a bank account for, and then select the link on the **Vendor account ID** field.
1. On the Action Pane, select **Vendor**.
1. Select **Bank accounts**.
1. On the Action Pane, select **New**.
1. In the **Bank account** field, type a value. This ID identifies the bank account on the vendor record.  
1. In the **Name** field, type a value.
1. In the **Bank groups** field, enter or select a value.
1. In the **Routing number type** field, select an option. This type of routing number is used for international payments.  
1. In the **Bank account number** field, type a value.
1. In the **SWIFT code** field, type a value.
1. In the **IBAN** field, type a value.
    - The IBAN number must be in the correct format. For example, you could use *DE89370400440532013000*.  
    - The status of the bank account is *Active* if the **Active date** is reached, and the **Expiration date** isn't exceeded. It's also active if both the **Active date** and **Expiration date** fields are blank. If the dates in both the **Active date** and **Expiration date** fields are in the future, electronic payments aren't available. Other payment types are available and the bank account is active.  
1. Expand the **Setup** section.
1. In the **Text code** field, type a value. This field specifies a code that appears on the bank statement of the recipient.  
1. In the **Message to bank** field, type a value.
1. In the **Exchange reference** field, type a value. This is the reference number for any forward-term or fixed-term rate of exchange.
1. In the **Currency** field, enter or select a value. When prenotes are issued, this section provides an overview of their status (pending or approved).  
1. Expand the **Address** section.
1. Expand the **Prenotes** section.
1. Expand the **Contact information** section.
1. In the **Telephone** field, type a value.
1. Close the page.
1. Select **Edit**.
1. Expand the **Payment** section.
1. In the **Bank account** field, select the account that you just created.
1. Select **Save**. The address might be inherited from the bank group, if one is specified, or you can add it here.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
