---
# required metadata

title: Database movement API - Authentication
description: This topic provides overview information about how to authenticate with the Database Movement application programming interface (API).
author: laneswenka
ms.date: 02/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.0

---

# Database movement API - Authentication

[!include [banner](../../includes/banner.md)]

This topic provides overview information about how to authenticate with the Database Movement application programming interface (API).

## Fundamentals

To call the Database Movement API, your application must acquire an access token from the Microsoft identity platform. The access token contains information about your application and the permission that it has to call resources in Microsoft Dynamics Lifecycle Services (LCS).

### Access token

Access tokens that are issued by the Microsoft identity platform are base64–encoded JavaScript Object Notation (JSON) Web Tokens (JWTs). They contain information (claims) that the Database Movement API and other web APIs that are secured by the Microsoft identity platform use to validate the caller and make sure that the caller has the correct permissions to perform the operation that they are requesting. During calls, you can treat access tokens as opaque. You should always transmit access tokens over a secure channel, such as Transport Layer Security (TLS) and Hypertext Transfer Protocol Secure (HTTPS).

Here is an example of an access token that is issued by the Microsoft identity platform.

```jwt
EwAoA8l6BAAU7p9QDpi/D7xJLwsTgCg3TskyTaQAAXu71AU9f4aS4rOK5xoO/SU5HZKSXtCsDe0Pj7uSc5Ug008qTI+a9M1tBeKoTs7tHzhJNSKgk7pm5e8d3oGWXX5shyOG3cKSqgfwuNDnmmPDNDivwmi9kmKqWIC9OQRf8InpYXH7NdUYNwN+jljffvNTewdZz42VPrvqoMH7hSxiG7A1h8leOv4F3Ek/oeJX6U8nnL9nJ5pHLVuPWD0aNnTPTJD8Y4oQTp5zLhDIIfaJCaGcQperULVF7K6yX8MhHxIBwek418rKIp11om0SWBXOYSGOM0rNNN59qNiKwLNK+MPUf7ObcRBN5I5vg8jB7IMoz66jrNmT2uiWCyI8MmYDZgAACPoaZ9REyqke+AE1/x1ZX0w7OamUexKF8YGZiw+cDpT/BP1GsONnwI4a8M7HsBtDgZPRd6/Hfqlq3HE2xLuhYX8bAc1MUr0gP9KuH6HDQNlIV4KaRZWxyRo1wmKHOF5G5wTHrtxg8tnXylMc1PKOtaXIU4JJZ1l4x/7FwhPmg9M86PBPWr5zwUj2CVXC7wWlL/6M89Mlh8yXESMO3AIuAmEMKjqauPrgi9hAdI2oqnLZWCRL9gcHBida1y0DTXQhcwMv1ORrk65VFHtVgYAegrxu3NDoJiDyVaPZxDwTYRGjPII3va8GALAMVy5xou2ikzRvJjW7Gm3XoaqJCTCExN4m5i/Dqc81Gr4uT7OaeypYTUjnwCh7aMhsOTDJehefzjXhlkn//2eik+NivKx/BTJBEdT6MR97Wh/ns/VcK7QTmbjwbU2cwLngT7Ylq+uzhx54R9JMaSLhnw+/nIrcVkG77Hi3neShKeZmnl5DC9PuwIbtNvVge3Q+V0ws2zsL3z7ndz4tTMYFdvR/XbrnbEErTDLWrV6Lc3JHQMs0bYUyTBg5dThwCiuZ1evaT6BlMMLuSCVxdBGzXTBcvGwihFzZbyNoX+52DS5x+RbIEvd6KWOpQ6Ni+1GAawHDdNUiQTQFXRxLSHfc9fh7hE4qcD7PqHGsykYj7A0XqHCjbKKgWSkcAg==
```

To call the Database Movement API, you attach the access token as a bearer token to the authorization header in your HTTP request. Here is an example.

```HTTP
HTTP/1.1
Authorization: Bearer EwAoA8l6BAAU ... 7PqHGsykYj7A0XqHCjbKKgWSkcAg==
Host: lcsapi.lcs.dynamics.com
GET https://lcsapi.lcs.dynamics.com/databasemovement/v1/databases
```

## Register a new application by using the Azure portal

1. Sign in to the [Microsoft Azure portal](https://portal.azure.com) by using a work or school account, or a personal Microsoft account.
2. If your account gives you access to more than one tenant, select your account in the upper-right corner, and set your portal session to the Azure Active Directory (Azure AD) tenant that you want.
3. In the left pane, select the **Azure Active Directory** service, and then select **App registrations \> New registration**.
4. When the **Register an application** page appears, enter your application's registration information:

    - **Name** – Enter a meaningful application name that will be shown to users of the app.
    - **Supported account types** – Select the types of accounts that your app should support.

        | Supported account types | Description |
        |-------------------------|-------------|
        | Accounts in this organizational directory only | Select this option if you're building a line-of-business app. This option isn't available unless you're registering the app in a directory.<p>This option is mapped to **Azure AD only single-tenant**.</p><p>This option is the default option unless you're registering the app outside a directory. In that case, the default option is **Azure AD multi-tenant and personal Microsoft accounts**.</p> |
        | Accounts in any organizational directory | Select this option to target all business and educational customers.<p>This option is mapped to **Azure AD only multi-tenant**.</p><p>If you registered the app as **Azure AD only single-tenant**, you can use the **Authentication** blade to update it to **Azure AD only multi-tenant** and then back to **Azure AD only single-tenant**.</p> |
        | Accounts in any organizational directory and personal Microsoft accounts | Select this option to target the widest set of customers.<p>This option is mapped to **Azure AD multi-tenant and personal Microsoft accounts**.</p><p>If you registered the app as **Azure AD multi-tenant and personal Microsoft accounts**, you can't change this setting in the user interface (UI). Instead, you must use the application manifest editor to change the supported account types.</p> |

    - **Redirect URI (optional)** – Select the type of app that you're building: **Web** or **Public client (mobile & desktop)**. Then enter the redirect URI (or reply URL) for the app.

        - For web apps, provide the base URL of the app. For example, `http://localhost:31544` might be the URL for a web app that runs on your local machine. Users then use this URL to sign in to a web client app.
        - For public client apps, provide the URI that Azure AD uses to return token responses. Enter a value that is specific to your app, such as `myapp://auth`.

        To see specific examples for web apps or native apps, see the [quick start guides from Azure AD](/azure/active-directory/develop/#quickstarts).

5. Under **API permissions**, select **Add a permission**. Then, on the **APIs my organization uses** tab, search for **Dynamics Lifecycle services**, and add the **user\_impersonation** permission to your app.
6. Select **Register**.

[![Registering a new app in the Azure portal.](../media/new-app-registration-expanded.png)](../media/new-app-registration-expanded.png#lightbox)

Azure AD assigns a unique application ID (client ID) to your app, and you're taken to the **Overview** page for your app. To add more capabilities to your app, you can select other configuration options, such as options for branding, and for certificates and secrets.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]