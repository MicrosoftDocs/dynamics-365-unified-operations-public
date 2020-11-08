---
# required metadata

title: What's new or changed for India GST Localization in 10.0.13 (October 2020)
description: This topic describes new or changed functionality for India GST features released in Dynamics 365 Finance version 10.0.14.
author: prabhatb
manager: annbe
ms.date: 25/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.14

---

# What's new or changed for India GST Localization in 10.0.14 (Oct 2020)

[!include [banner](../includes/banner.md)]

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.14 for India GST localization. 

## New features

No new feature was released in version 10.0.14 

## Critical Fixes :- 

 **KB 4571303**- adjusting withholding tax cannot work because of using role has been assigned to specified legal entity : User manually adjust and apply the tax amount of India TDS withholding tax in a vendor invoice journal. observed the adjustment is lost (reset) if user change the Invoice number in the journal before posting. After this fix Withholding tax adjustment will remain even after user make any change in the invoice Journal  

 

**KB- 4572378** - After enabling the India localization, the milestone details were not displaying on the Project contract form :-Billing Rule Details is displaying empty for Existing Entries when India localization Tax Extension is Turned On. After this fix on enablement of India localization billing rule and mile stone details will display for existing entries as well. 

 

**KB- 4574866** - GST amount not showing correctly in the Purchase requisition > Total form when Purchase requisition created foreign currency :- GST amount not showing correctly. GST amount showing in foreign currency whereas Subtotal and Total amount showing in INR. Actually, GST amount should be converted and added to the subtotal to display correct total amount. In case Purchase requisition ,line is created in foreign currency the tax amount should be converted and added to subtotal to display correct total amount under  Summary > ‘Total ‘to review Tax amount 

## Upcoming critical fixes in 10.0.15 :-  

- GST Challan details is not getting updated and throwing a warning “the bank reference number constraint must be between 17 and 20 digits” 
