---
title: View POS extension package information
description: Learn about the Extension packages section of the Settings view in Microsoft Dynamics 365 Commerce the point of sale (POS).
author: josaw1
ms.date: 02/20/2026
ms.topic: article
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-02-25
ms.custom:
  - bap-template
---

# View POS extension package information

[!include [banner](../includes/banner.md)]

This article explains the **Extension packages** section of the **Settings** view in Microsoft Dynamics 365 Commerce the point of sale (POS).

In the **Settings** view in the point of sale (POS), the **Extension packages** section shows the list of POS extension packages that are included as part of the core POS. The tile for each package shows the status of that package. The package status indicates whether the extension was loaded, couldn't be loaded, or was skipped.

## Extension package status

This section describes what each package status means.

- **Loaded** – The extension package was successfully loaded.
- **Failed** – The extension package wasn't successfully loaded.
- **Skipped** – The package was skipped and wasn't loaded. In the extension manifest, you can specify that a package should be loaded for a specific locale, such as **en-fr**, but skipped for all the other locales.

:::image type="content" source="./media/ExtensionPackage.png" alt-text="Screenshot of the Extension packages section in the POS Settings view.":::

> [!NOTE]
> Store Commerce for web doesn't display the extension version in the Customization.settings file under the **About** section on the **Settings** page. It only shows the Microsoft app package version. You can view extension package versions only from the **Extension details** section.

## Extension package details

If an issue occurs when an extension loads, or if there's a conflicting extension, use the details provided for each extension package to determine which extension file causes the problem. You can troubleshoot the problem this way.

To view the details of an extension package, select **View details** on the tile for that package. The POS opens a new view, where you can see the details of all the individual extensions in the package. If any extensions aren't successfully loaded or are skipped, the details appear in the right pane.

The **Status** column shows the status of each extension in the package, the **Name** column shows the name of the extension type, and the **Path** column shows the path of the implementation file in the package. When you select a specific line item, the right pane also shows a description of the extension.

The information in this view is based on the manifest file that the extension package includes. The POS extension loader loads all the extension packages and updates the status. The status information includes any errors that it logs.

> [!NOTE]
> Dual display custom control and other extension details information related to dual display aren't shown in the extension details view.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
