---
# required metadata

title: Cookie API overview
description: This topic provides an overview of the Dynamics 365 Commerce e-Commerce SDK APIs used to set and get cookie data.
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
# Cookie API overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic provides an overview of the Dynamics 365 Commerce online software development kit (SDK) APIs used to set and get cookie data.

## Cookie consent

Before cookies can be stored, the end user must provide consent. The SDK provides utilities that ensure the read/write operation of a cookie is contingent on user consent.

##  Cookie APIs

The Commerce online SDK provides the following set of APIs that access cookies from within the `props.context.request` API, as in the following example.

```
    get<T>(cookieName: string, isEssential?: boolean): ICookieValue<T>;
    set<T>(cookieName: string, cookieValue: T, options?: ICookieSetOptions): void;
    remove(cookieName: string): void;
    isConsentGiven(): boolean;
    setConsentCookie(): void;
    deleteConsentCookie(): void;
```

### Get user consent

The **setConsentCookie()** API is used to obtain user consent before cookies can be written. The **isConsetGiven()** API can be used to determine if consent has been given.

### Set a cookie

The following example shows how to set a cookie.

`this.props.context.request.cookies.set<string>('favoriteColor', 'blue');` 

If consent is not provided before calling this API, the SDK maintains a queue of all set operations and only sets the cookie once the user provides consent.

### Get the value of a cookie

The following example shows how to get the value of a cookie.

`const favColor = this.props.context.request.cookies.get<string>('favoriteColor');`
