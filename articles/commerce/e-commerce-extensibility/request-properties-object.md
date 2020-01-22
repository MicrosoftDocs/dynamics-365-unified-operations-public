---
# required metadata

title: Request properties object
description: This topic covers the request properties object in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Request properties object

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers the request properties object in Microsoft Dynamics 365 Commerce.

## Overview

The request properties object represents an HTTP request and includes various data properties, such as the requested URL, locale, device, user, cookies, and query string parameters. To get the request information, modules can access a read-only request context object that is named **this.props.context**, and they can change module behavior as required.

## Example

The following example shows how to access the request properties object from within the request context.

```
if (this.props.context.request.user.isAuthenticated) {
    userName = this.props.context.request.user.signinName ? this.props.context.request.user.signinName : '';
    firstName = this.props.context.request.user.firstName ? this.props.context.request.user.firstName : '';
    lastName = this.props.context.request.user.lastName ? this.props.context.request.user.lastName : '';
}
```

## General properties

* **url** – The requested URL.
* **locale** – The locale context (for example, **"en-us"**).
* **textDirection** – The text direction (the possible values are **"rtl"** and **"ltr"**).
* **sitePath** – The full path of the site.
* **device** – The device that the request came from.

  * **Type** – The device type (for example, **"pc"**).

* **user** – Information about the user. The following properties are included:

    * **token**
    * **isAuthenticated**
    * **signinURL**
    * **signoutURL**
    * **signUpUrl**
    * **editProfileUrl**
    * **signinName**
    * **name**
    * **firstName**
    * **lastName**
    * **emailAddress**
    * **customerAccountNumber**

* **query** – A list of query string parameters.
* **cookies** – Cookie information.

## Interface

```typescript
interface IParsedQSP<TValue> {
    hasValue: boolean;
    isTruthy: boolean;
    value: TValue | undefined;
}

interface IRequestContextUrl {
    serverUrl: string;
    serverPageUrl: string;
    requestUrl: URL;
    staticCdnUrl: string;
}

interface IRequestContextParams {
    mock?: string;
    isDebug: boolean;
    isEditor: boolean;
    concatJs: IParsedQSP<boolean | string | number | undefined>;
    theme: string;
}

interface IRequestContextDevice {
    Type: string;
}

interface IRequestContextUser {
    token: string;
    isAuthenticated: boolean;
    signInUrl?: string;
    signOutUrl?: string;
    signUpUrl?: string;
    editProfileUrl?: string;
    signinName?: string;
    name?: string;
    firstName?: string;
    lastName?: string;
    emailAddress?: string;
    customerAccountNumber?: string;
}

interface IRequestContextFeatures {
    [switchName: string]: boolean;
}

interface IRequestContextHeaders {
    readonly [header: string]: string;
}

interface IRequestContext {
    url: IRequestContextUrl;
    locale: string;
    market?: string;
    textDirection: string;
    sitePath?: string;
    params: IRequestContextParams;
    device: IRequestContextDevice;
    user: IRequestContextUser;
    app: IGeneric<IAny>;
    query?: IDictionary<string>;
    apiSettings: ICommerceApiSettings;
    channel?: IChannelConfiguration;
    gridSettings?: IGridSettings;
    urlTokens: IUrlTokens;
    operationId: string;
    features: IRequestContextFeatures;
    pageData: IGeneric<IAny>;
    headers: IRequestContextHeaders;
    cookies: ICookieContext;
}
```

## Test a module with authenticated signed-in state

Some modules may require the state to be "signed-in." To test these modules, a test page mock can be created with user authentication information.

To get started, follow these steps.

1. Load the e-Commerce web page you are working on and sign in or create a new account.
1. Open up the web browser debugging tools. For example, when using Google Chrome enable the developer tools with the F12 key. 
1. Type `___initialData___.requestContext.user` into console to get the user info. (User info is available in the Global JS variable `___initialData___.requestContext.user`.)
1. Add the module to be tested into a page mock.
1. Inside the **renderingContext** section of the page mock, add the **userContext** section below. 
1. Update user information taken from the web browser debugging tools.

```
"userContext": {
    "token": "<TOKEN>",
    "isAuthenticated": true,
    "signInUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signin",
    "signOutUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signout",
    "signUpUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signup",
    "editProfileUrl": "https://dev.fabrikam.com/fedev/_msdyn365/editprofile",
    "signinName": "<User Name>",
    "firstName": "<User First Name>",
    "lastName": "<User Last Name>",
    "tenantId": "",
    "customerAccountNumber": "<User Account Number(HQ)>",
     "name": "<User Name>",
     "emailAddress": "<User Email Address>"
},
```

The user information can now be obtained in the React component from within the **this.props.context.request.user** object.

Example page mock:
```
{
    "exception": null,
    "pageRoot": {
        "id": "core-root_0",
        "typeName": "core-root",
        "modules": {
            "body": [
                {
                    "id": "default-page_0",
                    "typeName": "default-page",
                    "modules": {
                        "primary": [
                            {
                                "id": "ProductFeature__0",
                                "typeName": "product-feature",
                                "config": {
                                    "imageAlignment": "left",
                                    "productTitle": "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses",
                                    "productDetails": "High-quality and pioneered with the perfect blend of timeless classic and modern technology with hint of old school glamor.",
                                    "productImage": {
                                        "src" : "https://bit.ly/33cMGxr",
                                        "altText" : "Retro Horn Rimmed Keyhole Nose Bridge Round Sunglasses"
                                    },
                                    "buttonText": "Buy Now"
                                }
                            }
                        ]
                    }
                }
            ]
        }
    },
    "renderingContext": {
        "gridSettings": {
            "xs": {
                "w":767
            },
            "sm": {
                "w":991
            },
            "md": {
                "w":1199
            },
            "lg": {
                "w":1599
            },
            "xl": {
                "w":1600
            }
        },        
        "staticContext": {
            "staticCdnUrl": "/_scnr/"
        },
        "locale": "en-us",
        "userContext": {
            "token": "<TOKEN>",
            "isAuthenticated": true,
            "signInUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signin",
            "signOutUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signout",
            "signUpUrl": "https://dev.fabrikam.com/fedev/_msdyn365/signup",
            "editProfileUrl": "https://dev.fabrikam.com/fedev/_msdyn365/editprofile",
            "signinName": "<User Name>",
            "firstName": "<User First Name>",
            "lastName": "<User Last Name>",
            "tenantId": "",
            "customerAccountNumber": "<User Account Number(HQ)>",
            "name": "<User Name>",
            "emailAddress": "<User Email Address>"
        },
    },
    "statusCode": 200
}
```

## Additional resources

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)
