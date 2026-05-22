---
title: Code signing a Modern POS (MSIX) extension package
description: Learn how to code sign a Modern POS (MSIX) extension package.
author: josaw1
ms.date: 02/25/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.custom: 
  - bap-template
---

# Code signing a Modern POS (MSIX) extension package

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/mpos-hybrid-apps-deprecation-banner.md)]

This article explains how to code sign a Modern POS (MSIX) extension package. This article applies to version 10.0.18 and later of the Retail software development kit (SDK).

You must sign all .appx files for Modern POS extensions by using a code signing certificate. For production, use a certificate from a trusted authority. For information about how to sign a Universal Windows Platform (UWP) app, see [Create a certificate for package signing](/windows/uwp/packaging/create-certificate-package-signing).

To include your code signing certificate in the Modern POS JavaScript project file, edit the .proj file, and include the node for certificate signing, as shown in the following XML.

```XML
<PackageCertificateKeyFile Condition="Exists('.\MPOS_Extension_Certificate.pfx')">MPOS_Extension_Certificate.pfx</PackageCertificateKeyFile>
```

> [!WARNING]
> Visual Studio 2017 doesn't support a password protected certificate, but the Azure sign tool in the build pipeline can use a password protected cert. 

If you use a self-signed certificate for development purposes, you must manually make the certificate trusted on the machine by adding it to the trusted root folder.

You can also download and include a certificate from a secured location or a secure task during build automation.

For information about how to code sign Universal Windows app packages, see the following articles:

- [Configure the Build solution build task](/windows/uwp/packaging/auto-build-package-uwp-apps#configure-the-build-solution-build-task)
- [Create a certificate for package signing](/windows/msix/package/create-certificate-package-signing)

The sample in GitHub generates a self-signed test certificate during build. This certificate is for development purposes only. Don't use this development certificate for production app extension packages, it's available only to unblock development scenarios.

> [!WARNING]
> The sample script included in GitHub to generate the test certificate works only with a domain account. If you don't use a domain account, the build fails. If you're running a nondomain account, generate or include your own certificate in the "PackageCertificateKeyFile" section.

The generated test certificate is available in the project's intermediate output directory.

- The default location of the test certificate is **bld\\x86\\Debug\\MPOS\_Extension\_Certificate.pfx**.
- You **must** manually make the test certificate trusted before the extension package can be successfully installed on the development machine.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
