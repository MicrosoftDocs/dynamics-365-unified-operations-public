---
# required metadata

title: Automatically apply prepayments to vendor invoices overview
description: This topic describes the capability for applying prepayments to vendor invoices automatically. 
author: sunfzam
ms.date: 10/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.23

---

# Automatically apply to vendor invoices overview

[!include [banner](../includes/banner.md)]

This topic describes the capability for applying prepayments to vendor invoices automatically. Prepayment can be created for purchase order as part of a purchase agreement. Once vendor invoice comes, the prepayment can be used to settle the account payable from vendor invoice. With this new feature, the system will automatically use purchase order numbers on a vendor invoice to look up corresponding prepayments when the vendor invoice is imported.

If prepayments are found and can be applied, then additional lines (in addition to the existing invoice lines) will be added to apply the prepayment. The prepayment lines are never considered during the invoice matching process.

The following points describe how prepayments are applied when different purchasing processes are followed. 

- **One vendor invoice for one purchase order** - The prepayment of the purchase order will be applied to the vendor invoice.

- **One vendor invoice for multiple purchase orders** - Prepayments on all purchase orders will be applied to the single vendor invoice.

- **Multiple vendor invoices for one purchase order** - The prepayment for the single purchase order will be applied to the first imported vendor invoice. If the prepayment amount exceeds the invoice amount, prepayment application will fail. You'll need to apply the prepayment manually. 

- **Multiple vendor invoices for multiple purchase orders** - Prepayments for purchase orders will be applied for first relevant invoice. If the prepayment amount exceeds the invoice amount, prepayment application fails. You must apply the prepayment manually. If some prepayments remain after prepayments have been applied to the first invoice, they can be applied to the invoices that follow.

- The **Block follow-up automation process in case of prepayment application failure** parameter is set to No 

   If the system tries to apply a prepayment and the application fails, the error message **"Automatic application of prepayment: Failed"** will be inserted into the automation history. The invoice will remain in the list of pending vendor invoices. When the **Block follow-up automation process in case of prepayment application failure** parameter is set to Yes, the invoice will be blocked until you apply the prepayment manually. 

     To apply prepayments manually, go to the pending vendor invoice. On the **Invoice details** page, set the **Include in automated processing** option for the blocked invoice to **No**. Changing the setting for this option lets you apply the prepayment manually. When the prepayment has been applied, set the **Include in automated processing** option back to **Yes** to allow the invoice to be processed automatically. 

   You can also bypass the automatic application of the prepayment. To do so, set the **Include in automated processing** field to **No** and then switch it back to **Yes**. The message: **A prepayment already exists for the purchase order. Do you want to ignore it for selected vendor invoice?** will be displayed. Select **Yes**. A new status, **Application of prepayment bypassed manually**, will be inserted into the automation history. Now the vendor invoice won't be blocked when the automated process runs again.

- The **Block follow-up automation process in case of prepayment application failure** parameter is set to No 

   Follow-up automation processes will continue, even if application of the prepayment has failed. You can still apply the prepayment during settlement.
