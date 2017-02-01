---
# required metadata

title: Configure authentication providers | Microsoft Docs
description: This topic provides an overview of the process for configuring a new OpenID authentication provider.
author: kfend
manager: AnnBe
ms.date: 2016-02-04 20:58:59
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 31241
ms.assetid: 39cc037d-c6d7-4ea5-b5ed-96795e407667
ms.region: Global
# ms.industry: 
ms.author: meeram

---

# Configure authentication providers

This topic provides an overview of the process for configuring a new OpenID authentication provider.

The E-Commerce platform uses industry-standard [OpenID Connect](http://openid.net/connect/) as the mechanism for authentication. This article covers the pages that you use to register the OpenID providers that are used in an online store. Retail Server uses OpenID Connect as the mechanism to support authenticated customers. OpenID Connect is a universally accepted standard that acts as simple and evolved identity provider on top of OAuth 2.0. Retail Server can be integrated with both ready-to-use OpenID providers through the Microsoft Azure Access Control service and other independently available providers. In addition, any custom providers that support OpenID connect can be integrated. These providers can be registered with Microsoft Dynamics 365 for Operations. The following illustration shows the step-by-step handshake that occurs between the Retail Server and the E-Commerce front-end server to pass the authentication token for subsequent calls. [![OpenId](./media/openid-1024x540.png)](./media/openid.png) Here is a walkthrough of the process for registering OpenID providers so that they can be used in Retail Server.

1.  From the Retail IT workspace, go to **Retail shared parameters** &gt; **OpenID providers**. You can use the **OpenID providers** page to register additional providers, as shown in the following screen shot. For every provider that you support, enter the details of the OpenID provider and the details of the relying parties in Dynamics 365 for Operations. Retail Server uses this information to request and use an authentication token for subsequent calls. [![ECommerce1](./media/ecommerce1-1024x430.png)](./media/ecommerce1.png)
2.  Run distribution schedule 1110.
3.  For the test online store, edit the web.config file so that it specifies the correct redirect URL and domain, as shown in the following example. If you're using a third-party online store, this information can be stored as required.

        redirectUrl=https://usnconeboxax1ecom.cloud.onebox.dynamics.com/en/Pages/OauthV2Redirect/OauthV2Redirect.aspx



