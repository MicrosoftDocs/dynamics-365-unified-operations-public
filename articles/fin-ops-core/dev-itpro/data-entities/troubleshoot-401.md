---
title: Troubleshoot unauthorized 401 issues
description: Access some tips for troubleshooting issues that involve unauthorized 401 issues.
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

# Troubleshoot unauthorized 401 issues

[!include [banner](../includes/banner.md)]

This article provides some tips for troubleshooting issues that involve unauthorized 401 issues. 

If you encounter a 401 error, it may be due to client application tokens lacking security compliance. To troubleshoot this issue, check the following: 
 - The "tid" segment of the JWT might contain Entra ID value other than current environment. The “tid” must contain current Entra ID. Make sure the token is acquired from the current environment, Entra.
 - The "oid" segment of the JWT might be absent. Token must have “oid” claim set. Ensure that the client application is provisioned in your Entra. This means it should have a service principal in the Entra.
For more information, see [Multitenant apps without a service principal](/fin-ops/get-started/removed-deprecated-features-platform-updates.md#multitenant-apps-without-a-service-principal-in-the-microsoft-entra-id
-tenant).
 - The "aud" segment of the JWT might contain appId or URL other than the environment url. The “aud” value must be the environment URL. For more information, see [Tokens without an environment URL](/fin-ops-core/
fin-ops/get-started/removed-deprecated-features-platform-updates.md#tokens-without-an-environment-url-in-finance-and-operations-apps).  

