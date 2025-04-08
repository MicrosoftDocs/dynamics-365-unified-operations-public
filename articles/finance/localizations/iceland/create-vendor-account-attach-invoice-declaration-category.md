--- 
title: Create a vendor account and attach the invoice declaration category
description: Learn how to create a vendor with configuration for an invoice declaration in Microsoft Dynamics 365 Finance. 
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: Iceland
ms.search.validFrom: 2016-06-30
ms.search.form: VendTable, DirPartyLookup
---

# Create a vendor account and attach the invoice declaration category

[!include [banner](../../includes/banner.md)]

This article explains how to create a vendor with configuration for an invoice declaration in Microsoft Dynamics 365 Finance.

The following procedures show you how to create a vendor with configuration for an invoice declaration. The demo data company used to create these procedures is DEMF with the country/region of legal entity primary address updated to Iceland.

## Create a vendor

To create a vendor, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. Select **New**.
1. In the **Vendor accoun** field, enter "IS-001".
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Select**.
1. In the **Group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.

## Set the invoice declaration category for the vendor

To set the invoice declaration category for the vendor, follow these steps.

1. Expand or collapse the **Invoice and delivery** section.
1. In the **Invoice declaration** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
