---
title: Add custom redirect for categories and product pages in cusotomized module
description: This article describes how to implement a custom redirect for category and product pages by extending modules in online SDK.
author: krishnabh
ms.date: 07/24/2025
ms.topic: how-to
audience: Developer
ms.reviewer: adpattanaik
ms.search.region: Global
ms.author: krishnabh
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
Category and product pages may accept extraneous values in their URLs, which can negatively impact SEO by spreading product traffic across multiple URLs. Additionally, this behavior may introduce security risks by allowing unauthorized or inappropriate content within URLs. To mitigate these issues, you can implement custom redirects for category and product pages by extending modules in the online SDK 

## Implementation

To perform a 301 or 302 redirect inside a module, throw a HttpRedirectException within the relevant module. Assign the redirect URL to HttpRedirectException.Location, and set the appropriate HTTP status code (301 or 302)

## Example
The example below demonstrates how to implement a canonical redirect for category pages by extending the default-page-summary module. This approach ensures that if the current page URL differs from the canonicalUrl, the page will redirect to the canonical URL. 
Step 1: Clone the category page-summary module and add custom logic to throw a HttpRedirectException. 

```TS
import { HttpRedirectException } from '@msdyn365-commerce/core-internal'; 

      // if the canonical url is different from the current page url, then redirect via throwing an error also check if request url ends with .c 

        // // verify if context.request.url.requestUrl.href is a category url 

        if (canonicalUrl && context && context.request && context.request.url && canonicalUrl !== context.request.url.requestUrl.href) { 

            const e = new HttpRedirectException(canonicalUrl); 

            e.name = 'HttpRedirectException'; 

            throw e; 

        } 
```
Step2:  Replace the page-summary mdoule in category template with new module. 

## Important Note : Avoid Infinite Redirects
 When implementing bulk redirects in conjunction with custom redirects, exercise caution to prevent infinite redirect loops. Always verify that URLs targeted for client-side or server-side redirection are not themselves sources or destinations in bulk redirect rules. Properly auditing and testing your redirect logic will help you maintain site stability and avoid unnecessary redirect chains that could negatively affect both user experience and SEO. 


## Additional resources

[EX

[Extend a Module](cli-command-reference.md)

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
