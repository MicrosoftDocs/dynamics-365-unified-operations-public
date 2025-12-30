---
title: Set up and use PKWiU codes for Poland
description: Learn hot to set up the PKWiU code for Poland in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
---

# Set up and use PKWiU codes for Poland

[!include [banner](../../includes/banner.md)]

Learn hot to set up the Polska Klasyfikacja Wyrobów i Usług (PKWiU) code for Poland in Microsoft Dynamics 365 Finance.

The PKWiU code is used for tax purposes to categorize goods and services sold in Poland. It is included on all sales order invoices, free text invoices, and invoices posted from the Project module. You can view the PKWiU code in the project invoice and print the project invoice by using the **Invoice journals** form. You can also set up notifications for when a PKWiU code is missing from an invoice.

To ensure that users include a PKWiU code on all invoices, select one of the following options in the **PKWiU code requirement** field on the **Accounts receivable parameters** page: 
- **None** – Do not display a message when a PKWiU code is missing from a sales order or a free text invoice. The PKWiU code is not required for invoices. 
- **Warning** – Display a message when you invoice a sales order or a free text invoice that is missing the PKWiU code. 
- **Error** – Display a message when you invoice a sales order or a free text invoice that is missing the PKWiU code and stop the invoice from being processed. 

## Assign a PKWiU code to the sales category hierarchy

Category hierarchies are used to classify products or transactions for reporting and analysis. The category hierarchy that is of the Sales category hierarchy type is used for organizing products for sales activities. You can assign a PKWiU code to the sales category hierarchy so that the PKWiU code is included on invoices that include non-inventoried items. 

To assign a PKWiU code to the sales category hierarchy, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** \> **Setup** \> **Categories and attributes** \> **Category hierarchies**. 
1. Select the sales category hierarchy.
1. On the Action Pane, select **Edit**. 
1. On the **Assign PKWiU code** FastTab, enter the PKWiU code for the sales category hierarchy. 

## Assign a PKWiU code to released products

To assign a PKWiU code to released products, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** \> **Common** \> **Released products**. 
1. Select the released product to assign a PKWiU code to.
1. On the Action Pane, select **Edit**. 
1. On the **Sell** FastTab, enter the PKWiU code for the released product. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
