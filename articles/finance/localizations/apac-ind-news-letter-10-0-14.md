---
# required metadata

title: What's new or changed for India GST in 10.0.14 (October 2020)
description: This topic describes new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.14.
author: prabhatb
ms.date: 11/18/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.14

---

# What's new or changed for India GST in 10.0.14 (October 2020)

[!include [banner](../includes/banner.md)]

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.14 for India GST localization. 

## New features

No new features were released in version 10.0.14. 

## Critical fixes 

 **KB 4571303**: Adjusting withholding tax doesn't work because the role has been assigned to a specified legal entity. When you manually adjust and apply the tax amount of India TDS withholding tax in a vendor invoice journal, the adjustment is lost or reset, if the invoice number is changed in the journal before posting. After this fix, the withholding tax adjustment will remain even after changes are made in the invoice journal.

**KB- 4572378**: After you enable India localization, the milestone details aren't showing on the **Project contract** page. When you enable the India localization tax extension, the **Billing rule** details are empty for existing entries. After this fix, milestone details and billing rules are shown for existing entries. 

**KB- 4574866**: The GST amount isn't showing correctly in the **Total** page for a purchase requisition that is created with a foreign currency. The GST amount is shown in the foreign currency, and the subtotal and total amount are shown in INR. The GST amount should be converted and added to the subtotal to display the correct total amount. For a Purchase requisition, the line is created in the foreign currency and the tax amount should be converted and added to the subtotal to display the correct total amount.

## Upcoming critical fixes in 10.0.15 

- GST Challan details aren't updating. Instead, the following warning appears, “The bank reference number constraint must be between 17 and 20 digits”.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]