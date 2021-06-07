---
title: Code signing a Modern POS (MSIX) extension package
description: This topic explains how to code sign a Modern POS (MSIX) extension package.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Code signing a Modern POS (MSIX) extension package

[!include [banner](../../../includes/banner.md)]

This topic explains how to code sign a Modern POS (MSIX) extension package. This topic applies to the Retail SDK version 10.0.18 and later.

All MPOS extension .appx files must be signed by a code signing certificate. We recommend that you use a certificate from a trusted authority for production. For information on signing a Universal Windows Platform (UWP) app, see [Create a certificate for package signing](/windows/uwp/packaging/create-certificate-package-signing).

To include your certificate for signing in the ModernPos JavaScript project file, edit the .proj file and include the node for certificate signing:

```XML
<PackageCertificateKeyFile Condition="Exists('.\MPOS_Extension_Certificate.pfx')">MPOS_Extension_Certificate.pfx</PackageCertificateKeyFile>
```

If you're using a self-signed certificate for development purpose, then the certificate must be manually trusted in that machine by adding it to the trusted root folder.

You can also download and include a cert from secured location/secure task during your build automation.

For information about code signing Universal Windows App packages, see these links:

+ [Configure the Build solution build task](/windows/uwp/packaging/auto-build-package-uwp-apps#configure-the-build-solution-build-task)
+ [Create a certificate for package signing](/windows/msix/package/create-certificate-package-signing)

The sample in GitHub generates a self-signed test certificate during build for development purposes only. This certificate is only available to unblock development scenarios.

> [!WARNING]
> Do not use this development certificate for production app extension packages.

The generated test certificate will be available in the project's intermediate output directory.

- By default, the location is `bld\x86\Debug\MPOS_Extension_Certificate.pfx`.
- The generated test certificate MUST be manually trusted for the extension package to be successfully installed on the development machine.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
