---
title: Add custom redirect for pages inside online SDK
description: Learn how to implement a custom redirect for category and product pages by extending modules in the online SDK.
author: krishnabh
ms.date: 07/24/2025
ms.topic: Application User
audience: 
ms.reviewer: adpattanaik
ms.search.region: Global
ms.author: krishnabh
ms.search.validFrom: 2025-04-07
ms.custom: 
  - bap-template
---

[!include [banner](../includes/banner.md)]

# Add custom redirect for category and product pages in the online SDK

This article describes how to implement server-side redirects (301 or 302) for category and product pages in Microsoft Dynamics 365 Commerce by extending existing modules in the online SDK.

## Why use custom redirects?

Category and product pages  allow extraneous values in their URLs. While functional, such URLs may be undesirable from a user experience perspective. You can ensure clean, canonical URLs by implementing custom redirects.

## Prerequisites

- A working Dynamics 365 Commerce online SDK environment.
- Familiarity with extending modules.

## Implementation

**Step 1:** Clone the **default-page-summary** module and implement custom logic to throw a HttpRedirectException. Below is a sample code to throw a HttpRedirectException error when the canonical URL for the category page does not match the it's request URL, causing a redirect. 

**src\modules\default-page-summery-extension\default-page-summery-extension.tsx**

```typescript

import { HttpRedirectException } from '@msdyn365-commerce/core-internal';

if (canonicalUrl && context && context.request && context.request.url && canonicalUrl !== context.request.url.requestUrl.href) {
    const e = new HttpRedirectException(canonicalUrl);
    e.name = 'HttpRedirectException';
    throw e;
}
});
```

**Step 2:** Extend the **category-page-summary-module**. Modify the definition of the category-page-summary-extension module to point to your custom view.

**src\modules\category-page-summary-extension\category-page-summary-extension.definition.json**
```json

"module": {
		"view": "../default-page-summery-extension/default-page-summery-extension"
	}

```

**Step 3:**  Replace the **category-page-summary** module with the **category-page-summary-extension** module in the category template. 





> [!NOTE]
> **Avoid Infinite Redirects** : When implementing bulk redirects alongside custom redirects, exercise caution to prevent infinite redirect loops. 
>Always verify that URLs set for client-side or server-side redirection are not also listed as sources or destinations in bulk redirect rules. 


## Additional resources

[Module library overview](../starter-kit-overview.md)

[Page Summary Module](../dev-itpro/page-summary-module.md)

[Meta Tags Module](../dev-itpro/metatags-module.md)

[Default Page Module](../dev-itpro/default-page-module.md)

[Extend Module Definition](extend-module-definition.md)

[Create New Module](create-new-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
