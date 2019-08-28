---
# required metadata

title: Work with Cookies
description: This topic provides an overview of the Dynamics 365 Commerce e-Commerce SDK APIs to set and get Cookie data.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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
# Work with Cookies

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic provides an overview of the Dynamics 365 Commerce online SDK APIs to set and get Cookie data.

## Cookie consent
Before cookies can be stored the end user must provide consent.  The SDK provides utilites to ensure read/write operation of cookie based on the user approves the writing of cookies.

##  Cookie APIs
The SDK provides the following set of APIs to access Cookies from within the `props.context.request` API

```
    get<T>(cookieName: string, isEssential?: boolean): ICookieValue<T>;
    set<T>(cookieName: string, cookieValue: T, options?: ICookieSetOptions): void;
    remove(cookieName: string): void;
    isConsentGiven(): boolean;
    setConsentCookie(): void;
    deleteConsentCookie(): void;
```

## Getting user consent
The **setConsentCookie()** API is used to acquire user consent before cookies can be written. The **isConsetGiven()** api can be used to determine if consent has been given.

## Setting a cookie
The following is an example usage to set a cookie:
`this.props.context.request.cookies.set<string>('favoriteColor', 'blue');`. If consent is not provided before calling this api, sdk maintian a queue of all set opertion and set all these cookie onces user provides consent

## Getting a cookie
The following is an example usage to get the value of a cookie
`const favColor = this.props.context.request.cookies.get<string>('favoriteColor');`
