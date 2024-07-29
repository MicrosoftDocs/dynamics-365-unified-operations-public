---
title: Cookie API overview
description: This article provides an overview of the application programming interfaces (APIs) in the Microsoft Dynamics 365 Commerce online software development kit (SDK) that are used to set and get cookie data.
author: samjarawan
ms.date: 07/26/2024
ms.topic: overview
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template: 
---
# Cookie API overview

[!include [banner](../includes/banner.md)]

This article provides an overview of the application programming interfaces (APIs) in the Microsoft Dynamics 365 Commerce online software development kit (SDK) that are used to set and get cookie data.

## Cookie consent

Before cookies can be stored, the user must give consent. The Dynamics 365 Commerce online SDK provides utilities that help guarantee that the read/write operation of a cookie depends on user consent.

##  Cookie APIs

The Dynamics 365 Commerce online SDK provides a set of APIs that access cookies from within the **props.context.request.cookies** API, as shown in the following interface.

```typescript
export interface ICookieContext {
    get<T>(cookieName: string): ICookieValue<T>;
    set<T>(cookieName: string, cookieValue: T, options?: ICookieSetOptions): void;
    getCartCookie(): string;
    setCartCookie(cart: Cart, isAuthenticated: boolean): void;
    getCheckoutCartCookie(): string;
    setCheckoutCartCookie(cart: Cart, isAuthenticated: boolean): void;
    removeCheckoutCartCookie(): void;
    remove(cookieName: string): void;
    isConsentGiven(): boolean;
    setConsentCookie(): void;
    deleteConsentCookie(): void;
    getTargetIdCookie(): string;
}
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

[Platform settings file](platform-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Interactive components overview](interactive-components.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Configure module properties to be shown based on context](configure-properties-context.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
