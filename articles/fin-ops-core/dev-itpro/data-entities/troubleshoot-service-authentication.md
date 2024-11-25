---
title: Troubleshoot service authentication issues
description: Access some tips for troubleshooting issues that involve service authentication, including reviewing event logs.
author: pnghub
ms.author: gned
ms.topic: article
ms.date: 05/13/2024
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: 0c22fad3-be0a-4111-97c0-2f3fadfd5f6b
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Troubleshoot service authentication issues

[!include [banner](../includes/banner.md)]

This article provides some tips for troubleshooting issues that involve service authentication.

When you troubleshoot service authentication issues, there are a few basic and common procedures that can help resolve the issues that are most often encountered. These procedures also provide a hands-on demonstration of how the authentication mechanism works. This article includes instructions and also lists a few common issues that users have encountered so far.

## Inspect the JWT
### Capture the JWT from an HTTP request

1. Download Fiddler from <https://www.telerik.com/fiddler>.
2. Set up HTTPS capture to watch the HTTPS traffic from the client.
3. Find the Open Authorization (OAuth) JSON Web Token (JWT). It's the value of the HTTP "Authorization" header without the "bearer" segment.

### Use a deserializer tool to look at the token contents

1. Go to <https://jwt.io>, and paste the JWT into the input panel.
2. View the contents in the form of name-value pairs. See the example that follows.
3. Verify that the following information is correct:

    - **"aud"** – The value corresponds to the Microsoft Microsoft Entra resource concept. Here are some typical issues that involve "aud":

        - The **"aud"** segment of the JWT contains a URI that has a trailing slash.
        - The **"aud"** segment of the JWT contains a URI that uses an incorrect capitalization style. The URI must be all lowercase.

    - **"appid"** – The value corresponds to the Microsoft Entra Native Client App ID (or Service App ID).
    - **"upn"** – The value corresponds to the user who is being authenticated through a Native Client App.


### Check token compliance

You might encounter a 401 Unauthorized error because client application tokens lack security compliance. To troubleshoot the issue, check the following items: 

- The `tid` segment of the JSON web token (JWT) might contain a Microsoft Entra ID value other than current environment. The `tid` segment must contain the current Microsoft Entra ID value. Make sure that the token is acquired from the current environment, Microsoft Entra.
- The `oid` segment of the JWT might be absent. The `oid` claim must be set in the token. Confirm that the client application is provisioned in your Microsoft Entra by having a service principal in Microsoft Entra. For more information, see [Multitenant apps without a service principal in the Microsoft Entra ID tenant](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md#multitenant-apps-without-a-service-principal-in-the-microsoft-entra-id-tenant).
- The `aud` segment of the JWT might contain an appId value or a URL other than the environment URL. The `aud` value must be the environment URL. For more information, see [Tokens without an environment URL in finance and operations apps](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md#tokens-without-an-environment-url-in-finance-and-operations-apps).


## Review the event logs
You can also look at the event logs of the instance machine, if you have access to the virtual machine (VM).

1. Start Event Viewer by running the **eventvwr** command from the **Run** window.
2. Go to the following channels:

    - Application and Services Logs &gt; Microsoft &gt; Dynamics &gt; AX-IntegrationServices &gt; Channel:Operational (Microsoft-Dynamics-AX-IntegrationServices/Operational)
    - Application and Services Logs &gt; Microsoft &gt; Dynamics &gt; AX-SystemRuntime &gt; Channel:Operational (Microsoft-Dynamics-AX-SystemRuntime/Operational)

## Other approaches
- For more information about how OAuth is configured, see [Service endpoints overview](services-home-page.md).
- You can also try to call the service in parallel by using your own client code. The sample code that we published is available at <https://github.com/Microsoft/Dynamics-AX-Integration>.
- If the second method works, you can compare the JWTs from each method.

## Known issues
### Microsoft EntraSTS65001: The user or administrator hasn't consented to use the application

- The **"aud"** segment of the JWT might contain a URI that has a trailing slash. The slash must be removed.
- The **"aud"** segment of the JWT might contain a URI that uses an incorrect capitalization style. The URI must be all lowercase.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
