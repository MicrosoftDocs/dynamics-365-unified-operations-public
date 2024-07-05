---
# required metadata

title: Set up pay invoice scenarios
description: This article describes how to configure Dynamics 365 Commerce to support various scenarios relating to invoice payments.
author: josaw1
ms.date: 11/14/2018
ms.topic: conceptual
# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Set up pay invoice scenarios

[!include [banner](includes/banner.md)]

The Pay invoice functionality in Dynamics 365 Commerce has been expanded to support:

- Payoff of multiple sales order invoices in a single POS transaction.
- Payment of various customer invoice types including free text invoices, project-based invoices, and credit notes.

To enable these scenarios, the functionality profile for stores must be configured as outlined in below.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles** and select a profile that's linked to the stores that you want to make the changes for.
2. On the **Functions** tab, configure the following parameters as needed.

    - **Sales order invoice** – Select **Yes** to allow users to pay one or more sales order-based invoices in a single POS transaction.
    - **Free text invoice** – Select **Yes** to allow users to pay one or more free text-based invoices in a single POS transaction.
    - **Project invoice** – Select **Yes** to allow users to pay one or more project-based invoices in a single POS transaction.
    - **Sales order credit note** – Select **Yes** to allow users to settle multiple sales order-based credit notes against open invoices or process a refund to the customer for an open credit note.

> [!NOTE]
> Payment or settlement of partial amounts is not yet supported.


[!INCLUDE[footer-include](../includes/footer-banner.md)]