---
title: Mass deploy the mobile app for user-based authentication
description: This article explains how to mass deploy the Warehouse Management mobile app for user-based authentication by using a mobile device management (MDM) solution such as Microsoft Intune.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Mass deploy the mobile app with user-based authentication

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> In order to leverage the advantages of mobile mass deployment (MDM), you must have configured the Warehouse Management mobile app to use [username/password authentication](warehouse-app-authenticate-user-based.md#usernamepassword-authentication) with [single sign-on](warehouse-app-authenticate-user-based.md#single-sign-on). This is because ...

## Prerequisites

 - Follow the [guide to mass deploy the Warehouse Management mobile app and manage connection configurations](warehouse-app-intune.md)

## How the Warehouse Management mobile app authenticates

When using the device code flow authentication or the username/password authentication without single sign-on, after deploying the app and the connection configurations, each instance will need to be authenticated separately.

When using single sign-on, provided that the Entra ID that will be used to authenticate the Warehouse Management mobile app is already signed in the device in another application (for example Microsoft Teams, Company Portal or Outlook), the Warehouse Management mobile app will automatically get the authentication token, without the user needing to enter the Entra ID password.
Then, the user can proceed with logging in to their work user account to access the work, or will be logged in automatically, if you are using [default user ID](mobile-device-work-users.md#set-up-mobile-device-user-accounts).

## Additional resources

- [Mass deploy the Warehouse Management mobile app and manage connection configurations](warehouse-app-intune.md)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
