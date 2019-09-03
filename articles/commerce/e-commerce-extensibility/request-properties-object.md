---
# required metadata

title: Request properties object
description: This topics covers the request properties object in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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

This topics covers the request properties object in Dynamics 365 Commerce.

## Overview

The request properties object represents an HTTP request and includes properties for data such as the requested URL, locale, device, user, cookie, and query string parameters. Modules can access a read-only request context object named **this.props.context** to get the request information, and can change module behavior as needed.  

## Example
The following example shows how to access the request properties object from within the request context:

```
if (this.props.context.request.user.isAuthenticated) {
    userName = this.props.context.request.user.signinName ? this.props.context.request.user.signinName : '';
    firstName = this.props.context.request.user.firstName ? this.props.context.request.user.firstName : '';
    lastName = this.props.context.request.user.lastName ? this.props.context.request.user.lastName : '';
}      
```

## General properties

* **url** - Provides the requested URL
* **locale** - The locale context (example "en-us")
* **textDirection** - The text direction, possible values "rtl" and "ltr"
* **sitePath** - The site's full path
* **device** - Device the request came from
  * **Type** - Device type (example: 'pc')
* **user** - Information about the user including:
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
* **query** - List of query string parameters
* **cookies** - Cookie information

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
