---
title: New VC++ runtime requirement for cloud-hosted environments running version 10.0.36 or later
description: This article describes the new prerequisite for cloud-hosted environments that run version 10.0.36 or later.
author: mnordick
ms.date: 08/25/2023
ms.topic: conceptual
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: mnordick
ms.search.validFrom: 2022-10-14
ms.custom: bap-template

---

#  New VC++ runtime requirement for cloud-hosted environments and VHD images running version 10.0.36 or later

[!include [banner](../includes/banner.md)]

This article describes the new prerequisite for cloud-hosted environments or VHD images that run version 10.0.36 or later.

## Update cloud-hosted environments to the latest VC++ runtime

As of version 10.0.36, an updated Microsoft Visual C++ (VC++) runtime must be installed in developer cloud-hosted environments (also known as OneBox environments) or VHD images as a prerequisite for new service updates. This new runtime is automatically installed in all newly deployed cloud-hosted environments. However, existing environments and VHD images require manual installation. To download the new runtime, go to [VC++ runtime download](https://aka.ms/vs/17/release/VC_redist.x64.exe).

> [!IMPORTANT]
> After you install the new VC++ runtime, you must restart the machine before you apply the service update. Otherwise, the service update isn't successfully installed.

## Frequently asked questions

### Can I update the VC++ runtime in cloud-hosted environments that currently run versions earlier than 10.0.36?

Yes. You can safely apply the new VC++ runtime to any pre-existing environment or VHD image that doesn't yet run version 10.0.36. We recommend that you apply the update before you apply the version 10.0.36 or later service update.

### Do I have to install this component for every new cloud-hosted environment that I provision?

No. By default, the updated VC++ runtime is installed in all newly provisioned environments.

### Do I have to install this component on the VHD Image?

Yes. The VHD image downloads, through Dynamics 365 version 10.0.32, don't have this VC++ runtime installed. 

### Are any other actions required after the VC++ runtime update is installed?

Yes. You must restart the virtual machine before the update takes effect.
