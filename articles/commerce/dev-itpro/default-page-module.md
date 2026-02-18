---
title: Default page module
description: Learn about default page modules and how to add them to page templates in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Default page module

[!include [banner](../includes/banner.md)]

This article explains default page modules and describes how to add them to page templates in Microsoft Dynamics 365 Commerce.

The default page module is a special module that becomes the root container of a page. You can only add it to a template's **Body** slot. The default page module defines the core slots (**Header Slot**, **Sub Header Slot**, **Main Slot**, **Sub Footer Slot**, and **Footer Slot**) that appear in the Commerce site builder page editor, as shown in the following example illustration.

:::image type="content" source="../media/page-module-1.png" alt-text="Screenshot of page module slots in Commerce site builder page editor.":::

The Commerce module library provides only one type of default page module. However, you can use the [Commerce online channel extensibility software development kit (SDK)](../e-commerce-extensibility/overview.md) to create more custom default page modules as needed.

## Page module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Skip to main content text | Text | The link text that appears in the "skip to main content" link on the page. The default value is **Skip to main content**. |
| Theme | A theme that you select from a list of available themes | The theme to use for the pages that are derived from this template.<p><strong>Note:</strong> This property is deprecated and will be removed in a future release. Set themes only at the site level.</p> |
| Requires sign-in? | **True** or **False** | This Boolean property controls whether access to the page requires user sign-in. If you set it to **True**, users who aren't signed in are redirected to the sign-in page. |

## Add a default page module to a template

To add a default page module to a template, follow these steps:

1. In Commerce site builder for your site, select **Templates**.
1. Select a template, and then select **Edit**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add module**.

    :::image type="content" source="../media/page-module-2.png" alt-text="Screenshot of adding a new module to the Body slot in Commerce site builder.":::

1. In the **Select modules** dialog box, select the **Default Page** module, and then select **OK**.

    :::image type="content" source="../media/page-module-3.png" alt-text="Screenshot of selecting the Default Page module in the Select modules dialog box.":::

After you add the default page module, it should resemble the example in the following illustration. You can now configure the module, and save and publish the template.

:::image type="content" source="../media/page-module-4.png" alt-text="Screenshot of the default page module added to a template in Commerce site builder.":::

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Page summary modules](page-summary-module.md)

[External and inline script modules](script-module.md)

[Metatags module](metatags-module.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
