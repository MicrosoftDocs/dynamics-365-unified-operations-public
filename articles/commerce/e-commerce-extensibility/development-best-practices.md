---
# required metadata

title: Best practices for Dynamics 365 Commerce Development 
description: This topic describes some best practices when developing Dynamics 365 Commerce e-Commerce customizations. 
author: samjarawan
manager: annbe
ms.date: 10/06/2020
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
# Best practices for Dynamics 365 Commerce Development 

[!include [banner](../includes/banner.md)]

This topic describes some best practices when developing Dynamics 365 Commerce e-Commerce customizations.

## Overview
The Dynamics 365 Commerce platform provides a rich online software development kit (SDK) for developer extensibility. Custom modules, data actions and themes can be created or the provided (module library)[starter-kit-overview.md] can be extended. It is important to consider web site performance when building e-Commerce customizations.  Standard best practices used for web site development are applicable including minimizing HTML, JavaScript, CSS and optimizing images.

## Infrastructure setup

The [Dynamics 365 Commerce system](../commerce-architecture.md) includes various sub-systems including the Back Office HQ, the Commerce Scale Unit, the Web Storefront which includes the Node rendering service, the Commerce site builder, and the product recommendations services.  For best performance the various components should be deployed into the same region.  The Commerce Scale Unit setup allows you to the select specific region. The specific region decision should be made in accordance with the customer's regional location.

## Minimizing HTML, CSS & JavaScript

The Dynamics 365 online SDK provides development extensions using TypeScript and SCSS files.  TypeScript is a typed superset of JavaScript that compiles to plain JavaScript and SCSS is a superset of CSS that is compiled down to standard CSS.  When the configuration package is built using [yarn msdyn365 pack](cli-command-reference#pack.md) or the Node server is started on a local development environment using the [yarn start](setup-dev-environment#run-your-node-app.md) command, the typescript files and SCSS files will compiled down to JavaScript and CSS respectively.  These files are also minified to reduce network bandwidth.

You should ensure extra unused JavaScript and CSS are not included in your extension package.  Some tools are listed at the bottom of this document to help measure page load times and can help in identifying problem areas with CSS and JavaScript.

### Reducing JavaScript by excluding unused modules
Dynamics 365 Commerce comes with a large [Module Library](../starter-kit-overview.md) set of modules.  If there are modules that won't be used on the e-Commerce site, they can be excluded to reduce the JavaScript chunk size.  The excluded modules will not be rendered on the live e-Commerce site or available within the site builder tool when authoring pages.

Modules can be excluded by adding the module name to the **excludeModules** property in the SDK's "/src/settings/platform.settings.json" file as shown below.

```
{
    ...
    "excludeModules": ["<EXCLUDED_MODULE_NAME1>","<ExCLUDED_MODULE_NAME2>"]
    ...
}
```

You can verify if the module was successfully excluded by comparing the chunk size displayed after a build or test it in a dev environment (after running the Node server using "yarn start") using the "http://localhost:4000/modules?type=<your-module-name>", you should observe that the excluded module is not rendered.

## Optimizing Images
One of the biggest performance hits to a web page can be the downloading of images.  Use CSS whenever possible to generate images for items such as buttons, but in cases where you need marketing or product images, you should leverage the [media libary](dam-overview.md) inside of the site builder tool to upload the images.  Images uploaded through the media library should be uploaded with the highest quality and resolution that covers all scenarios on the web site.  Images served from the media library will automatically use an image resizer service to serve up the best image.

### Image resizer service
Images served go through an **image resizer** service included in the Commerce rendering engine when rendered inside of a module. This is important for responsive design, in general, as the screen size gets smaller images will be auto scaled down to the correct size for each particular module.

It's important to follow some guidelines to ensure images get resized correctly.  Modules can specify their images sizes for particular view ports in the theme.settings.json file.  See the [configure theme settings](configure-theme-settings.md) document for more information.

When building modules with images, the HTML should always include the width and height parameters. If the width and height are not provided, image caching will not be optimized through the image resizer.

### Image types
There are three aspects that come into play when determining the file size of an image. The resolution of the image (width and height), how the image is encoded (JPEG, GIF, or PNG), and the quality parameter (JPEG only). 

JPEG uses lossy compression, meaning that the file size is decreased by discarding image detail. The amount of detail discarded is controlled with the quality parameter, which is between 0 and 100, with 100 being the best quality. A lower number results in a lower quality image, but also a smaller file size. 

PNG is a lossless format, so no image detail is lost but the image file size will be larger. For images with text, sharp lines, or color gradients, PNG may be a better choice since the JPEG format may show undesirable artifacts as a result of the lossy compression. 

GIF is also a lossless format, but it only supports 256 colors in a single image. For images with text or sharp lines that also don't have many colors, GIF may be a better choice than PNG or JPEG. GIF also has support for simple animations.

Ultimately, the goal is to find the right balance to maintain image quality while keeping the image size as small as possible.


## Cache configuration

Caching is often used on static content that doesn't change often such as JavaScript, CSS, images and product content. Some scenarios may require custom cache settings to achieve best performance results.

### Image caching 

The default content delivery network (CDN) cache time for images is set to 5 minutes. This means that after 5 minutes the next request to get a specific image will need to be retrieved from the origin, and so will be slower. Increasing the cache time setting is possible, however it must be done by opening a support ticket.

### Retail data caching

There is layer of caching of product-specific data in the e-Commerce rendering Node layer. Caching times are different for each entity type and can be configured inside of the **cache.settings.json** file included with the SDK under the "/src/settings/" directory.  For more information, see [Data cache settings](e-commerce-extensibility/data-action-cache-settings.md).


### Module development

#### Retail API

Wherever possible, adopt the **SearchByCriteria** retail API for custom modules. This API returns product attributes as well.

#### Browser hint meta tags

Browser hint meta tags such as **preconnect** and **prefetch** can be used to tell the browser what resources are needed ahead of time to render a page.  This will cause a broswer to initiate network connections before it normally would to make expensive network calls.  

The **preconnect** hint can be used if the page relies on resources coming from external origins or domains to initiate a TCP connection.  This will cause a DNS lookup, TCP handshake and TLS negotiation to happen before the reference in the html document.

The **prefetch** hint can be used if you can identify a resource the user is likely to nagiate to.  The resource will be fetched in the background and the browser cache or server cache can persist


Use preconnect and dns-prefetch metatags for different services being consumed. For example, rendering endpoint, image endpoints, fonts, files, and visual studio application insight trace calls. 

## Tools for performance analysis

### Page load times 

Use [WebPageTest](https://webpagetest.org) for detailed analysis of the page load times across different regions and using different connection speeds.  

### Analyzing performance under load 

Use [BlazeMeter](https://blazemeter.com) for generating load on the pages from different regions to help in measuring load times when content is cached. 

## Additional resources

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Create an e-Commerce site](create-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
