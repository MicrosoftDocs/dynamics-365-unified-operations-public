---
title: External and inline script modules
description: Learn about external and inline script modules and how to add them to templates in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# External and inline script modules

[!include [banner](../includes/banner.md)]

This article explains external and inline script modules and describes how to add them to templates in Microsoft Dynamics 365 Commerce.

By using external and inline script modules, you can add client-side JavaScript scripts to site pages. The scripts can be inline, or you can call them from an external file. Add external and inline script modules to a template's **HTML Head**, **Body Begin**, or **Body End** slot.

The following illustration shows an example where external and inline script modules are added to the various supported slots in a template.

:::image type="content" source="../media/script-modules-1.png" alt-text="Screenshot of script modules in different slots of a template.":::

## External script module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Script source | Text | The URL of the script file location. |
| Execute script asynchronously | **True** or **False** | If you set this property to **True**, the script runs asynchronously. |
| Defer script execution | **True** or **False** | If you set this property to **True**, the script runs when the page finishes running. |

## Inline script module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Inline script | Text | The collection of scripting statements that the module inserts inline into **\<script\>** tags on the HTML page. |

## Content security policy

If you enable content security policy (CSP), external scripts might not run. To enable external scripts to run, first add their domain URLs to the **script-src** CSP directive in Commerce site builder. For more information, see [Manage Content Security Policy](manage-csp.md).

## Add a script module to a template

To add a script module to a template, follow these steps:

1. In Commerce site builder for your site, select **Templates**.
1. Select a template, and then select **Edit**.
1. In the **Body Begin** slot, select the ellipsis (**...**), and then select **Add module**.

    :::image type="content" source="../media/script-modules-2.png" alt-text="Screenshot of adding a new module.":::

1. In the **Select modules** dialog box, select either the **External script** module or the **Inline script** module, and then select **OK**.

    :::image type="content" source="../media/script-modules-3.png" alt-text="Screenshot of adding a script module.":::

After you add the script module, it should resemble the example in the following illustration. You can now configure the module, and save and publish the template.

:::image type="content" source="../media/script-modules-4.png" alt-text="Screenshot of an inline script module added.":::

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Default page module](default-page-module.md)

[Page summary modules](page-summary-module.md)

[Metatags module](metatags-module.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
