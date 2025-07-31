---
title: GB-00002 Set up item sales tax groups for reverse charge VAT
description: Learn how to set up item sales tax groups and assign the default values to procurements categories subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/07/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: TaxItemGroup, DefaultDashboard, EcoResProductDetailsExtended, ProcCategoryHierarchyManagement
---

# GB-00002 Set up item sales tax groups for reverse charge VAT

[!include [banner](../../includes/banner.md)]

This article explains how to set up item sales tax groups and assign the default values to procurements categories subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.

The following procedure requires that the following sales tax codes are created for reverse charge purposes.  
    - REV17.5 - positive value
    - REV-17.5 - negative value

The walkthrough procedure uses the demo company GBSI.

To set up item sales tax groups for reverse charge VAT, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.
1. In the list, find and select the item sales tax group **RC-VAT**. On the Setup tab, you can add sales tax codes to this sales tax group.  Verify that the following sales tax codes exist for Reverse charge purposes:  REV17.5 – positive value  REV-17.5 – negative value  
1. Verify that the following sales tax codes are included in the **RC-VAT** item sales tax group for reverse charge purposes, and then close the form:
    - REV17.5 – positive value
    - REV-17.5 – negative value  
1. Go to **Product information management** \> **Products** \> **Released products**. On this form you'll assign the item sales tax group to the products that are subject to reverse charge.  
1. In the list, find and select item **S0012**.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Purchase** section.
1. Select **Edit**.
1. In the **Item sales tax group** field, select **RC-VAT** to open the lookup.
1. In the list, find and select **RC-VAT**. 
1. Expand or collapse the **Sell** section.
1. In the **Item sales tax group** field, select **RC-VAT** to open the lookup.
1. In the list, find and select **RC-VAT**. 
1. Select **Save**.
1. Close the form
1. In the list, find and select **S0020**.
1. In the list, select the link in the selected row.
1. In the Item sales tax group field, select **RC-VAT** to open the lookup.
1. In the list, select **RC-VAT** in the selected row.
1. In the **Item sales tax group** field, select **RC-VAT** to open the lookup.
1. In the list, select **RC-VAT** in the selected row.
1. Close the page.
1. Go to **Procurement and sourcing** \> **Procurement categories**. On this form you'll assign the item sales tax group to the categories that are subject to reverse charge.  
1. In the tree, expand **Expand the category tree and select a category**. 
1. Select **Cleaning**.
1. In the tree, select **Select a category**.
1. Select **Cleaning**. 
1. Expand or collapse the **Item sales tax groups** section.
1. In the **Item sales tax group** field, select **RC-VAT** to open the lookup.
1. In the list, select **RC-VAT** the selected row.  
1. Select **Save**.
1. Close the page.

> [!NOTE]
> The reverse charge should be set up for specific scenarios, including:
>
> - **Domestic reverse charge** - For example, the purchase of UK services, gold, computers chips, or mobile phones.
> - **European service purchase** - For the European goods (items) purchasing, you can activate **Use tax** on the sales tax group.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
