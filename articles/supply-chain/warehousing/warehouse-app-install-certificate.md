---
title: Install Warehouse Management mobile app V4 on Windows (preview)
description: Learn how to install Warehouse Management mobile app V4 and its required certificate on Windows.
author: nsayginer
ms.author: nsayginer
ms.topic: how-to
ms.date: 07/11/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Install Warehouse Management mobile app V4 on Windows (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Warehouse Management mobile app V4 (now in preview) is available for Microsoft Windows, Apple iOS, and Google Android. This article explains how to install the app and its required certificate on Windows.  

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Download the App

To download the app to your Windows computer, follow these steps:

 1. Go to the [Warehouse Management (Windows) page on App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release).
 1. Download the `.msixbundle` file to your device.

## Install the certificate

Before you can install the app on Windows, you must install the certificate that is used to sign the app. Follow these steps to install the certificate:

1. Open Windows File Explorer and navigate to the location where you downloaded the `.msixbundle` file.
1. Right-click the `.msixbundle` file and select **Properties**.
1. Open the **Digital signatures** tab.
1. Select the signature in the **Embedded signatures** list and then select **Details**.
1. Select **View certificate**.
1. Select **Install certificate**.
1. The **Certificate Import Wizard** opens. Select **Local machine**. Then select **Next**.
1. Choose **Place all certificates in the following store**.
1. Select **Browse**.
1. Select **Trusted Root Certification Authorities** and then select **OK**.
1. Select **Next**.
1. Select **Finish**.

## Install the app

After you have downloaded the app and installed the certificate, you're ready to install the app. Follow these steps:

 1. Open Windows File Explorer and navigate to the location where you downloaded the `.msixbundle` file.
 1. Double-click on the `.msixbundle` file.
 1. The installer opens and shows information about the app. Select **Install** to install it.
