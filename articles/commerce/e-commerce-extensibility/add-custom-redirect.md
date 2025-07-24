---
title: Add custom redirect for pages inside online SDK
description: This article describes how to implement a custom redirect for category and product pages by extending modules in online SDK.
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

# Add custom redirect for pages inside online SDK

This article demonstrates how to do a custom redirect for pages like categories, products etc from online sdk by [ extending existing modules](clone-starter-module.md)

## Implementation

To perform a 301 or 302 redirect inside a module, throw a HttpRedirectException within the relevant module. Assign the redirect URL to **HttpRedirectException.Location**, and set the appropriate http status code(301 or 302) to **HttpRedirectException.statusCode**.

## Example : Implement Redirect for category pages to sanitize the garbage values in the url and redirect to a canonical url.


Category and product pages can accept extraneous values in their URLs which may not be preferable by some customers. In that case, you can implement custom redirects for category and product pages by extending modules in the online SDK.

The example below demonstrates how to implement a canonical redirect for category pages by extending the default-page-summary module. This approach ensures that if the current page URL differs from the canonicalUrl, the page will redirect to the canonical URL.

**Step 1:** Clone the **default-page-summary** module and implement custom logic to throw a HttpRedirectException. Added HttpRedirectException logic in default-page-summery-extension.tsx.// This will throw HttpRedirectException error when canonical url for the category doesn't match the requesturl causing a redirect.

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
**Step 2:** Extend **category-page-summary-module**. update its definition to use **default-page-summary-extension.tsx** as view.

**src\modules\category-page-summary-extension\category-page-summary-extension.definition.json**

```json

"module": {
		"view": "../default-page-summery-extension/default-page-summery-extension"
	}

```

**Step 3:**  Replace the category-page-summary module with new module in category template. 





> [!NOTE]
> **Avoid Infinite Redirects**: when implementing bulk redirects in conjunction with custom redirects, exercise caution to prevent infinite redirect loops.
> Always verify that URLs targeted for client-side or server-side redirection are not themselves sources or destinations in bulk redirect rules.


## Additional resources

[Module library overview](starter-kit-overview.md)

[Page Summary Module](page-summary-module.md)

[Meta Tags Module](metatags-module.md)

[Default Page Module](default-page-module.md)

[Extend Module Definition](extend-module-definition.md)

[Create New Module](create-new-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
