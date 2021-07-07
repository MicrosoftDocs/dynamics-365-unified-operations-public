---
title: Remove Cloud Scale Unit extensions
description: This topic explains how to remove extensions from the Cloud Scale Unit (CSU).
author: mugunthanm 
ms.date: 06/29/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-29
ms.dyn365.ops.version: 10.0.18
---

# Remove Cloud Scale Unit extensions

[!include [banner](../../includes/banner.md)]

This topic explains how to remove extensions from the Cloud Scale Unit (CSU) and applies to SDK version 10.0.16 or later.

All extensions (Commerce Runtime, Headless Commerce APIs, Channel database scripts, and Cloud POS) applied to the CSU can be removed by applying the Remove CSU Extension ( Microsoft.Dynamics.Commerce.Deployment.CSUExtensionCleanUpPackage) package to the CSU. This package, when applied to the CSU, removes all the extensions and keeps only the base CSU components and the Microsoft hotfixes. The package will not remove extensions applied to channel components like Modern POS, Hardware station, Cloud Scale Unit - Self hosted or Commerce back office.

To remove the extensions follow the below steps:

1. Go to https://lcs.dynamics.com/v2.
2. Sign in to Lifecycle Serivces (LCS), and select the **Shared asset library** tile.
3. For **Select asset type**, select **Commerce Cloud Scale Unit Extension**.
4. Download the package with name **Remove CSU Extension** from the Commerce Cloud Scale Unit Extension files.
5. When the download finishes, navigate to your project in LCS. On the hamburger menu, select **Asset library**.
6. Select the **Commerce Cloud Scale Unit Extension** asset type, and then select the **+** button to upload the **Remove CSU Extension** package. Provide a package name and description and then add the package file by selecting **Add file**.
7. After the upload finishes, select **Confirm** to complete the upload process.
8. The package will be validated by LCS in a few minutes. After validation finishes, mark the package as **Release candidate**.
9. After the upload finishes, the package needs to be deployed to the environment. To deploy the package, follow the steps in the [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

For information about how to deploy the packages either manually or by using the automated flow in LCS, see [Apply a deployable package](../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md) and [Install a deployable package](../../fin-ops-core/dev-itpro/deployment/install-deployable-package.md).
