---
# required metadata

title: Remove Cloud Scale Unit Extensions
description: This topic explains how to remove extensions from the Cloud Scale Unit (CSU).
author: mugunthanm 
ms.date: 06/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-29
ms.dyn365.ops.version: 10.0.18

---

# Remove Cloud Scale Unit Extensions

[!include [banner](../../includes/banner.md)]

This topic explains how to remove extensions from the Cloud Scale Unit (CSU) and applies to SDK version 10.0.16 or later.

All extensions (Commerce Runtime, Headless Commerce APIs, Channel database scripts and Cloud POS) applied to CSU can be removed by applying  the Microsoft.Dynamics.Commerce.Deployment.CSUExtensionCleanUpPackage to CSU, this packages when applied to CSU removes all the extensions and keeps only the base CSU components and the Microsoft hotfixes.

To remove the extensions follow the below steps:

1. Go to https://lcs.dynamics.com/v2.
2. Sign in to LCS, then click the **Shared asset library** tile.
3. In the Select asset type, select **Commerce Cloud Scale Unit Extension**
4. Download the package with name **Remove CSU Extension** from the Commerce Cloud Scale Unit Extension files.
5. After the download, navigate to your project in LCS then on the hamburger menu, select Asset library.
6. Select the Commerce Cloud Scale Unit Extension asset type, and then select the + button to upload the *Remove CSU Extension** package. Provide a package name and description and then add the package file by selecting Add file.
7. After the upload is complete, select Confirm to complete the upload process.
8. The package will be validated by LCS in a few minutes. After validation is complete, mark the package as Release candidate.
9. After upload, the package needs to be deployed to the environment. For more information, follow the steps outlined in [Apply updates and extensions to Commerce Scale Unit (cloud)](../../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

For information about how to deploy the packages either manually or by using the automated flow in LCS, see [Apply a deployable package](../../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md) and [Install a deployable package](../../../fin-ops-core/dev-itpro/deployment/install-deployable-package.md).
