---
title: GB-00002 Set up sales tax groups for reverse charge VAT
description: Learn how to set up reverse charge sales tax groups for purchasing and sales purposes for the United Kingdom in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/04/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: TaxGroup
---

# GB-00002 Set up sales tax groups for reverse charge VAT

[!include [banner](../../includes/banner.md)]

This article explains how to set up reverse charge sales tax groups for purchasing and sales purposes for the United Kingdom in Microsoft Dynamics 365 Finance.

The following procedure shows how to create a new sales tax group that contain a **+ve** sales tax code. The sales tax group **RC-VAT** should already contain both **+ve** and **-ve** sales tax codes.

The procedure requires that the following sales tax codes are created for reverse charge purposes.  
- REV17.5 – positive value
- REV-17.5 – negative value

The procedure uses the demo company GBSI.

To set up sales tax groups for reverse charge VAT, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax groups**.
1. In the list, find and select **RC-VAT**.  
1. Expand or collapse the **Setup** section.
1. Verify that the following sales tax codes exist for reverse charge purposes:
    - REV17.5 – positive value
    - REV-17.5 – negative value    
1. In the list, find and select the **REV-17.5** sales tax code. This sales tax code must have a negative value.  
1. Select **Edit**.
1. Select the **Reverse charge** checkbox.
1. Select **Save**.
1. Select **New**.
1. In the **Sales tax group** field, enter "RC-VAT-AR".  
1. In the **Description** field, enter "Reverse charge VAT sales".  
1. Select **Add**.
1. In the **Sales tax code** field, select the drop-down button to open the lookup.
1. In the list, find and select the sales tax code **REV17.5** (positive value).
1. In the list, select the link in the selected row.
1. Select the **Exempt** checkbox.
1. Select the **Reverse charge** checkbox.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
