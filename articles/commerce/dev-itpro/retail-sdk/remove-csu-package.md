---
title: Remove Cloud Scale Unit extensions
description: Learn how to remove extensions from the Cloud Scale Unit (CSU).
author: josaw1
ms.date: 02/20/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: global
ms.search.validFrom: 2020-06-29
ms.custom: 
  - bap-template
---

# Remove Cloud Scale Unit extensions

[!include [banner](../../includes/banner.md)]

This article explains how to remove extensions from the Cloud Scale Unit (CSU). It applies to version 10.0.16 or later of the software development kit.

You can remove all extensions (Commerce runtime, Headless Commerce APIs, channel database scripts, and Store Commerce for web) that you applied to the CSU by applying the Remove CSU Extension package (Microsoft.Dynamics.Commerce.Deployment.CSUExtensionCleanUpPackage) to the CSU. When you apply this package, it removes all extensions, and keeps only the base CSU components and the Microsoft hotfixes. It doesn't remove extensions that you applied to channel components such as the Store Commerce app, Hardware station, Cloud Scale Unit - Self hosted, or Commerce back office.

To remove extensions, follow these steps:

1. Sign in to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2).
1. Select the **Shared asset library** tile.
1. Select **Commerce Cloud Scale Unit Extension** as the asset type, and download the package that is named **Remove CSU Extension**.
1. After the package is downloaded, go to your project in LCS.
1. On the Menu button (sometimes referred to as the hamburger or the hamburger button), select **Asset library**.
1. Select **Commerce Cloud Scale Unit Extension** as the asset type, and then select the plus sign (**+**) button to upload the **Remove CSU Extension** package.
1. Enter a package name and description, and then add the package file by selecting **Add file**.
1. After the package file is uploaded, select **Confirm** to complete the upload process.
1. LCS validates the package. This validation takes a few minutes. After it's completed, mark the package as **Release candidate**.
1. After the upload process is completed, deploy the package to the environment. Follow the steps in [Apply updates and extensions to Commerce Scale Unit (cloud)](../../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

> [!IMPORTANT]
> The **Remove CSU Extension** package is designed to be applied once per calendar day. While this package is in place, any subsequent deployment attempts in the same day fail.

For information about how to deploy packages either manually or by using the automated flow in LCS, see [Apply a deployable package](../../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md) and [Install a deployable package](../../../fin-ops-core/dev-itpro/deployment/install-deployable-package.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]