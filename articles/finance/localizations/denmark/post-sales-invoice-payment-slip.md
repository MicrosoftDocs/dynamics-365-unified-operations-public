--- 
title: Post a sales invoice with a payment slip
description: Learn how to post a free text invoice with a payment slip attachment in a specified format in Denmark with Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak  
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines  
ms.custom: 
  - bap-template
---

# Post a sales invoice with a payment slip

[!include [banner](../../includes/banner.md)]

This article describes how to post a free text invoice with a payment slip attachment in a specified format in Denmark by using Microsoft Dynamics 365 Finance.

The following procedure shows you how to post a free text invoice with a payment slip attachment in a specified format. The payment slip prints with the creditor identification number and invoice number to identify the payment. This procedure was created by using the demo data company DEMF. This functionality is available for legal entities whose primary address is in Denmark.

Before you can complete this procedure, you must first set up payment slip formats and payment slips for customer invoices. 

To post a sales invoice with a payment slip, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. Set up the associated payment attachment in customer invoice for the selected customer first.  
1. Select the link in the selected row.
1. In the **Currency** field, select the drop-down button to open the lookup. You can only print the payment slip for sales orders with the Danish kroner (DKK) currency.  
1. In the list, find and select the desired record.
1. Select the link in the selected row.
1. Select **OK**.
1. Mark the selected row.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. Select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **OK**. Ensure that the associated payment that you attach to the customer invoice is set to "FIK 751" or "FIK 752".  
1. Select **Yes**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
