---
# required metadata

title: Set up and use PKWiU codes for Poland
description: This topic walks you through setting up the PKWiU code for Poland.  
author: ShylaThompson
ms.date: 09/20/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Poland
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Set up and use PKWiU codes for Poland

[!include [banner](../includes/banner.md)]

The PKWiU code is used for tax purposes to categorize goods and services sold in Poland. It is included on all sales order invoices, free text invoices, and invoices posted from the Project module. You can view the PKWiU code in the project invoice and print the project invoice by using the **Invoice journals** form. You can also set up notifications for when a PKWiU code is missing from an invoice.

To ensure that users include a PKWiU code on all invoices, select one of the following options in the **PKWiU code requirement** field on the **Accounts receivable parameters** page: 
- **None** – Do not display a message when a PKWiU code is missing from a sales order or a free text invoice. The PKWiU code is not required for invoices. 
- **Warning** – Display a message when you invoice a sales order or a free text invoice that is missing the PKWiU code. 
- **Error** – Display a message when you invoice a sales order or a free text invoice that is missing the PKWiU code and stop the invoice from being processed. 

## Assign a PKWiU code to the sales category hierarchy

Category hierarchies are used to classify products or transactions for reporting and analysis. The category hierarchy that is of the Sales category hierarchy type is used for organizing products for sales activities. You can assign a PKWiU code to the sales category hierarchy so that the PKWiU code is included on invoices that include non-inventoried items. 

1. Click **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**. 
2. Select the sales category hierarchy. On the Action Pane, click **Edit**. 
3. On the **Assign PKWiU code** FastTab, enter the PKWiU code for the sales category hierarchy. 

## Assign a PKWiU code to released products

1. Click **Product information management** > **Common** > **Released products**. 
2. Select the released product to assign a PKWiU code to. On the Action Pane, click **Edit**. 
3. On the **Sell** FastTab, enter the PKWiU code for the released product. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]