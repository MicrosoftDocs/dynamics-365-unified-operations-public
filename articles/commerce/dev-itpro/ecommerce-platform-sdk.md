---
# required metadata

title: e-Commerce platform software development kit (SDK)
description: This topic describes the e-Commerce Platform SDK.
author: kfend
manager: AnnBe
ms.date: 07/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 18101
ms.assetid: c0b1740b-1cbb-47c4-94e8-779cde8411af
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

#  e-Commerce platform software development kit (SDK)

[!include [banner](../includes/banner.md)]

This topic describes the e-Commerce Platform SDK. The e-Commerce Platform SDK consist of the following components:

-   Framework
-   Controls
-   Publishing (only supported in version 1661 and higher: [Support for Service to Service authentication in Retail Server](https://community.dynamics.com/ax/b/axforretail/archive/2016/09/24/support-for-service-to-service-authentication-in-retail-server))
-   Sample ASP.net website

## Use the sample asp.net website


### Download the Retail SDK

The Retail SDK is available in development environments, and in hotfix packages in a Retail SDK folder. For more information see:

- If you get the SDK from a development instance, it is immediately ready for configuration and use. For more information, see [Access instances](../../dev-itpro/dev-tools/access-instances.md). 
- If you get the SDK from a hotfix, it is included in the hotfix package as a zipped folder. Hotfixes are cumulative and include all other fixes. 

We recommend that you put the SDK in a source control system such as Visual Studio Online.

### Use the Retail SDK to create the sample asp.net website
1.  Open Visual Studio in Admin mode. This is necessary for publishing to the inetpub folder.
2.  Open C:\\Microsoft Dynamics AX70\\RetailSdkOnlineStoreOnlineStore.sln contains all the framework components.
3.  The sample online store is available at C:\\Microsoft Dynamics AX70\\RetailSdkSampleExtensionsOnlineStore.
4.  Compile and publish the web store front, from within Visual Studio.
5.  Update the path of the RetailStorefrontWebSite from IIS Manager.
    -  Note that RetailStorefrontWebSite created by the default setup points to C:\\Microsoft Dynamics AX70\\Retail Store Front\\Package.
    -  However, the publishing of the web storefront from RetailSDK will drop the files at C:\\inetpub\\RetailWeb\\Storefront.
    -  Hence, the physical path of the RetailStorefrontWebSite must be updated to point to “C:\\inetpub\\RetailWeb\\Storefront” to access web storefront on the same ports as before. Another option would be to create a new website and have that point to the inetpub location.

6.  Browse to `http://localhost:55080` or access `https://usnconeboxax1ecom.cloud.onebox.dynamics.com/` to see a test asp.net website.

### Enabling anonymous access

e-Commerce websites need to enable anonymous access. This is available as a web.config file in the Commerce Scale Unit web.config under app settings. Please ensure that this is enabled to have the website work. 

`
add key="IsAnonymousEnabled" value="true"
`

### Externally accessing the ASP.net website

The following configuration changes will be required if either of these applies:

-   If you are accessing web storefront from within a browser that is not on the same box as the e-Commerce server.
-   If the e-Commerce server and Commerce Scale Unit are on two different boxes.

You will need to update the “retailServerUrl” inside the web.config file of the RetailStorefrontWebSite. The following two fields will need to be updated to use the machine name instead of local host:

- retailServerUrl=<http://localhost:35080/RetailServer/V1>
- &lt;add key="RetailServerRoot" value="<http://localhost:35080/RetailServer/V1>" /&gt;

If you are accessing the web storefront over HTTPS, then you will need to update the above URLs to the HTTPS equivalent.

### Operating unit or channel configuration

The e-Commerce website will operate on an operating unit number(channel) specified in the web.config. To change it, change the OU \# below. Note that Fabrikam is “077” in the demo data. You will need to update the “retailServerUrl” inside web.config of the RetailStorefrontWebSite. The following two fields will need to be updated to use the machine name instead of local host:

-  `<ecommerceControls productUrlFormat="/Pages/ProductDetails/ProductDetails.aspx?itemId={0}" retailServerUrl="http://localhost:35080/RetailServer/V1" operatingUnitNumber="068">`

-  `<add key="OperatingUnitNumber" value="068" />`

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

