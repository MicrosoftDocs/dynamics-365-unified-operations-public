---
# required metadata

title: Set up pay invoice scenarios
description: Learn how to configure Microsoft Dynamics 365 Commerce to support various scenarios relating to invoice payments.
author: josaw1
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.custom: 
  - bap-template
---
# Set up pay invoice scenarios

[!INCLUDE [banner](includes/banner.md)]

The Pay invoice functionality in Microsoft Dynamics 365 Commerce is expanded to support:

- Payoff of multiple sales order invoices in a single POS transaction.
- Payment of various customer invoice types, including free text invoices, project-based invoices, and credit notes.

To enable these scenarios, configure the functionality profile for stores as outlined in the following steps.

1. Go to **Retail and Commerce > Channel setup > POS setup > POS profiles > Functionality profiles** and select a profile linked to the stores where you want to make the changes.
1. On the **Functions** tab, configure the following parameters as needed.

    - **Sales order invoice** – Select **Yes** to allow users to pay one or more sales order-based invoices in a single POS transaction.
    - **Free text invoice** – Select **Yes** to allow users to pay one or more free text-based invoices in a single POS transaction.
    - **Project invoice** – Select **Yes** to allow users to pay one or more project-based invoices in a single POS transaction.
    - **Sales order credit note** – Select **Yes** to allow users to settle multiple sales order-based credit notes against open invoices or process a refund to the customer for an open credit note.

> [!NOTE]
> The system doesn't yet support payment or settlement of partial amounts.


[!INCLUDE [footer-include](../includes/footer-banner.md)]
