---
title: Correct a free text invoice
description: Learn how to correct a free text invoice that has been posted and reissue it as a corrected invoice, including definitions for different invoice types.
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustFreeInvoice
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 2a0a4789-8619-4974-bef9-0923cc848420
---

# Correct a free text invoice

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to correct a free text invoice that you already posted and reissue it as a corrected invoice.

To correct a free text invoice that you already posted:

1. Open the posted free text invoice.
1. On the **Invoice** page, select **Cancel**, and then select **Correct invoice**.
1. Select a reason code, add comments, and select the date for new corrected invoice.
1. Modify the corrected invoice, and post it.

When you post the corrected invoice, a canceling invoice is created for a credit amount that equals the original invoice amount. Therefore, the combined balance of the original invoice and the canceling invoice is 0 (zero). The canceling invoice is settled against the original invoice.

After you post the corrected invoice, you will have three invoices:

- **Original invoice** – The invoice that includes the information that you're correcting.
- **Canceling invoice** – The system-generated credit invoice that the system creates to cancel the invoice that was most recently corrected.
- **Corrected invoice** – The invoice that contains the corrected invoice information.

You can identify canceling and correcting invoices in two ways:

- The **All free text invoices** page includes a **Correction** column, where you can see which invoices are canceling invoices and corrected invoices.
- The header of the free text invoice shows a status of **Cancelling invoice '\[invoice number\]'** or **Corrected invoice '\[invoice number\]'**.

> [!NOTE]
> This feature is available only if the **Free text invoice correction** configuration key is selected. For more information about how to enable configuration keys, see the **Enable (or disable) configuration keys** section in the [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md) article.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
