---
title: E-commerce platform software development kit (SDK)
description: This article describes the e-commerce Platform SDK.
author: josaw1
ms.date: 08/01/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

#  E-commerce platform software development kit (SDK)

[!include [banner](../includes/banner.md)]

This article describes the e-commerce Platform SDK. The e-commerce Platform software development kit (SDK) consists of the following components:

-   Framework
-   Controls
-   Publishing (only supported in version 1661 and higher: [Support for Service to Service authentication in Retail Server](https://community.dynamics.com/ax/b/axforretail/archive/2016/09/24/support-for-service-to-service-authentication-in-retail-server))
-   Sample ASP.NET website

## Use the sample ASP.NET website


### Download the Retail SDK

The Retail SDK is available in development environments, and in hotfix packages in a Retail SDK folder.

- If you get the SDK from a development instance, it's immediately ready for configuration and use. For more information, see [Access instances](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md). 
- If you get the SDK from a hotfix, it's included in the hotfix package as a zipped folder. Hotfixes are cumulative and include all other fixes. 

We recommend that you put the SDK in a source control system such as Visual Studio Online.

### Use the Retail SDK to create the sample ASP.NET website
1.  Open Visual Studio in Admin mode. This step is necessary for publishing to the inetpub folder.
2.  Open C:\\Microsoft Dynamics AX70\\RetailSdkOnlineStoreOnlineStore.sln contains all the framework components.
3.  The sample online store is available at C:\\Microsoft Dynamics AX70\\RetailSdkSampleExtensionsOnlineStore.
4.  Compile and publish the web store front, from within Visual Studio.
5.  Update the path of the RetailStorefrontWebSite from Internet Information Services (IIS) Manager.
    -  Note that RetailStorefrontWebSite created by the default setup points to C:\\Microsoft Dynamics AX70\\Retail Store Front\\Package.
    -  However, the publishing of the web storefront from RetailSDK drops the files at C:\\inetpub\\RetailWeb\\Storefront.
    -  Hence, the physical path of the RetailStorefrontWebSite must be updated to point to C:\\inetpub\\RetailWeb\\Storefront to access web storefront on the same ports as before. Another option would be to create a new website and have that point to the inetpub location.
6.  Browse to `http://localhost:55080` or access `https://usnconeboxax1ecom.cloud.onebox.dynamics.com/` to see a test ASP.NET website.

### Enable anonymous access

E-Commerce websites must allow anonymous access to work correctly. Ensure that anonymous access is enabled by adding the following key in the Commerce Scale Unit web.config file under app settings.

`
add key="IsAnonymousEnabled" value="true"
`

### Externally accessing the ASP.NET website

The following configuration changes are required if either of these conditions applies:

-   You're accessing web storefront from within a browser that isn't on the same box as the e-commerce server.
-   The e-commerce server and Commerce Scale Unit are on two different boxes.

You need to update the “retailServerUrl” inside the web.config file of the RetailStorefrontWebSite. The following two fields need to be updated to use the machine name instead of local host:

```xml
retailServerUrl=<http://localhost:35080/RetailServer/V1>
<add key="RetailServerRoot" value="<http://localhost:35080/RetailServer/V1>" />
```

If you're accessing the web storefront over HTTPS, then you need to update the above URLs to the HTTPS equivalent.

### Operating unit or channel configuration

The e-commerce website operates on an operating unit number (channel) specified in the web.config file. To change it, update the `operatingUnitNumber` as shown in the following example. Fabrikam is "077" in the demo data. You need to update the “retailServerUrl” inside web.config of the RetailStorefrontWebSite. The following two fields need to be updated to use the machine name instead of local host:

```xml
<ecommerceControls productUrlFormat="/Pages/ProductDetails/ProductDetails.aspx?itemId={0}" retailServerUrl="http://localhost:35080/RetailServer/V1" operatingUnitNumber="068">
<add key="OperatingUnitNumber" value="068" />
```

## Configure authentication providers
### Authentication providers that you're using

The e-commerce platform uses OpenID as the mechanism for authentication. You can register any OpenID provider of your choice in the following tables to make this work. You can then log in to test as needed.

1.  Edit the web.config file and change it to the following.

    ```xml
    redirectUrl=https://usnconeboxax1ecom.cloud.onebox.dynamics.com/en/Pages/OauthV2Redirect/OauthV2Redirect.aspx
    ```
    
    The subsequent steps should only be done to register additional providers.

2.  The **Retail Shared Parameters -&gt; Open ID Providers** form can be used to register additional providers.
3.  Run distribution schedule 1110.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
