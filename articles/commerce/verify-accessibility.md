---
# required metadata

title: Verify page content accessibility
description: This topic describes how to verify the accessibility of page content in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/08/2020
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
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2019-12-19
ms.dyn365.ops.version: Release 10.0.8

---

# Verify page content accessibility

[!include [banner](includes/banner.md)]

This topic describes how to verify the accessibility of page content in Microsoft Dynamics 365 Commerce.

When you've finished changing a page, you should make sure that the content is accessible to everyone on the web. In the Commerce authoring tools, you can easily verify the accessibility of page content by using the integrated [Microsoft Accessibility Insights](https://accessibilityinsights.io/) service. This service verifies your page content against the latest [World Wide Web Consortium (W3C) accessibility](https://www.w3.org/standards/webdesign/accessibility) guidelines.

The [Microsoft Accessibility Insights](https://accessibilityinsights.io/) integration must be turned on at the tenant or site level before you can use it.

## Turn on Microsoft Accessibility Insights for all the sites in your tenant

To turn on the [Microsoft Accessibility Insights](https://accessibilityinsights.io/) integration for all the Commerce sites in your tenant, follow these steps.

> [!NOTE]
> To access tenant settings, you must be signed in to Commerce as a system admin.

1. Sign in to Commerce as a system admin.
1. In the left navigation pane, select **Tenant Settings** (next to the gear symbol) to expand it.
1. Under **Tenant Settings**, select **Features**.
1. Set the **Accessibility Check** option to **On**.

## Turn on Microsoft Accessibility Insights for a single site

To turn on the [Microsoft Accessibility Insights](https://accessibilityinsights.io/) integration for a single Commerce site, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the left navigation pane, select **Site Settings** to expand it.
1. Under **Site Settings**, select **Features**.
1. Set the **Accessibility Check** option to **On**.

## Verify the accessibility of the content on the home page

To use the integrated [Microsoft Accessibility Insights](https://accessibilityinsights.io/) service to scan and verify the content of your home page in Commerce, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the left navigation pane, select **Pages**.
1. Find and select the home page to open it in the page editor.
1. On the command bar, select **Check accessibility**. The **Check Accessibility** page appears.
1. After the scan is completed, review the contents of the report.
1. If any checks failed, select each failed check item to expand it so that you can view more details.
1. To close the report after you've finished reviewing it, scroll to the bottom of the **Check Accessibility** page, and select **OK**.

## Additional resources

[Modify an existing site page](modify-existing-page.md)

[Add a new site page](add-new-page.md)

[Select page layouts](select-page-layouts.md)

[Manage SEO metadata](manage-seo-metadata.md)

[Save, preview, and publish a page](save-preview-publish-page.md)

[Enrich a product page](enrich-product-page.md)

[Enrich a category landing page](enrich-category-page.md)

[Create dynamic e-commerce pages based on URL parameters](create-dynamic-pages.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
