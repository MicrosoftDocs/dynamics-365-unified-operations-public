---
title: AX 2009 migration - Generate maps
description: Learn about how to generate data maps to migrate data from Microsoft Dynamics AX 2009 to finance and operations.
author: pnghub
ms.author: priysharma
ms.topic: how-to
ms.date: 06/30/2018
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Generate maps

[!include [banner](../includes/banner.md)]

Before you can migrate your data from Microsoft Dynamics AX 2009 to finance and operations, you must align your source data with your target environment. This article explains how to generate source-to-target mappings.

Before you can generate maps, you must provide the target URL, tenant URL, and service app ID to validate the connection.

> [!NOTE]
> When you create a new app under Microsoft Microsoft Entra ID in the Azure portal, you have two options, **Web API** and **Native**. Select **Native**, and grant permissions to the native Microsoft Entra app.

## Prerequisites
Before you generate the data maps between the source and target environments, you must install the Data migration tool (DMT). For more information, see [AX 2009 migration - Install the Data migration tool](install-dmt.md).

## Generate maps
Follow these steps to generate maps for data migration.

1. In AX 2009, in the navigation pane, go to **Data migration** \> **Setup** \> **Configure connections**.
2. Review the field information to verify that it's correct, and then click **Validate**.
3. After the validation is completed, close the form.
4. Under **Setup**, click **Configure and generate maps**.
5. Verify that the information in the form is correct, and then click **Validate path**.
6. After validation is completed, click **Generate maps**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
