---
# required metadata

title: Best practices for Dynamics 365 Commerce development 
description: This topic describes some best practices to follow when developing Dynamics 365 Commerce customizations. 
author: samjarawan
manager: annbe
ms.date: 10/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Best practices for Dynamics 365 Commerce development 

[!include [banner](../includes/banner.md)]

This topic describes some best practices to follow when developing Dynamics 365 Commerce customizations.

The Dynamics 365 Commerce platform provides a rich online software development kit (SDK) for developer extensibility. Custom modules, data actions, and themes can be created, or modules from the Commerce [module library](../starter-kit-overview.md) can be extended. It is important to consider web site performance when building Commerce customizations. Standard best practices used for website development are applicable including minimizing HTML, JavaScript, and CSS files, and optimizing images.

## Infrastructure setup

The [Dynamics 365 Commerce ecosystem](../commerce-architecture.md) comprises various subsystems including Commerce headquarters, Commerce Scale Unit, the web storefront that includes the Node rendering service, Commerce site builder, and the product recommendations services. For best performance, the various components should all be deployed to the same region. The specific region decision should be made in accordance with the customer's regional location.

> [!NOTE]
> Commerce Scale Unit allows you to select a specific region during setup.

## Minimize HTML, CSS, and JavaScript file sizes

The Dynamics 365 online SDK provides development extensions that use TypeScript and Sassy Cascading Style Sheets (SCSS) files. When a configuration package is built using the [yarn msdyn365 pack](cli-command-reference.md#pack) command, or the Node server is started on a local development environment using the [yarn start](setup-dev-environment.md#run-your-node-app) command, the TypeScript and SCSS files will compile down to JavaScript and Cascading Style Sheets (CSS) files, respectively. These files are also minified to reduce network bandwidth.

You should ensure that extra, unused JavaScript and CSS files are not included in your extension package. Some tools are listed at the bottom of this document to help measure page load times and can help in identifying problem areas with CSS and JavaScript. Refer to the [Tools for performance analysis](#tools-for-performance-analysis) section laster in this document to find a list of tools that can help you measure page load times and can help in identifying problem areas with CSS and JavaScript.

### Reduce JavaScript by excluding unused modules

Dynamics 365 Commerce comes with a large set of modules referred to as the Commerce [module library](../starter-kit-overview.md). If there are modules that won't be used on an e-Commerce site, they can be excluded to reduce the JavaScript chunk size. The excluded modules will not be rendered on the live e-Commerce site or available within Commerce site builder when authoring pages.

Modules can be excluded by adding the module name to the **excludeModules** property in the SDK's "/src/settings/platform.settings.json" file, as shown in the following example.

```JSON
{

    "excludeModules": ["<EXCLUDED_MODULE_NAME1>","<EXCLUDED_MODULE_NAME2>"]

}
```

You can verify that the module was successfully excluded by comparing the chunk size displayed after a build, or by testing the module in a development environment. For the latter method, you can confirm that the excluded module is not rendered by using the URL `http://localhost:4000/modules?type=<your-module-name>` (after running the Node server by using the "yarn start" command).

## Optimize images

One of the biggest performance hits to a web page can be the downloading of images. You should use CSS whenever possible to generate images for items such as buttons, but in cases where you need marketing or product images you should upload images to the Commerce site builder [Media Library](../dam-overview.md). Images uploaded to the Media Library should be of high quality and resolution to cover all web site usage scenarios. Images served from the Media Library will automatically be resized using an image resizer service.

### Image resizer service

When rendered inside of a module, served images are processed by an image resizer service included in the Commerce rendering engine. This is important for responsive design because as the screen size gets smaller, images will automatically be scaled down to the optimum size for each particular module.

It's important to follow some guidelines to ensure that images are resized correctly. Modules can specify images sizes for particular view ports in the **theme.settings.json** file. For more information, see [Configure theme settings](configure-theme-settings.md).

When building modules with images, the HTML should always include the width and height parameters. If the width and height are not provided, image caching will not be optimized through the image resizer.

### Image types and file sizes

There are three aspects that are important when determining the file size of an image:
- The resolution of the image (width and height).
- How the image is encoded (JPEG, GIF, or PNG). 
- The quality parameter (JPEG only). 

JPEG uses lossy compression that decreases the file size by discarding image detail. The amount of detail discarded is controlled by the quality parameter, which is a number between 0 and 100, with 100 being the best quality. A lower quality parameter number results in a lower quality image, but also a smaller file size. 

PNG is a lossless format, so no image detail is lost but the image file size will be larger. For images with text, sharp lines, or color gradients, PNG may be a better choice because the JPEG format may show undesirable artifacts as a result of the lossy compression. 

GIF is also a lossless format, but it only supports 256 colors in a single image. For images with text or sharp lines that also don't have many colors, GIF may be a better format choice over PNG or JPEG. GIF also has support for simple animations.

Ultimately, the goal is to find the right balance to maintain image quality while keeping the image size as small as possible.

## Cache configuration

Caching is often used on static content that doesn't often change, such as images, product content, and JavaScript and CSS files. Some scenarios may require custom cache settings to achieve the best performance results.

### Image caching 

The default content delivery network (CDN) cache time for images is set to 5 minutes. This means that after 5 minutes the next request to get a specific image will need to be retrieved from the origin, and so will be slower. Increasing the cache time setting is possible, but it must be done by opening a support ticket.

### Data caching

Product-specific data is cached in the e-Commerce rendering Node layer. Caching times are different for each entity type and can be configured inside of the **cache.settings.json** file in the SDK "/src/settings/" directory.  For more information, see [Data cache settings](data-action-cache-settings.md).

## Browser hint meta tags

Browser hint meta tags such as **preconnect** and **dns-prefetch** can be used to tell browsers what resources are needed ahead of time to render a page. Such tags will cause a browser to initiate network connections before it typically would, to make time-expensive network calls earlier. This is useful for adding additional rendering of image, font, or file endpoints used within a page.

The **preconnect** browser hint meta tag can be used if a page relies on resources coming from external origins or domains to initiate a TCP connection. This will cause DNS lookup, TCP handshake, and TLS negotiation to happen before the reference in the HTML document.

The following is an example of a **preconnect** meta tag hint used in HTML.

```html
<link rel="preconnect" href="https://<DOMAIN_TO_PRECONNECT>">    
```

The **dns-prefetch** browser hint meta tag can be used if a resource is likely to be navigated to or used on a page. DNS prefetching can resolve a domain's address earlier than usual to avoid this time-expensive step later.

The following is an example of a **dns-prefetch** browser hint meta tag used in HTML.

```html
<link rel="dns-prefetch" href="https://<DOMAIN_TO_PREFETCH>">
```

Adding meta tags to a page can be done in Commerce site builder using the **Metatags** module. The **Metatags** module should be added to a page template's "HTML Head" section. For more information, see [Work with templates](../work-with-templates.md).

## Tools for performance analysis

The following tools are recommended for performance analysis.

### Use WebPageTest to analyze page load times 

[WebPageTest](https://webpagetest.org) can provide detailed analysis of page load times across different regions using different connection speeds.  

### Use BlazeMeter to analyze performance under load 

[BlazeMeter](https://blazemeter.com) can generate load on site pages from different regions to help measure load times when content is cached. 

## Restricting e-Commerce website from loading inside external iFrame
The **frame-ancestors** directive can be used to restrict loading your e-Commerce site inside an external iFrame. See the [Manage Content Security Policy](../manage-csp.md) for more information on how to set this feature from within the site builder tool.

## Additional resources

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Online channel extensibility overview](overview.md)

[System requirements](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Module library overview](../starter-kit-overview.md)

[Configure theme settings](configure-theme-settings.md)

[Data cache settings](data-action-cache-settings.md)

[Work with templates](../work-with-templates.md)


