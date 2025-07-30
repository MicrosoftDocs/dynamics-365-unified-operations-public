---
title: Redirect category and product pages to canonical URLs (preview)
description: Learn how to redirect category and product pages to canonical URLs by extending modules using the Microsoft Dynamics 365 Commerce online SDK.
author: krishnabh
ms.date: 07/30/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: krishnabh
ms.search.validFrom: 2025-04-07
ms.custom: 
  - bap-template
---

# Redirect category and product pages to canonical URLs (preview)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article explains how to redirect category and product pages to canonical URLs by extending modules using the Microsoft Dynamics 365 Commerce online SDK.

## Importance of canonical URLs 

Dynamics 365 Commerce category and product pages can be accessed through URLs that include unnecessary or random segments. While these URLs are technically valid, they can lead to:

- Duplicate content issues.
- Poor search engine optimization (SEO) performance.
- Confusing user experiences.

Redirecting to canonical URLs helps maintain a consistent structure, improves search engine indexing, and enhances overall site usability.   

## Prerequisites

- A functioning Dynamics 365 Commerce online SDK environment.
- Familiarity with extending modules.

## How canonical redirects work 

A canonical URL redirect works in the following ways:  

- Detects when the requested URL doesn't match the canonical format.  
- Throws an instance of the HttpRedirectException class with the correct URL set in the **Location** property.  
- Halts further page rendering and initiates a redirection to the canonical URL.  

If a user accesses a product page using a noncanonical URL, the Commerce page module should detect this action and redirect the user to the correct canonical URL. 

In the following URL example, the custom module logic detects the extraneous `<unnecessaryparameter>` segment of the requested URL and issues a redirect to the clean, canonical URL. 

- **Requested URL**: `https://www.fabrikam.com/womens-clothing/<unnecessaryparameter>/45678.p` 
- **Canonical URL**: `https://www.fabrikam.com/womens-clothing/45678.p` 

## Implement a custom redirect within a module 

To implement a custom redirect within a module, you add custom redirect logic that throws an instance of the HttpRedirectException class at the appropriate location in the module. This action halts the rendering of subsequent modules and initiates a redirect to the URL specified in the **Location** property of the HttpRedirectException class. 

## Example

All e-commerce site pages hosted on the Dynamics 365 Commerce domain include a canonical URL in the page metadata by default. To implement a redirect based on this canonical URL, you must first identify the module responsible for generating it and insert your redirect logic there.

In this example, the category page template uses the category page summary module to generate its canonical URL. The category page summary module references the default page summary module view file. Adding conditional redirect logic to the default page summary module ensures that the redirect occurs wherever category pages are accessed. 

**Step 1 - Customize the default page summary module**: In the default-page-summary-extension.tsx file (src\modules\default-page-summery-extension\default-page-summary-extension.tsx), we customize the default page summary module to implement custom logic that throws the HttpRedirectException error, as shown in the following code sample.

```typescript
import { HttpRedirectException } from '@msdyn365-commerce/core-internal';

if (canonicalUrl && context && context.request && context.request.url && canonicalUrl !== context.request.url.requestUrl.href) {
    const e = new HttpRedirectException(canonicalUrl);
    e.StatusCode = 302 
    throw e;
}
});
```

**Step 2 - Customize the category page summary module**: In the category-page-summary-extension.definition.json file (src\modules\category-page-summary-extension\category-page-summary-extension.definition.json), we customize the category page summary module and update the module definition to point to the custom view, as shown in the following code sample.

```json
"module": {
		"view": "../default-page-summary-extension/default-page-summary-extension"
	}
```

**Step 3 - Edit the category page template**:  In the category page template in Dynamics 365 Commerce site builder, we substitute references to the category page summary module with references to the custom category page summary extension module. 

> [!NOTE]
> When you implement bulk redirects alongside canonical redirects, take care to avoid creating infinite redirect loops. 

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Page summary module](../dev-itpro/page-summary-module.md)

[Meta tags module](../dev-itpro/metatags-module.md)

[Default page module](../dev-itpro/default-page-module.md)

[Extend module definition](extend-module-definition.md)

[Create new module](create-new-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
