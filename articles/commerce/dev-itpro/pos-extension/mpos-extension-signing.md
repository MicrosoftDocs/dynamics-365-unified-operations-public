---
title: Code signing a Modern POS (MSIX) extension package
description: This article explains how to code sign a Modern POS (MSIX) extension package.
author: josaw1
ms.date: 05/03/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: AX 10.0.18
---

# Code signing a Modern POS (MSIX) extension package

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/mpos-hybrid-apps-deprecation-banner.md)]

This article explains how to code sign a Modern POS (MSIX) extension package. This article applies to version 10.0.18 and later of the Retail software development kit (SDK).

All .appx files for Modern POS extension must be signed by a code signing certificate. For production, we recommend that you use a certificate from a trusted authority. For information about how to sign a Universal Windows Platform (UWP) app, see [Create a certificate for package signing](/windows/uwp/packaging/create-certificate-package-signing).

To include your code signing certificate in the Modern POS JavaScript project file, edit the .proj file, and include the node for certificate signing, as shown in the following XML.

```XML
<PackageCertificateKeyFile Condition="Exists('.\MPOS_Extension_Certificate.pfx')">MPOS_Extension_Certificate.pfx</PackageCertificateKeyFile>
```
> [!WARNING]
> A password protected certificate is not supported in Visual Studio 2017, but you can use password protected cert in the build pipeline using the Azure sign tool. 

If you're using a self-signed certificate for development purposes, you must manually make the certificate trusted on the machine by adding it to the trusted root folder.

You can also download and include a certificate from a secured location or a secure task during build automation.

For information about how to code sign Universal Windows app packages, see the following articles:

+ [Configure the Build solution build task](/windows/uwp/packaging/auto-build-package-uwp-apps#configure-the-build-solution-build-task)
+ [Create a certificate for package signing](/windows/msix/package/create-certificate-package-signing)

The sample in GitHub generates a self-signed test certificate during build. This certificate is for development purposes only. Do not use this development certificate for production app extension packages, it's available only to unblock development scenarios.

> [!WARNING]
> The sample script included in GitHub to generate the test certificate will work only with a domain account. If you are not using a domain account, the build will fail. If you are running a non-domain account, generate or include your own certificate in the "PackageCertificateKeyFile" section.

The test certificate that is generated will be available in the project's intermediate output directory.

- The default location of the test certificate is **bld\\x86\\Debug\\MPOS\_Extension\_Certificate.pfx**.
- You **must** manually make the test certificate trusted before the extension package can be successfully installed on the development machine.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
