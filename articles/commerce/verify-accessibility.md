---
# required metadata

title: Verify page content accessibility
description: This topic describes how to verify page content accessibility in Microsoft Dynamics 365 Commerce.
author: arotkin
manager: annbe
ms.date: 12/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: arotkin
ms.search.validFrom: 2019-12-19
ms.dyn365.ops.version: Release 10.0.8

---

# Verify page content accessibility

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to verify page content accessibility in Microsoft Dynamics 365 Commerce.

## Overview

When you have finished modifying a page, you should to ensure that the content is accessible for everyone on the web. You can easily do this in the Commerce authoring tools by using the integrated [Microsoft Accessibility Insights](https://accessibilityinsights.io/en/) service. This will verify your page contents against the latest [W3C accessibility](https://www.w3.org/standards/webdesign/accessibility) guidelines.

The [Microsoft Accessibility Insights](https://accessibilityinsights.io/en/) integration must be enabled at the tenant or site level before you can use it.

## Enable Microsoft Accessibility Insights for all of the sites in your tenant

To enable [Microsoft Accessibility Insights](https://accessibilityinsights.io/en/) integration for all of the Commerce sites in your tenant, follow these steps. 

>[!NOTE]
>You must be signed in to Commerce as a system administrator to access tenant settings.

1. Sign in to Commerce as a system administrator.
1. In the left navigation pane, select **Tenant Settings** (next to the gear icon) to expand it.
1. Below **Tenant Settings**, select **Features**.
1. Set the **Accessibility Check** option to **On**.

## Enable Microsoft Accessibility Insights for a single site

To enable [Microsoft Accessibility Insights](https://accessibilityinsights.io/en/) integration for a single Commerce site, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the left navigation pane, select **Site Settings** to expand it.
1. Below **Site Settings**, select **Features**.
1. Set the **Accessibility Check** option to **On**.

## Verify the accessibility of the content on the home page

To scan and verify your home page content in Commerce using the integrated [Microsoft Accessibility Insights](https://accessibilityinsights.io/en/) service, follow these steps.

1. Under **Sites**, select **Fabrikam** (or the name of your site).
1. In the left navigation pane, select **Pages**.
1. Find and select the home page to open it in the page editor.
1. On the command bar, select **Check accessibility**. The **Check Accessibility** window appears.
1. After the scan is complete, review the contents of the report.
1. If there are failed checks, select each failed check item to expand it for more details.
1. To close the report when done reviewing it, scroll to the bottom of the **Check Accessibility** window and click **OK**.
