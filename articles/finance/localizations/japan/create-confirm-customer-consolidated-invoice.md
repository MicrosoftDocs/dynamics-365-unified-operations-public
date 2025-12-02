--- 
title: Create and confirm a customer consolidated invoice
description: Learn how to consolidate customer invoices each month to calculate the due amount in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/18/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustConsInvoice_JP  
---

# Create and confirm a customer consolidated invoice

[!include [banner](../../includes/banner.md)]

This article explains how to consolidate customer invoices each month to calculate the due amount in Japan with Microsoft Dynamics 365 Finance.

In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 

To complete the following procedure, the sales or purchase invoices should have been posted before running this task. The procedure uses the JPMF demo company data.

To create and confirm a customer consolidated invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. Select **New**.
    - The default execution date is the session date.  
    - If you want to override the consolidation date, set the **Use consolidation date specified below** slider to **Yes**. For example, when the consolidation date is specified as the 25th, you can run the consolidation on the 24th if you set the slider to **Yes**. You must manually specify a consolidation date.  
1. Select **OK**.
    - Verify that the consolidated invoice was generated.  
    - One consolidated invoice contains only one customer account. When there are multiple customer accounts to be consolidated, multiple consolidated invoices are generated.  
1. In the list, select the link in the selected row.
    - To switch to the detail view of the **Consolidated invoice** page, in the grid select the consolidation ID of the consolidated invoice.  
    - Verify that invoiced sales orders are included in the consolidated invoice.  
1. Select **Confirm**. The status of the consolidated invoice changes to **Confirmed**. When confirmed, the consolidated invoice is locked and you can't edit it.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
