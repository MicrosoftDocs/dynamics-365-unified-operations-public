---
# required metadata

title: External and inline script modules
description: This topic covers the external and inline script modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 03/25/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# External and inline script modules

[!include [banner](includes/banner.md)]

This topic covers the external and inline script modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.

External and inline script modules enable you to add JavaScript client-side scripts to site pages, either inline or called from an external file. External and inline script modules can be added to a template's **HTML Head**, **Body Begin**, or **Body End** slots. 

The following example image shows external and inline script modules added to various slots in a template.

![Script modules](media/script-modules-1.png)

## External script module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Script source | Text | The URL of the script file location. |
| Execute script asynchronously | **True** or **False** | If set to **True**, the script will execute asynchronously. |
| Defer script execution | **True** or **False** | If set to **True**, the script will execute when the page has finished executing. |

## Inline script module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Inline script | Text | The collection of scripting statements that will be inserted inline into script tags on the HTML page. |

## Content security policy

If you have content security policy (CSP) enabled, external scripts may not run. To allow external scripts to run, you must first add their domain URLs to the **script-src** CSP directive in Commerce site builder. For more information, see [Manage Content Security Policy](manage-csp.md).

## Add a script module to a template

To add a script module to a template, follow these steps.

1. In site builder for your site, select **Templates**. 
1. Select a template, and then select **Edit**.
1. In the **Body Begin** slot, select the ellipsis (**...**), and then select **Add Module**.

    ![Add new module](media/script-modules-2.png)

1. In the **Add Module** dialog box, select either the **Inline script** or **External script** module, and then select **OK**.

    ![Add script module](media/script-modules-3.png)

Once the script module is added, it should look similar to the following example image. The module can now be configured and the template can be saved and published.

    ![Inline script module added](media/script-modules-4.png)

## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](default-page-module.md)

[Page summary modules](page-summary-module.md)

[Metatags module](metatags-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
