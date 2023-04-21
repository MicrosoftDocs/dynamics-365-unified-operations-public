---
title: Prepare content for use with the Help pane
description: This article describes how you can prepare content so that it can be used with the Help pane.
author: edupont04
ms.date: 04/12/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Prepare content for use with the Help pane

[!include [banner](../includes/banner.md)]

Content that can be used with the **Help** pane in Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce can be derived from existing Microsoft content, migrated from existing Dynamics AX 2012 Help content, or created as new files.

Microsoft creates Help in multiple languages for the locales that are supported by Finance, Supply Chain Management, and Commerce. However, locale support isn't restricted to those locales.

### <a name="metadata"></a>Metadata requirements for custom Help topics

The following metadata must be present in your topics for context-sensitive Help and full-text search to return results.

| Property | Description |
|----------|-------------|
| title | The value is used for full-text search from the **Help** pane. |
| description | The value is used for full-text search from the **Help** pane. |
| ms.search.form | The value contains the Application Object Tree (AOT) name of a page and is used for context-sensitive search from the **Help** pane. |
| ms.locale | The value indicates the language of the article. It's mapped against the current browser locale when the **Help** pane searches the content. Language fallback can be configured for the target custom Help website. For more information, see [Language and locale descriptors in the product and in Help](language-locale.md). |
| ms.search.scope | The value determines which client the Help article is shown in. You can specify one or more values. Values include **Core**, **Operations**, **Retail**, and **Human Resources**. |

The following table describes the values that can be specified for the **ms.search.scope** property. You can specify one or more values. The values determine which client a Help article is shown in.

| Value | Description |
|-------|-------------|
| Core | If this value is present, the article appears in the **Help** pane. Otherwise, the article doesn't appear in the **Help** pane. This value is set for the part of the Microsoft content that must always be available in the **Help** pane, for all users across all supported Dynamics 365 solutions. |
| Operations | This value applies to solutions that are based on Finance or Supply Chain Management. |
| Retail | This value applies to solutions that are based on Commerce. |
| Human Resources | This value applies to solutions that are based on Dynamics 365 Human Resources. |
| Talent | This value applies to solutions based on Dynamics 365 Talent. (Note that the Dynamics 365 Talent: Attract and Dynamics 365 Talent: Onboard apps are being retired. For more information, see [Retiring Dynamics 365 Talent: Attract and Onboard apps](https://community.dynamics.com/365/talent/b/dynamics365fortalent/posts/retiring-dynamics-365-talent-attract-and-nboard-apps).) |

## Migrating content from existing AX 2012 Help content

If you have content from AX 2012, you can reuse it for Finance, Supply Chain Management, and Commerce. However, you must transform the HTML files so that they can be used in the custom Help environment.

[!INCLUDE [custom-help-toolkit-tools](../includes/custom-help-toolkit-tools.md)]

### Non-required metadata

The following properties are reserved for future use:

- **ms.search.region** – Eventually, this property might be used to limit the content that is shown to content that is tagged either as global or for the region of the implementation.
- **ms.search.validFrom** – Eventually, this property might be used to limit the content that is shown to content for a product that was released on a given date or earlier.
- **ms.dyn365.ops.version** – Eventually, this property might be used to limit the content that is shown to content for a specific version of a product or earlier.
- **ms.search.industry** – Eventually, this property might be used to limit the content that is shown to content for a specific industry.

## Changing the locale of topics to match the locale of solutions

If your solution supports multiple markets, you can provide Help content for each market. For example, your solution might support German (Germany) and German (Austria), but you have HTML files only for German (Germany). To make the content available in German (Austria), you can make a copy of the HTML files and then use the [HtmlLocaleChanger](custom-help-toolkit-HtmlLocaleChanger.md) tool to update the **ms.locale** metadata. You can also add content that's specific to Austria to these new HTML files.

## See also

[Custom Help overview](custom-help-overview.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Configure the Help experience for finance and operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
