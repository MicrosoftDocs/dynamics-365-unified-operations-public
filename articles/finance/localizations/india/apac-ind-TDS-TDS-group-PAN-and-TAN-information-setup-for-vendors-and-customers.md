---
title: Set up TDS group, PAN, and TAN information for vendors and customers
description: Learn how to set up information about the Tax Deducted at Source (TDS) group, permanent account number (PAN), and tax account number (TAN) for vendors.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# TDS group, PAN, and TAN information setup for vendors and customers

[!include [banner](../../includes/banner.md)]

This article explains how to set up information about the Tax Deducted at Source (TDS) group, permanent account number (PAN), and tax account number (TAN) for vendors and customers.

1. Go to **Accounts payable \> Vendors \> All vendors** or **Accounts receivable \> Customers \> All customers**.

    :::image type="content" source="../media/apac-ind-TDS-55.png" alt-text="Screenshot of the All vendors page.":::

1. On the Action Pane, select **New** to create a vendor or customer, and enter the required details. Alternatively, select an existing vendor or customer.
1. On the **Invoice and delivery** FastTab, in the **Withholding tax** section, set the **Calculate withholding tax** option to **Yes** to calculate withholding tax, TDS, or Tax Collected at Source (TCS) for the vendor or customer.
1. TDS for a purchase invoice is calculated based on the default TDS group that is defined for the vendor or customer. In the **TDS group** field, select the default TDS group.

    > [!NOTE]
    > When you select a TDS group in the **TDS group** field, the **Withholding tax group** and **TCS group** fields become unavailable.

1. On the **Tax information** FastTab, in the **PAN information** section, in the **Status** field, select the status of the permanent account number for the vendor or customer:

    - **Not available** – The vendor or customer doesn't have a PAN.
    - **Received** – The vendor or customer has a PAN.
    - **Applied** – The vendor or customer has applied for a PAN.
    - **Invalid** – The vendor or customer has a PAN, but it isn't valid.

1. If you selected **Received** in the **Status** field to indicate that the vendor or customer has a PAN, enter the PAN in the **Number** field. The PAN must consist of five alphabetic characters, then four numeric characters, and then one alphabetic character. Here is an example: **ABCDE1260A**.
1. If you selected **Applied** in the **Status** field to indicate that the vendor or customer has applied for PAN, enter the reference number in the **Reference number** field.
1. In the **Nature of assessee** field, select the nature of assessee category that the vendor or customer belongs to:

    - Company
    - HUF
    - Firm
    - Individual
    - AOP
    - BOI
    - Local authority
    - Others

    :::image type="content" source="../media/apac-ind-TDS-56.png" alt-text="Screenshot of the Tax information FastTab.":::

1. On the Action Pane, on the **Vendor** tab, in the **Registration** group, select **Registration IDs** to open the **Manage addresses** page.
1. On the **Manage addresses** page, on the **Tax information** FastTab, select **Add** or **Edit** to open the **Manage tax information** page, where you can maintain the tax registration entry.
1. On the **Manage tax information** page, on the **Withholding tax** FastTab, in the **Tax Account Number (TAN)** field, enter the TAN. The TAN must consist of four alphabetic characters, then five numeric characters, and then one alphabetic character. Here is an example: **AFGH54821T**.
1. Close the page.
