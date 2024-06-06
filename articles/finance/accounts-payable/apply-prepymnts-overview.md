---
title: Automatically apply prepayments to vendor invoices
description: Learn about the capability for automatically applying prepayments to vendor invoices, which is created for purchase orders as parts of purchase agreements.
author: sunfzam
ms.author: shpandey
ms.topic: overview
ms.date: 10/19/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.23
---

# Automatically apply to vendor invoices

[!include [banner](../includes/banner.md)]

This article describes the capability for automatically applying prepayments to vendor invoices. A prepayment can be created for a purchase order as part of a purchase agreement. After a vendor invoice is received, the prepayment can be used to settle the accounts payable from the vendor invoice. The new feature enables the system to automatically use purchase order numbers on a vendor invoice to look up corresponding prepayments when the vendor invoice is imported.

If prepayments are found and can be applied, lines are added to the existing invoice lines to apply the prepayments. The prepayment lines are never considered during the invoice matching process.

The following points describe how prepayments are applied when different purchasing processes are followed:

- **One vendor invoice per purchase order** – The prepayment on the purchase order will be applied to the vendor invoice.
- **One vendor invoice for multiple purchase orders** – The prepayments on all purchase orders will be applied to the vendor invoice.
- **Multiple vendor invoices per purchase order** – The prepayment on the purchase order will be applied to the first imported vendor invoice. If the prepayment amount exceeds the invoice amount, prepayment application fails, and you must manually apply the prepayment.
- **Multiple vendor invoices for multiple purchase orders** – The prepayments on the purchase orders will be applied to the first relevant invoice. If the prepayment amount exceeds the invoice amount, prepayment application fails, and you must manually apply the prepayments. If any prepayments that remain after prepayments are applied to the first invoice, they can be applied to the invoices that follow.

If an attempt to apply a prepayment fails, the setting of the **Block follow-up automation process in case of prepayment application failure** option will determine next steps:

- **Yes** – The error message "Automatic application of prepayment: Failed" is added in the automation history, and the invoice remains in the list of pending vendor invoices. The invoice will remain blocked until you manually apply the prepayment.

To manually apply prepayments, go to the pending vendor invoice. On the **Invoice details** page, set the **Include in automated processing** option for the blocked invoice to **No**. You can now manually apply the prepayment. After the prepayment has been applied, set the **Include in automated processing** option back to **Yes** so that the invoice can be automatically processed.

You can also bypass automatic application of the prepayment by setting the **Include in automated processing** option to **No** and then setting it back to **Yes**. You'll receive the following message: "A prepayment already exists for the purchase order. Do you want to ignore it for selected vendor invoice?" Select **Yes**. The message "Application of prepayment bypassed manually" is added in the automation history, and the vendor invoice won't be blocked when the automated process runs again.

- **No** – Follow-up automation processes will continue. You can still apply the prepayment during settlement.
