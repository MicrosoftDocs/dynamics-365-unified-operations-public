---
title: MX-00007 Customer registration IDs and other information
description: Learn how to create a customer with fiscal and other related information used in electronic invoices and legal reports for Mexico in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - CustTable, DirPartyQuickCreateForm
  - DefaultDashboard
---

# MX-00007 Customer registration IDs and other information

[!include [banner](../../includes/banner.md)]

This article explains how to create a customer with fiscal and other related information used in electronic invoices and legal reports for Mexico in Microsoft Dynamics 365 Finance.

The following procedure was created using the demo data company MXMF.

To create a customer with fiscal and other related information, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. In the **Customer group** field, enter a value.
1. Select **Save**.
1. In the list, select the customer you created.  
1. Expand or collapse the **Miscellaneous details** section.
1. In the **Company type** field, select an option.
1. In the **RFC number** field, enter the 12 or 13-character Federal Registration for Taxpayers (RFC) number of the customer.  

    > [!NOTE]
    > The RFC number is the tax identification number assigned by tax authorities to a person or a corporation. The tax registration IDs are validated according to the format specified by tax authorities in Mexico.

1. In the **CURP number** field, enter the 18-character Clave Única de Registro de Población (CURP) number of the customer. If the company type for this customer is **Legal Person**, this field is required.  
1. In the **State inscription** field, enter a value.
1. In the **Tax registration ID** field, enter a value. If the company type for this customer is **Foreign**, this field is required.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
