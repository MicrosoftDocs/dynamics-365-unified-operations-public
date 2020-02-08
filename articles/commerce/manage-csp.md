---
# required metadata

title: Manage Content Security Policy (CSP)
description: This topic describes how to manage Content Security Policy (CSP) in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience:  Developer
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
# Manage Content Security Policy (CSP)


[!include [banner](includes/banner.md)]

This topic describes how to manage Content Security Policy (CSP) in Microsoft Dynamics 365 Commerce.

## Overview

CSP is an additional layer of security that helps detect and mitigate some types of web attacks. The purpose of these attacks can range from data theft, to site defacement, to the distribution of malware. CSP provides an extensive set of policy directives that help you control the resources that a site page is allowed to load. Each directive defines the restrictions for a specific type of resource.

When CSP is turned on for an e-Commerce site, it helps enhance security by blocking connections, scripts, fonts, and other types of resources that originate from unknown or malicious sources. In Dynamics 365 Commerce, CSP is turned on by default. However, it will likely require additional configuration for most sites. The Dynamics 365 Commerce online software development kit (SDK) provides a default list of allowed source URLs that style, script, and application programming interface (API) calls can be made from. You can edit this list on the **Extensibility** tab in Commerce.

For more information about CSP, see [Content Security Policy Reference](https://content-security-policy.com/).

## CSP directives in Commerce

The following CSP directives can be used on Commerce sites.

| Directive   | Description |
|-------------|-------------|
| child-src   | This directive defines valid sources of web workers and nested browsing contexts that are loaded by using elements such as **&lt;frame&gt;** and **&lt;iframe&gt;**. |
| connect-src | This directive defines the URLs that AJAX requests can be made from. |
| font-src    | This directive defines valid sources of fonts. |
| img-src     | This directive defines valid sources of images. |
| media-src   | This directive defines valid sources of audio and video, such as HTML5 **&lt;audio&gt;** and **&lt;video&gt;** elements. |
| object-src  | This directive defines valid sources of plug-ins, such as **&lt;object&gt;**, **&lt;embed&gt;**, and **&lt;applet&gt;** elements. |
| script-src  | This directive defines valid sources of JavaScript. |
| style-src   | This directive defines valid sources of stylesheets. |

### Example: Configure a CSP directive

The following example shows how to configure a CSP directive so that an external script can be called from your site.

1. In Commerce, go to your site.
1. Select **Site Management**, and then select the **Extensibility** tab.
1. On the **Content Security Policy** tab, under **script-src**, select **Add**, and then enter the full URL of the external script that should be called.

    ![URL for an external script on the Content Security Policy tab](media/content-security-policy.png)

1. Select **Save and Publish**.

## Interpret and fix CSP errors

When you first configure CSP for a site, some pages probably won't be loaded at all or won't work as intended, because CSP is blocking external connections, scripts, fonts, and other types of resources from being loaded. Fortunately, CSP logs some helpful errors that you can use to fix, tune, and clean up unwanted or unneeded requests.

The following illustration shows an example of CSP errors in a web browser's developer tools.

![CSP errors in a web browser's developer tools](media/content-security-policy-errors.png)

There are two CSP errors in this example:

- The **Eval** function is blocked by default, because it can cause arbitrary JavaScript execution. To allow this function, add **'unsafe-eval'** to your site's **script-src** directive. The single quotation marks are required.
- The external stylesheet is blocked. To allow a stylesheet to be loaded from an external domain, add the URL to your site's **style-src** directive.

The following screenshot shows what the fixed settings look like on the **Content Security Policy** tab in Commerce.

![Fixed settings on the Content Security Policy tab](media/content-security-policy-fixed.png)

## Update page mocks that use CSP

If you're testing modules by using the online SDK in a development environment, you can also add CSP by using page mocks. In a page mock, you must either add a top-level **"appContext"** property or go to the existing top-level **"appContext"** property, and create a property under it that is named **"contentSecurityPolicy"**. There, you can add key/value pairs of directives to policies, as shown in the following example.

```
"appContext": {
	"contentSecurityPolicy": {
		"script-src": ["https://www.w3schools.com/js/myScript.js"],
		"font-src": ["https://*.commerce.dynamics.com"]
	}
}
```

> [!NOTE]
> If you add CSP policies in a page mock, the page mock won't include any of the default CSP policies that are provided by the platform.

You can turn off CSP in a page mock by using the following code.

```
"appContext": {
	"contentSecurityPolicy": {
		"disableContentSecurityPolicy": true
	}
}
```

## Turn off CSP for a site

To prevent CSP from applying policies to your site, you can turn it off for that site.

1. In Commerce, go to your site.
1. Select **Site Management**, and then select the **Extensibility** tab.
1. On the **Content Security Policy** tab, select the **Disable content security policy** check box.

    ![Disable content security check box on the Content Security Policy tab](media/content-security-policy-disable.png)

1. Select **Save and Publish**.

## Additional resources

[Manage e-Commerce users and roles](manage-ecommerce-users-roles.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

[Search engine optimization (SEO) considerations for your site](search-engine-optimization-considerations.md)
