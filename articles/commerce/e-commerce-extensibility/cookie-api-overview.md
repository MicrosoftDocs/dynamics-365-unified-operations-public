---
# required metadata

title: Cookie API overview
description: This topic provides an overview of the application programming interfaces (APIs) in the Microsoft Dynamics 365 Commerce e-Commerce software development kit (SDK) that are used to set and get cookie data.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
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
# Cookie API overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic provides an overview of the application programming interfaces (APIs) in the Microsoft Dynamics 365 Commerce e-Commerce software development kit (SDK) that are used to set and get cookie data.

## Cookie consent

Before cookies can be stored, the user must give consent. The Dynamics 365 Commerce online SDK provides utilities that help guarantee that the read/write operation of a cookie depends on user consent.

##  Cookie APIs

The Dynamics 365 Commerce online SDK provides a set of APIs that access cookies from within the **props.context.request** API, as shown in the following example.

```typescript
get<T>(cookieName: string, isEssential?: boolean): ICookieValue<T>;
set<T>(cookieName: string, cookieValue: T, options?: ICookieSetOptions): void;
remove(cookieName: string): void;
isConsentGiven(): boolean;
setConsentCookie(): void;
deleteConsentCookie(): void;
```

### Obtain user consent

The **setConsentCookie()** API is used to obtain user consent before cookies can be written.

### Determine whether user consent has been given

The **isConsentGiven()** API is used to determine whether user consent has been given.

### Set a cookie

The following example shows how to set a cookie.

```typescript
this.props.context.request.cookies.set<string>('favoriteColor', 'blue');
``` 

If user consent isn't given before this API is called, the SDK maintains a queue of all **set** operations and sets a cookie only after the user gives consent.

### Get the value of a cookie

The following example shows how to get the value of a cookie.

```typescript
const favColor = this.props.context.request.cookies.get<string>('favoriteColor');
```
## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)
