---
# required metadata

title: Work with CSS override files
description: This topic describes why, when, and how to use Cascading Style Sheets (CSS) override files in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: niholman
ms.search.validFrom: 2019-12-12
ms.dyn365.ops.version: Release 10.0.8

---
# Work with CSS override files

[!include [banner](includes/banner.md)]

This topic describes why, when, and how to use Cascading Style Sheets (CSS) override files in Microsoft Dynamics 365 Commerce.

Permanent site styles should usually be handled through a site's theme. Themes provide the foundational CSS and style settings for the modules on any page of your site. Themes are created by using the Dynamics 365 Commerce online software development kit (SDK), and they are deployed to your websites through Microsoft Dynamics Lifecycle Services (LCS). Theme debugging capabilities and module interface configurations in the SDK help site developers create customizable and cohesive site design packages. When these design packages are deployed to a site, site authors can focus on creating, editing, and publishing content instead of site development.

Given the usual lifecycle of a theme, the dependency on developers to make style changes through the SDK and LCS deployment pipeline can be prohibitive in some scenarios. Site prototypes or hotfixes can seem cumbersome if the SDK isn't configured, or if you don't have time to wait for an LCS deployment.

In these scenarios, CSS override files can help. In the Commerce authoring tools, authenticated users can upload a CSS file, preview it, and then activate it to override a site's theme. The overhead of SDK or LCS deployment isn't required. The overrides that are specified in a CSS override file can be as small as a change to a single text style or as wide-ranging as a complete brand overhaul.

Before you use CSS override files, be aware of the following limitations:

- Only one CSS override file can be active on a site at a time. Therefore, all active overrides must be present in a single override file.
- Although you can preview the overrides in the Commerce authoring tools, there are no dedicated debugging features to help identify any bugs that the overrides introduce. In other words, when you use CSS override files, you don't have the same toolset that the SDK provides for module and authoring validation.

Nevertheless, CSS override files provide a quick way to prototype a design or implement a hotfix before a full theme update is developed and deployed.

## Create a CSS override file

To create a CSS override file, you can use any integrated development environment (IDE), text editor, or source code editor. A typical approach is to use standard web debuggers in your browser to identify style selectors, properties, and values on your existing site. Most browsers let you change values and preview them in the debugger. After you've identified the changes that you want to make, you can save them to your own CSS file.

## Upload a CSS override file

To upload a CSS file to your site in Commerce, follow these steps.

1. In the authoring tools, go to your site.
1. In the navigation pane on the left, select **Design**.

    > [!NOTE]
    > Depending on the version of the Commerce authoring tools that you're using, you might have to expand **Settings** in the navigation pane before you can select **Design**.

1. At the top of the main design pane, select the **CSS override** tab, if it isn't already selected.
1. Under **Available CSS overrides**, select **Upload CSS file**. A File Explorer window appears.
1. In File Explorer, browse to and select a CSS file, and then select **Open**. The uploaded CSS file now appears under **Available CSS overrides**.

## Preview a CSS override file

To preview a CSS override file before you make it active on your live site, follow these steps.

1. In the navigation pane on the left, select **Design**, and then, on the **CSS override** tab, under **Available CSS overrides**, find the CSS file that you want to preview.
1. Next to the CSS file name, select **Preview site**.
1. In the **Select a URL** dialog box, select the URL of the site that you want to see the override applied to, and then select **OK**.
1. If there are multiple variants for the selected URL, select the desired variant in the **Preview variations** dialog box that appears.

A new browser tab or window is opened, where you can validate your style overrides against your site. You can then share the URL with other authenticated Commerce users for review and feedback.

## Activate a CSS override file on your live site

After you've previewed and approved the CSS override file, you can activate it on your live site.

> [!NOTE]
> Only one CSS override file can be active on your site at a time. If you activate a new override file, the previous override file is inactivated. Therefore, make sure that all required overrides are present in a single CSS override file.

To activate a CSS override file, follow these steps.

1. In the navigation pane on the left, select **Design**, and then, on the **CSS override** tab, under **Available CSS overrides**, find the CSS file that you want to activate.
1. Under the CSS file name, select **Activate**. The override file immediately becomes active on your live site.

## Deactivate a CSS override file on your live site

To deactivate a CSS override file on your site, follow these steps.

1. In the navigation pane on the left, select **Design**, and then, on the **CSS override** tab, under **Available CSS overrides**, find the CSS file that you want to deactivate.
1. Under the CSS file name, select **Deactivate**. The override file immediately becomes inactive on your live site.

> [!TIP]
> To access additional options for CSS override files, select the ellipsis (**...**) next to the CSS file name. The **Download**, **Rename**, and **Replace** options are useful for quick changes to an existing CSS override file.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with style presets](style-presets.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
