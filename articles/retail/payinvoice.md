---
# required metadata

title: Set up pay invoice scenarios
description: This topic describes how to configure Dynamics 365 for Retail to support various scenarios relating to invoice payments.
author: josaw1
manager: AnnBe
ms.date: 11/14/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
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

The "Pay invoice" functionality in Dynamics 365 for Retail has been expanded to support:
- Payoff of multiple sales order invoices in a single POS transaction.
- Payment of various customer invoice types including free text invoice, project-based invoices, and credit notes.

To enable these scenarios, the functionality profile for stores must be configured as outlined in the steps below.  

1. Go to **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** and select a profile that's linked to the stores that you want to make the changes for.

1. On the **Functions** tab, configure the following parameters as needed.

    - **Sales order invoice:** Select **Yes** to allow users to pay one or more sales order-based invoice in a single POS transaction.

    - **Free text invoice:** Select **Yes** to allow users to pay one or more free text-based invoice in a single POS transaction.

    - **Project invoice:** Select **Yes** to allow users to pay one or more project-based invoice in a single POS transaction.

    - **Sales order credit note:** Select **Yes** to allow users to settle multiple sales order-based credit notes against open invoices or process the refund to the customer for the open credit note.

> [!NOTE]
> Payment or settlement of partial amounts is not yet supported.
