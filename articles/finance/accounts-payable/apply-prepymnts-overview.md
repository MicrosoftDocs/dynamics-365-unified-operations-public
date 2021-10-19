---
# required metadata

title: Apply prepayments to vendor invoices overview
description: This topic describes the capability for applying prepayments to vendor invoices automatically. 
author: abruer
ms.date: 08/25/2021
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


This topic describes the capability for applying prepayments to vendor invoices automatically. Prepayment can be created for purchase order as part of the purchase agreement. Once vendor invoice comes, the prepayment can be used to settle the account payable from vendor invoice. With this new feature, during vendor invoice importing, system will automatically use purchase order numbers on vendor invoice to look up corresponding prepayments.

If prepayments are found and can be applied, then besides the invoice lines, additional lines will be added for prepayment application. The additional prepayment lines are always excluded in matching process.

Accordng to different purchasing processes, there could be several scenarios

- **One vendor invoice for one purchase order**

The prepayment of the purchase order will be applied to vendor invoice.

- **One vendor invoice for multiple purchase orders**

Prepayments on all purchase orders will be applied to the single vendor invoice.

- **Multiple vendor invoices for one purchase order**

The prepayment for the single purchase order will be applied to the first imported vendor invoice. If the prepayment amount exceeds the invoice amount, prepayment application fails. User needs to manually apply the prepayemnt. 

- **Multiple vendor invoices for multiple purchase orders**

Prepayments for purchase orders will be applied for first relevant invoice. If prepayment amount exceedes the invoice amount, prepayment application fails. User needs to manually apply the prepayemnt. After prepayments are applied to first invoice, if there are still  remaining prepayments, they can be applied to following invoices.

In case of any automatic prepayment application failure, error message **"Automatic application of prepayment: Failed"** is inserted into the automation history. And depends on setting of the parameter **"Block follow-up automation process in case of prepayment application failure."** System can continue processing the invoice in follow-up automation processes, or block it until manual handling finished.

**The parameter is set as Yes** 

To manual handle the prepayment application, user needs to go to pending vendor invoice. In the invoice detail form, the toggle **'Include in automated processing'** is switched on. Switch it off to do manual editing, so prepayment can be applied manually. Or if you want to bypass the prepayment application, you can directly switch on the toggle 'Include in automated processing'. A popup screen will be shown: "A prepayment already exists for the purchase order. Do you want to ignore it for selected vendor invoice?" Confirm it, then a new status **Application of prepayment bypassed manually** will be inserted in the automation history. And the vendor invoice will not be blocked for follow-up automation processes.

**The parameter is set as No** 

Follow-up automation processes will continue even application of prepayment fails. User can still have chance to apply the prepayment via settlement.
