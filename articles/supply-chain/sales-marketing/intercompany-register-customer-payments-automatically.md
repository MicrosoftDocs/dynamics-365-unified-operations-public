---
title: Register payments automatically for intercompany customer invoices
description: Learn how to register payments automatically for intercompany customer invoices, including a step-by-step process for registering payments.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Register payments automatically for intercompany customer invoices

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management creates a customer transaction when an intercompany customer invoice is posted. This customer transaction remains open until it is settled, which means that it has been paid. When the corresponding intercompany purchase order is invoice updated, a vendor transaction matching the customer transaction is created. This vendor transaction also remains open until it is settled. To reduce the risk of differences, an accounts receivable payment journal can be automatically created and posted when the accounts payable payment journal is posted.

1. Go to **Sales and marketing \> Customers \> All customers**.
1. On the Action Pane, on the **General** tab, select **Intercompany**.
1. To set up the intercompany accounts receivable payments on the **Intercompany** page for sales orders, select the **Sales order policies** link.
1. In the **Payment journal** field, select the accounts receivable payment journal that you want to register intercompany vendor payments to. You set this up on the **Accounts receivable parameters** page.
1. If you want to post to this journal automatically, select the **Post journal automatically** check box.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
