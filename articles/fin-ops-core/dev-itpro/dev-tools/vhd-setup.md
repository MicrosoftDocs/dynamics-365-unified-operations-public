---
title: Set up the downloadable VHD for first use
description: This article describes how to set up the downloadable VHD for first use of the Application Object Server.
author: gianugo
ms.date: 02/17/2022
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2022-02-09
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 
---

# Set up the downloadable VHD for first use

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This article applies to the virtual hard drive (VHD) that was released for versions 10.0.24 and later.

When you first sign in to the virtual machine, the **Application Object Server** will not be ready for use. A script needs to be run that will create self-signed certificates to be used on the virtual machine, and a customer-provided application registration ID for authentication. After successfully running the script, the environment will be ready for use.

## Register a new application in Azure Active Directory

To register a new application in Microsoft Azure Active Directory (Azure AD), follow the steps outlined in [Register app or web API](/azure/active-directory/develop/quickstart-register-app). The new app registration should be for a web application, and the following redirect URIs should be added:

- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/`
- `https://usnconeboxax1aos.cloud.onebox.dynamics.com/oauth/`

Once created, make note of the **Application (client) ID**.

## Run the setup script

After you sign in with the **localadmin** account, right-click the desktop shortcut **Generate Self-Signed Certificates**, and select **Run as administrator**. When the script prompts for the application ID, provide the **Application (client) ID** created in Azure Active Directory.

When the script finishes, the environment is ready for use. At this time, you can run the Admin Provisioning tool to set the administrator account, permissions, and tenant. Make sure that the email provided is for the Azure Active Directory tenant in which the application registration was created.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
