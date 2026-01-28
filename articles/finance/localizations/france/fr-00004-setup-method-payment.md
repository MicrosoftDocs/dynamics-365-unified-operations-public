--- 
title: FR-00004 Set up methods of payment
description: Learn how to set up methods of payment so you can create and post the bill of exchange after approving it from the draw bill of exchange journal in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2016-06-30
ms.search.form: CustPaymMode, CustVendPaymFormat 
---

# FR-00004 Set up methods of payment

[!include [banner](../../includes/banner.md)]

This article explains how to set up methods of payment so you can create and post the bill of exchange after approving it from the draw bill of exchange journal in Microsoft Dynamics 365 Finance.

The following procedure was created using the demo data company FRSI. 

The functionality described is available for legal entities whose primary address is in France. To perform this procedure you should have a role of Accounts receivables manager.

To set up methods of payment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments setup \> Methods of payment**.
1. Select **New**.
1. In the **Method of payment** field, enter a value.
4. In the **Description** field, enter a value.
1. In the **Payment status** field, select **Approved**.
1. In the **Payment type** field, select **Bill of exchange**.
1. Expand or collapse the **General** section.
1. In the **Account type** field, select **Bank**.
1. In the **Payment account** field, enter a value. For example, enter "FRSI OPER".  
1. Expand or collapse the **File formats** section.
1. Select **Setup**.
1. In the list, find and select **French bill of exchange**, and then use the arrow to move it to the **Selected** list.  
1. Select **Save**.
1. Close the page.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select **EnmmEAR**. 
1. In the **Export format** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select **French bill of exchange**.  
1. Select or clear the **Create and post draw journal automatically when posting invoices** checkbox.
1. Select or clear the **Run export script** checkbox.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
