---
# required metadata

title: Code Signing the Modern POS (MSIX) Extension Package
description: This topic explains how to Code Signing the Modern POS (MSIX) Extension Package.
author: mugunthanm
ms.date: 04/13/2021
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
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# Code Signing the Modern POS (MSIX) extension Package

[!include [banner](../includes/banner.md)]

This topic explains how to code signing the Modern POS (MSIX) extension Package, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

All MPOS extension appx file must be signed by code signing certificate, its recommend to use certificate from a trusted authority for production, details for signing the UWP app can be found [here](https://docs.microsoft.com/en-us/windows/uwp/packaging/create-certificate-package-signing).

Include your certificate for signing in the ModernPos JavaScript project file, edit the proj file and include the node for certificate signing:

```XML
Ex:

<PackageCertificateKeyFile Condition="Exists('.\MPOS_Extension_Certificate.pfx')">MPOS_Extension_Certificate.pfx</PackageCertificateKeyFile>
```

If your using self signed certificate for development purpose, then the certificate must be manually trusted in that machine by adding it to the trusted root folder.

You can also download and include cert from secured location/secure task during your build automation.

More information about code signing Universal Windows App packages can be found in the links below.

[Set up automated builds for your UWP app - UWP applications | Microsoft Docs](https://docs.microsoft.com/en-us/windows/uwp/packaging/auto-build-package-uwp-apps#configure-the-build-solution-build-task)

<https://docs.microsoft.com/en-us/windows/msix/package/create-certificate-package-signing>

The sample in the [GitHub](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-InStore?path=%2Fsrc%2FPosSample%2FModernPos%2FModernPos.jsproj) will generate a self-signed test certificate during build for dev purpose only. This certificate is only available to unblock development scenarios and SHOULD NOT be used for production app extension packages.

-   The generated test certificate will be available in the projects intermediate output directory.

    -   By default this will be: bld\\x86\\Debug\\MPOS\_Extension\_Certificate.pfx

    -   The generated test certificate MUST be manually trusted for the extension package to be successfully installed on the development machine.
