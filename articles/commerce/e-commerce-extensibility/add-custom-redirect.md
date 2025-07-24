---
title: Add custom redirect for pages inside online SDK
description: Learn how to implement a custom redirect for category and product pages by extending modules in the online SDK.
author: krishnabh
ms.date: 07/24/2025
ms.topic: how-to
audience: Application User
ms.reviewer: adpattanaik
ms.search.region: Global
ms.author: krishnabh
ms.search.validFrom: 2025-04-07
ms.custom: 
  - bap-template
---

[!include [banner](../includes/banner.md)]

# Add custom redirect for category and product pages in the online SDK

This article covers custom redirects and describes how to implement them in E-commerce Online SDK with a sample UseCase.

## Why use custom redirects?

As part of the e-commerce SDK, we provide customers with the flexibility to build and customize their own sites. By default, category and product pages can contain arbitrary or random values in their URLs. Although these URLs function correctly, they may not meet customer expectations for a clean and professional user experience. Implementing custom redirects helps ensure clean URLs, resulting in an improved user experience. 

## Prerequisites

- A working Dynamics 365 Commerce online SDK environment.
- Familiarity with extending modules.


## Implementing an HTTP Redirect within a Module 

Custom Redirect inside a module can be implemented by throwing a "HttpRedirectException" error wherever customer wants to do a redirect inside the relevant module. This will stop the rendering of the subsequent modules and does a redirect to the "Location" value passed to the "HttpRedirectException" error. 

- Begin by cloning or creating a new module. Ensure you define the custom redirect URL as needed for your use case. 

- In the module's view file (.tsx), implement the logic required to conditionally trigger a redirect based on your criteria. 

- When a redirect is necessary, throw a HttpRedirectException. Assign the desired redirect URL to HttpRedirectException.location and specify the redirect type using HttpRedirectException.statusCode. 

- The HttpRedirectException can be imported from the core-internal package.



## Sample Implementation of custom redirect for category pages

### Redirect a category page to its canonical URL

If a page request URL differs from its canonical URL, issue a redirect to the canonical version. For example:

Request URL: https://www.fabrikam.com/womens-clothing/garbagevalue/dresses

Canonical URL: https://www.fabrikam.com/womens-clothing/dresses

In this case, the module detects the mismatch and triggers a redirect to the clean canonical URL.


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
