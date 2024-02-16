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

[comment]: <> (Here we will write that after the app and the connections.json is installed, the app needs to retrieve the Entra ID session from somewhere. That somewhere is either Microsoft Intune, if the customer used this to mass deploy, or any other app that is authenticated using the Entra ID user that will be entered to authenticate wma.)

## Additional resources

- [Mass deploy the Warehouse Management mobile app and manage connection configurations](warehouse-app-intune.md)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
