---
title: Create configuration providers and mark them as active
description: This article explains how a user assigned to the System Administrator or Electronic Reporting Developer role can create a configuration provider.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERVendorPart, ERVendorTable
---

# Create configuration providers and mark them as active

[!include [banner](../../includes/banner.md)]

This article explains how a user assigned to the System Administrator or Electronic Reporting Developer role can create a configuration provider for Electronic reporting (ER). Each ER configuration refers to the provider as the author of the configuration. In this example, you create a configuration provider for sample company, Litware, Inc. You can perform these steps in any company because ER configuration providers are shared among all companies.

## Create a provider

1. Go to the **navigation pane** in the upper left corner and select **Organization administration**.
1. Go to **Workspaces > Electronic reporting**.
1. Go to **Related links > Configuration providers**.
1. Select **New**.
    - A provider record has a unique name and URL. Review the content of this page and skip this procedure if a record for Litware, Inc. (<https://www.litware.com>) already exists.  
1. In the Name field, type `Litware, Inc.`.
1. In the Internet address field, type `https://www.litware.com`.
1. Select **Save**.
1. Close the page.

## Select as an active provider

1. Select the Litware, Inc. provider.
1. Select **Set active**.

:::image type="content" source="../media/GER-Task-ActiveProvider-1.png" alt-text="Screenshot of the Electronic reporting workspace page.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
