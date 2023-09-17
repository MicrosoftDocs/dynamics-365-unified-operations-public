---
title: e-Commerce platform software development kit (SDK)
description: This article describes the e-Commerce Platform SDK.
author: josaw1
ms.date: 07/09/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: c0b1740b-1cbb-47c4-94e8-779cde8411af
---

#  e-Commerce platform software development kit (SDK)

[!include [banner](../includes/banner.md)]

This article describes the e-Commerce Platform SDK. The e-Commerce Platform software development kit (SDK) consists of the following components:

-   Framework
-   Controls
-   Publishing (only supported in version 1661 and higher: [Support for Service to Service authentication in Retail Server](https://community.dynamics.com/ax/b/axforretail/archive/2016/09/24/support-for-service-to-service-authentication-in-retail-server))
-   Sample ASP.NET website

## Use the sample ASP.NET website


### Download the Retail SDK

The Retail SDK is available in development environments, and in hotfix packages in a Retail SDK folder.

- If you get the SDK from a development instance, it is immediately ready for configuration and use. For more information, see [Access instances](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md). 
- If you get the SDK from a hotfix, it is included in the hotfix package as a zipped folder. Hotfixes are cumulative and include all other fixes. 

We recommend that you put the SDK in a source control system such as Visual Studio Online.

### Use the Retail SDK to create the sample ASP.NET website
1.  Open Visual Studio in Admin mode. This step is necessary for publishing to the inetpub folder.
2.  Open C:\\Microsoft Dynamics AX70\\RetailSdkOnlineStoreOnlineStore.sln contains all the framework components.
3.  The sample online store is available at C:\\Microsoft Dynamics AX70\\RetailSdkSampleExtensionsOnlineStore.
4.  Compile and publish the web store front, from within Visual Studio.
5.  Update the path of the RetailStorefrontWebSite from IIS Manager.
    -  Note that RetailStorefrontWebSite created by the default setup points to C:\\Microsoft Dynamics AX70\\Retail Store Front\\Package.
    -  However, the publishing of the web storefront from RetailSDK will drop the files at C:\\inetpub\\RetailWeb\\Storefront.
    -  Hence, the physical path of the RetailStorefrontWebSite must be updated to point to “C:\\inetpub\\RetailWeb\\Storefront” to access web storefront on the same ports as before. Another option would be to create a new website and have that point to the inetpub location.

6.  Browse to `http://localhost:55080` or access `https://usnconeboxax1ecom.cloud.onebox.dynamics.com/` to see a test ASP.NET website.

### Enable anonymous access

E-Commerce websites must allow anonymous access to work correctly. Ensure that anonymous access is enabled by adding the following key in the Commerce Scale Unit web.config file under app settings.

`
add key="IsAnonymousEnabled" value="true"
`

### Externally accessing the ASP.NET website

The following configuration changes will be required if either of these conditions applies:

-   You are accessing web storefront from within a browser that is not on the same box as the e-Commerce server.
-   The e-Commerce server and Commerce Scale Unit are on two different boxes.

You will need to update the “retailServerUrl” inside the web.config file of the RetailStorefrontWebSite. The following two fields will need to be updated to use the machine name instead of local host:

```xml
retailServerUrl=<http://localhost:35080/RetailServer/V1>
<add key="RetailServerRoot" value="<http://localhost:35080/RetailServer/V1>" />
```

If you are accessing the web storefront over HTTPS, then you will need to update the above URLs to the HTTPS equivalent.

### Operating unit or channel configuration

The e-Commerce website will operate on an operating unit number(channel) specified in the web.config. To change it, change the OU \# below. Note that Fabrikam is “077” in the demo data. You will need to update the “retailServerUrl” inside web.config of the RetailStorefrontWebSite. The following two fields will need to be updated to use the machine name instead of local host:

```xml
<ecommerceControls productUrlFormat="/Pages/ProductDetails/ProductDetails.aspx?itemId={0}" retailServerUrl="http://localhost:35080/RetailServer/V1" operatingUnitNumber="068">
<add key="OperatingUnitNumber" value="068" />
```

## Configure authentication providers
### Authentication providers that you are using

The e-Commerce platform uses OpenID as the mechanism for authentication. You can register any OpenID provider of your choice to the tables below to make this work. You can then log in to test as needed.

1.  Edit the web.config file and change it to the following.

    ```xml
    redirectUrl=https://usnconeboxax1ecom.cloud.onebox.dynamics.com/en/Pages/OauthV2Redirect/OauthV2Redirect.aspx
    ```
    
    The subsequent steps should only be done to register additional providers.

2.  The **Retail Shared Parameters -&gt; Open ID Providers** form can be used to register additional providers.
3.  Run distribution schedule 1110.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
