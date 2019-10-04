---
# required metadata

title: Content Security Policy
description: This topic describes how to enable and configure content security policy.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience:  Application user
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
# Chain data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to enable and configure content security policy.

## Overview
Enabling content security policy will enhance the security of an e-Commerce site by blocking connections, scripts, fonts, etc. from unknown sources.

The Dynamics 365 Commerce Online SDK provide a default allow list of source URLs where styles, scripts and API calls can be made.  The allow list can also be extended from within the authoring tools **Extensibility section** per site on a tenant.  

For more details see the [Content Security Policy referece guide](https://content-security-policy.com/) .

The following directives are extendable on each site.

Directive | Description
--- | ---
child-src | Defines valid sources for web workers and nested browsing contexts loaded using elements such as <frame> and <iframe>
connect-src | The connect-src directive restricts to which URLs AJAX requests can be made.
font-src | Defines valid sources for fonts.
img-src | Defines valid sources for images.
media-src | Defines valid sources of audio and video, eg HTML5 <audio>, <video> elements.
object-src | Defines valid sources of plugins, eg <object>, <embed> or <applet>.
script-src | Defines valid sources of JavaScript.
style-src | Defines valid sources of stylesheets.

Extending these policies can be done through authoring on a per-site basis.

Content Security Policy is enabled by default and will require some extra configuration for most sites.  Below outlines how this can be done.

As an example, with content security policy enabled, if a site needs to call an external script such as https://www.example.com/scripts/example.js, an entry must add it to the **script-src** directive under the **Content Security Policy** tab on the **Site Management** **Extensibilty** page.

[Content Security Policy](media\content-security-policy.png)

Navigate to the app-settings section in the authoring experience by clicking on ‘Site Management’ and then click on ‘Extensibility’

