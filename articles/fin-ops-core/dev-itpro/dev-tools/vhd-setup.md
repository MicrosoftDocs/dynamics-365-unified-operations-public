---
title: Set up the downloadable VHD for first use
description: Learn about how to set up the downloadable VHD for first use of the Application Object Server and register a new application in Microsoft Entra ID.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/30/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.dyn365.ops.version: AX 7.0.0
---

# Set up the downloadable VHD for first use

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This article applies to the virtual hard drive (VHD) that was released for versions 10.0.24 and later.

When you first sign in to the virtual machine, the **Application Object Server** isn't ready for use. You need to run a script that creates self-signed certificates for the virtual machine and a customer-provided application registration ID for authentication. After you successfully run the script, the environment is ready for use.

## Register a new application in Microsoft Entra ID

To register a new application in Microsoft Entra ID, follow the steps outlined in [Register app or web API](/azure/active-directory/develop/quickstart-register-app). The new app registration should be for a web application, and you should add the following redirect URIs:

- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/`
- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/oauth/`

When you create the app registration, note the **Application (client) ID**.

## Run the setup script

After you sign in by using the **localadmin** account, right-click the desktop shortcut **Generate Self-Signed Certificates**, and select **Run as administrator**. When the script prompts for the application ID, provide the **Application (client) ID** created in Microsoft Entra ID.

When the script finishes, the environment is ready for use. At this time, you can run the Admin Provisioning tool to set the administrator account, permissions, and tenant. Make sure that the email you provide is for the Microsoft Entra tenant in which you created the application registration.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
