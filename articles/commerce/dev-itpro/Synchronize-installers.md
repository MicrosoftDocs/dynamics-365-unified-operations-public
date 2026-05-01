---
title: Synchronize self-service installers in Dynamics 365 Commerce
description: Learn how to upload and synchronize self-service installers in Microsoft Dynamics 365 Commerce so that they can be used with the standard self-service download mechanism.
author: jashanno
ms.date: 02/20/2026
ms.topic: how-to
ms.search.form: SysMicrosoft Entra IDClientTable, RetailTransactionServiceProfile
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-04-30
ms.custom: 
  - bap-template
---

# Synchronize self-service installers in Dynamics 365 Commerce

[!include [banner](../../includes/banner.md)]

This article explains how to upload and synchronize self-service installers in Microsoft Dynamics 365 Commerce so that you can use them by using the standard self-service download mechanism.

Use the Asset library and Shared asset library in Microsoft Dynamics Lifecycle Services (LCS), and Microsoft Dynamics 365 Commerce headquarters to upload and synchronize self-service installers so that you can use them by using the standard self-service download mechanism. This functionality applies only to environments that Microsoft continuously manages. For other environments, such as on-premises environments or virtual hard disks (VHDs), download and use the installers directly from LCS, where they're currently published.

> [!IMPORTANT]
> The earlier method of uploading self-service packages is currently still supported. However, it's obsolete and will be removed in the future. It's recommended that you retrieve self-service packages from Lifecycle Services (LCS) instead. You can generate configuration files as needed, per standard steps.

The **Retail Self-service package** subsection in the **Shared asset library** stores all monthly releases for self-service installers. These installers include the Store Commerce app, Commerce Scale Unit, and hardware station. You can also upload customized installers into both this library and the project-level asset library. By using these locations, you can then synchronize the available installers in Commerce headquarters. After synchronization is complete, all the installers that are available between these two libraries (and whatever previously existed in the environment) are accessible for the standard self-service download processes that are described in detail in separate articles (see [Key terms](#key-terms)).

The following illustration shows a generic example of the **Retail Self-service package** subsection in the Shared asset library (or Asset library).

:::image type="content" source="media/SharedAssets.jpg" alt-text="Screenshot of the Retail Self-service package subsection in the Shared asset library.":::

## Key terms

| Term | Description |
|---|---|
| Shared asset library | In LCS, two types of asset libraries are available: the Shared asset library and the project-level Asset library. For more information about these libraries, see [Asset library in Lifecycle Services (LCS)](../../fin-ops-core/dev-itpro/lifecycle-services/asset-library.md). |
| Asset library | For more information, see [Asset library in Lifecycle Services (LCS)](../../fin-ops-core/dev-itpro/lifecycle-services/asset-library.md). |
| Self-service installers | Self-service installers are the Dynamics 365 Commerce components. For more information about the installers, see the links at the end of this article. |

## Upload or modify the self-service installer packages

When you view the **Retail Self-service package files** subsection in the **Shared asset library**, you see listings that include what Microsoft publishes and anything that project owners and users upload. Regardless of who uploads the package file (Microsoft or a user), you can edit the file to add extra details. At the top of the package listings, you see buttons. The first button is the **Upload** button, the second is the **Delete** button, and the third is the **Edit** button. By using the **Upload** button, you can upload a customized package or custom installer or file that you need for that particular project. Regardless of how you upload the file, you can select any package and use the **Edit** button to change the friendly name and add an informational description to the file. The legacy self-service installer packages that Microsoft uploads or that a project user or developer customizes and uploads can be easier to read, understand, and detail by adding a useful description. When you synchronize the installers, you can more easily view, understand, and use the installers.

## Synchronize installers in Dynamics 365 headquarters

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Channel deployment** tab, select **Check for package updates** to perform synchronization. The process synchronizes and updates the installers that are available for download through standard self-service processes, depending on which of the installers currently available in LCS apply to your environment.

    > [!IMPORTANT]
    > - Previously, the system used the RetailSelfService table as the source for all installer information. You entered information in this table based on the installers that you uploaded into headquarters through the earlier package application method. The new self-service population methodology combines all values in the RetailSelfService table (the earlier self-service package upload method) with all available installers in the LCS Shared asset library. The self-service drop-down package selectors show the options from this newly synchronized, combined source.
    > - As noted at the beginning of this article, the earlier self-service package upload method is obsolete but continues to be supported until it's removed in a future version.

1. On the same page, select default packages that you want to use throughout headquarters in their relevant locations (**Devices**, **All stores**, and **Channel database**).
1. Use the links in the following table to perform standard configuration and installation flows for Modern POS, hardware station, or Commerce Scale Unit.

> [!NOTE]
> There are several installers: Modern POS, Modern POS with offline (a separate installer), Commerce Scale Unit (self-hosted, formerly named *Retail Store Scale Unit*), hardware station, and the less frequent installers (AX 2012 R3 support installers and the Peripheral Simulator).

| Component | Link |
|---|---|
| Modern POS | [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md) |
| Hardware station | [Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md) |
| Commerce Scale Unit (formerly known as Retail Store Scale Unit) | [Configure and install Commerce Scale Unit](retail-store-scale-unit-configuration-installation.md) |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
