---
title: Acquire and dispose a CIAP fixed asset
description: This article describes how to acquire and dispose of a CIAP fixed asset in Brazil with Microsoft Dynamics 365 Finance.
author: v-gonode
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-06-30
---

# Acquire and dispose a CIAP fixed asset

[!include [banner](../../includes/banner.md)]

This article describes how to acquire and dispose of a CIAP fixed asset in Brazil with Microsoft Dynamics 365 Finance.

Fiscal books can acquire and dispose of fixed assets that are ICMS tax long-term return.

## Acquire a CIAP fixed asset

Use this functionality to register in Fiscal books module the acquisition of a fixed asset controlled by the ICMS tax long term return.

To acquire a CIAP fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **All purchase orders**.
1. In the **Vendor account** field, select a vendor.
1. Select **Add line**.
1. In the **Item number** field, enter a value.
1. In the **CFOP** field, enter a value.
1. In the **Quantity** field, enter a value.
1. In the **Unit price** field, enter a value.
1. Expand the **Line details** section.
1. Select the **Fixed assets** tab.
1. In the **New fixed asset?** field, select **Yes**.
1. In the **Fixed asset group** field, select a fixed asset group.
1. Select the **Financial dimensions** tab.
1. In the **CostCenter** field, enter a value.
1. In the **Filial** field, enter a value.
1. Select **Confirm**.
1. Go to **All purchase orders**
1. Select a purchase order link.
1. On the Action Pane, select **Invoice**.
1. Select **Default from: Product receipt quantity**.
1. In the **Default quantity for lines** field, select a quantity.
1. Select **OK**.
1. In the **Document model** field, enter a value.
1. In the **Access key** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. In the **Posting date** field, enter a date.
1. Select **Post**.
1. Go to **Booking period**.
1. Select **Create new booking period**.
1. In the **Fiscal establishment** field, enter a value.
1. In the **Month** field, enter a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Select **ICMS**.
1. Select **ICMS tax assessment**.
1. Select **OK**.
1. Go to **All CIAP fixed assets**.
1. Select a CIAP asset ID link.
1. Expand the **Line details** section.
1. Go to **CIAP Report**.
1. In the **Fiscal establishment** field, enter a value.
1. Select **OK**.

## Dispose of a CIAP fixed asset

Use this functionality to register the disposal of a fixed asset controlled by the ICMS tax long term return in the Fiscal books module.

To acquire a CIAP fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **All free text invoices**.
1. Select **New**.
1. In the **Fiscal establishment ID**, **Customer account**, **Date**, **Description**, **Main account**, **CFOP**, **Sales tax group**, **Item sales tax group**, **Quantity, and **Unit price** field, enter a value.
1. In the **Fiscal establishment ID** field, enter a value.
1. In the **Customer account** field, enter a value.
1. In the **Date** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter a value.
1. In the **CFOP** field, enter a value.
1. In the **Sales tax group** field, enter a value.
1. In the **Item sales tax group** field, enter a value.
1. In the **Quantity** field, enter a value.
1. In the **Unit price** field, enter a value.
1. Expand the **Line details** section.
1. In the **Fixed asset number** field, enter a value.
1. Select **Post**.
1. Expand the **Bill of lading** section.
1. In the **Carrier name** field, enter a value.
1. In the **Volume type** field, enter a value.
1. In the **Volume quantity** field, enter a value.
1. In the **Net weight** field, enter a value.
1. In the **Gross weight** field, enter a value.
1. Select **OK**.
1. Go to **Export/import NF-e process**.
1. Select **OK**.
1. Go to **Booking period \> Create new booking period**.
1. In the **Fiscal establishment** field, enter a value.
1. In the **Month** field, enter a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Select **ICMS**.
1. Select **ICMS tax assessment**.
1. Select **OK**.
1. Go to **All CIAP fixed assets**.
1. Select a CIAP asset ID link.
1. Go to **CIAP Report**.
1. In the **Fiscal establishment** field, enter a value.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
