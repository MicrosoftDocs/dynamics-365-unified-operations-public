---
title: Set up withholding tax authorities for the TDS tax type
description: Learn how to set up Tax Deducted at Source (TDS) authorities, including a step-by-step process on setting up TDS authorities.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Set up withholding tax authorities for the TDS tax type

[!include [banner](../../includes/banner.md)]

This article explains how to set up Tax Deducted at Source (TDS) authorities.

1. Go to **Tax \> Indirect taxes \> Withholding tax authorities**.

    [![Withholding tax authorities page.](../media/apac-ind-TDS-12.png)]

2. In the **Tax type** field, select **TDS** to set up withholding tax authorities for the TDS tax type.
3. On the Action Pane, select **New** to create a line.
4. In the **Withholding tax authority** field, enter a name for the TDS authority.
5. In the **Description** field, enter a description.
6. On the **General** FastTab, in the **Vendor account** field, select the vendor account for the TDS authority.

    > [!NOTE]
    > You must define the name of the bank where funds that are owed to the TDS authority vendor will be deposited. The bank's name is defined on the **Bank accounts** page (**Accounts payable \> All vendors \> Vendor \> Set up \> Bank accounts**).

7. Close the page.
