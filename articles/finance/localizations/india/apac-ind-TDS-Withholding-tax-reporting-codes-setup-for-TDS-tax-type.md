---
title: Set up withholding tax reporting codes for the TDS tax type
description: Learn how to set up withholding tax reporting codes steps so that you can set up Tax Deducted at Source (TDS) reporting codes.
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

# Set up withholding tax reporting codes for the TDS tax type

[!include [banner](../../includes/banner.md)]

Withholding tax reporting codes are used to generate Form 26Q and Form 27Q statements for Tax Deducted at Source (TDS). This article explains how to set up withholding tax reporting codes steps so that you can set up TDS reporting codes.

1. Go to **Tax \> Setup \> Withholding tax \> Withholding tax reporting codes**.

    :::image type="content" source="../media/apac-ind-TDS-16.png" alt-text="Screenshot of the Withholding tax reporting codes page.":::

1. In the **Tax type** field, select **TDS** to define withholding tax reporting codes for the TDS tax type.
1. In the **Withholding tax component** field, select the TDS component to that you're defining the withholding tax reporting code for. The **Withholding tax component group** field shows the TDS component group that was defined for the TDS component that you're defining.

    The **Section code** field on the **General** FastTab shows the section code that is attached to the TDS component group.

1. On the **General** FastTab, in the **Reporting code** field, select the TDS reporting code:

    - TDS
    - TCS
    - Surcharge
    - PE\_Cess
    - SHE\_Cess

1. Close the page.
