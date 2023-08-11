---
# required metadata

title: New VC++ Runtime requirements for Cloud-Hosted Environments running versions 10.0.36+
description: This article lists new prerequite requirements for Cloud-Hosted Environments running versions 10.0.36+
author: mnordick
ms.date: 08/11/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: mnordick
ms.search.region: Global
ms.author: mnordick
ms.search.validFrom: 2022-10-14

---
#  New VC++ Runtime requirement for Cloud-Hosted Environments running versions 10.0.36+

[!include [banner](../includes/banner.md)]

This article lists new prerequite requirements for Cloud-Hosted Environments running versions 10.0.36+.

## Update Cloud-Hosted Environments to the latest VC++ Runtime.

Developer Cloud-Hosted Environments (CHEs), also known as Onebox environments, as of version 10.0.36 will require an updated VC++ Runtime installed as a prerequisite for new service updates. All newly deployed environments will automatically have this new prerequisite installed, but existing environments will require manual installation. The download link for the new runtime can be found below.

[VC++ Runtime download](https://aka.ms/vs/17/release/VC_redist.x64.exe)

> [!IMPORTANT]
> After installing the new VC++ runtime, you must perform a machine reboot prior to applying the service update. This is required for the service update to install successfully.


## Frequently asked questions

### Can I update the VC++ runtime on Cloud-Hosted Environments currently running versions prior to 10.0.36?
Yes. The new VC++ runtime can be safely applied to any pre-existing environment not yet running 10.0.36. It is recommended to apply the update prior to applying the 10.0.36 or greater service update.

### Do I need to install this component for every new Cloud-Hosted Environment that I provision?
No. All newly-provisioned environments will have the updated VC++ runtime installed by default.

### Are any other actions necessary after the VC++ runtime update is installed?
Yes. The virtual machine requires a reboot to take effect.