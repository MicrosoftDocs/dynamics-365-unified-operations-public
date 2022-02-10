---
title: Setup the Downloadable VHD for First Use
description: This topic explains how to update an Azure pipeline to use new NuGet packages.
author: jorisdg
ms.date: 03/04/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.custom:
ms.search.region: Global
ms.author: jorisde
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: AX 7.0.0
---

# Setup the Downloadable VHD for First Use

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This topic applies to the VHD that was released for versions 10.0.24 and newer.

Upon first login to the virtual machine, the **Application Object Server** will not be ready for use. A script needs to be run that will create self-signed certificates to be used on the virtual machine, and a customer-provided application registration ID for authentication. After successfully running the script the environment will be ready for use.

## Register a New Application in Azure Active Directory

To register a new application in **Azure Active Directory**, follow the steps outlined in [Register app or web API](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app). The new app registration should be for a web application, and the redirect URI should be set to `https://usnconeboxax1aos.cloud.onebox.dynamics.com`.

Once created, make note of the **Application (client) ID**.

## Run the setup script

When logged in with the **Administrator** account, double click the desktop shortcut entitled **Generate SelfSigned Certs and Configure F&O**. When the script prompts for the application ID, provide the **Application (client) ID** created in **Azure Active Directory**.

Once the script is finished, the environment is ready for use. At this time, you can run the **Admin Provisioning Tool** to set the administrator account, permissions and tenant. Please ensure the email provided is for the **Azure Active Directory** tenant in which the application registration was created.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]