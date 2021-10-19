---
# required metadata

title: Apply prepayments to vendor invoices overview
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

# Apply prepayments to vendor invoices overview

[!include [banner](../includes/banner.md)]

This topic describes the capability for applying prepayments to vendor invoices automatically. Prepayment can be created for purchase order as part of a purchase agreement. Once vendor invoice comes, the prepayment can be used to settle the account payable from vendor invoice. With this new feature, system will automatically use purchase order numbers on a vendor invoice to look up corresponding prepayments when the vendor invoice is imported.

If prepayments are found and can be applied, then additional lines (in addition to the existing invoice lines,) will be added to apply the prepayment. The additional prepayment lines are never considered during the invoice matching process.

The following points describe how prepayments are applied when different purchasing processes are followed. 

- **One vendor invoice for one purchase order** - The prepayment of the purchase order will be applied to the vendor invoice.

- **One vendor invoice for multiple purchase orders** - Prepayments on all purchase orders will be applied to the single vendor invoice.

- **Multiple vendor invoices for one purchase order** - The prepayment for the single purchase order will be applied to the first imported vendor invoice. If the prepayment amount exceeds the invoice amount, prepayment application fails. User needs to manually apply the prepayemnt. 

- **Multiple vendor invoices for multiple purchase orders** - Prepayments for purchase orders will be applied for first relevant invoice. If the prepayment amount exceedes the invoice amount, prepayment application fails. User needs to manually apply the prepayemnt. After prepayments are applied to first invoice, if there are still remaining prepayments, they can be applied to following invoices.

If the system tries to apply a prepayment and the application fails, you'll receive the error message **"Automatic application of prepayment: Failed"** is inserted into the automation history. The message is inserted if the **Block follow-up automation process in case of prepayment application failure** the parameter is set to **Yes**. The system can continue processing the invoice when the automation process is run subsequently, or block it until the prepayment is applied manually.

### The Automatically apply prepayment for imported invoices parameter is set to Yes 

To apply prepayments manually, go to the pending vendor invoice. On the **Invoice detail** page, set the **Include in automated processing** is set to **Yes**. Change the setting to **No** to allow the prepayment to be applied manually. 

To bypass the prepayment application, you can directly set the **Include in automated processing** field to **No**. A message will display with the message: **A prepayment already exists for the purchase order. Do you want to ignore it for selected vendor invoice?** Select **Yes**. A new status **Application of prepayment bypassed manually** will be inserted into the automation history. And the vendor invoice will not be blocked for follow-up automation processes.

### The Automatically apply prepayment for imported invoices parameter is set to No 

Follow-up automation processes will continue, even if application of the prepayment has failed. YOu can still apply the prepayment during settlement.
