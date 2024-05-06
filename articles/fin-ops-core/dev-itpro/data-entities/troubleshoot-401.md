---
title: Troubleshoot 401 Unauthorized issues
description: This article provides tips to help you troubleshoot issues that involve 401 Unauthorized errors.
author: pnghub
ms.author: gned
ms.topic: article
ms.date: 05/06/2024
ms.reviewer: twheeloc
audience: Developer
ms.assetid: 0c22fad3-be0a-4111-97c0-2f3fadfd5f6b
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.0
---

# Troubleshoot 401 Unauthorized issues

[!include [banner](../includes/banner.md)]

This article provides tips to help you troubleshoot issues that involve 401 Unauthorized errors.

You might encounter a 401 Unauthorized error because client application tokens lack security compliance. To troubleshoot the issue, check the following items: 

- The `tid` segment of the JSON web token (JWT) might contain a Microsoft Entra ID value other than current environment. The `tid` segment must contain the current Microsoft Entra ID value. Make sure that the token is acquired from the current environment, Microsoft Entra.
- The `oid` segment of the JWT might be absent. The `oid` claim must be set in the token. Confirm that the client application is provisioned in your Microsoft Entra by having a service principal in Microsoft Entra. For more information, see [Multitenant apps without a service principal in the Microsoft Entra ID tenant](/fin-ops/get-started/removed-deprecated-features-platform-updates.md#multitenant-apps-without-a-service-principal-in-the-microsoft-entra-id-tenant).
- The `aud` segment of the JWT might contain an appId value or a URL other than the environment URL. The `aud` value must be the environment URL. For more information, see [Tokens without an environment URL in finance and operations apps](/fin-ops-core/fin-ops/get-started/removed-deprecated-features-platform-updates.md#tokens-without-an-environment-url-in-finance-and-operations-apps).
