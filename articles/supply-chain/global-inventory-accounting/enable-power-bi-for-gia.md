---
title: Enable Power BI for Global Inventory Accounting
description: This topics describes how to enable Power BI for Global Inventory Accounting
author: AndersGirke
ms.date: 06/18/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Enable Power BI for Global Inventory Accounting

[!include [banner](../includes/banner.md)]

You can pin tiles, dashboards, and reports from your [PowerBI.com](http://powerbi.com/) account to your Dynamics 365 application workspace.

## Prerequisites

The following prerequisites needs to be in place before you can enable Power BI reporting.

- Be system administrator in the D365 application.
- Have a [PowerBI.com](http://powerbi.com/) account.
- Have at least one dashboard and one report in your Power BI account.
- Be an administrator for your Microsoft Azure Active Directory (Azure AD) account.
- The Azure AD domain that is configured must be the same domain that you used for your [PowerBI.com](http://powerbi.com/)  account.

## Steps

1. Download the Global Inventory Accounting package from Microsoft Dynamics Lifecycle Services ([LCS](https://lcs.dynamics.com/Logon/Index)) under **Shared asset library \> Power BI report model**.

1. Sign in to [https://app.powerbi.com/](https://app.powerbi.com/)  with your account and Upload **Global Inventory Accounting** Power BI file

    - Clicking +New button.
    - Select Upload a file
    - Select **Global Inventory Accounting** Power BI file

1. Config **Global Inventory Accounting** Power BI report and get it ready for use

    - Find Dataset of **Global Inventory Accounting** in **My workspace** and select **Settings** from option menu
    - Expand **Parameters** in **Settings for Global inventory accounting** and update all parameters appropriately

1. Application registration

    - Refer the link: <https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/configure-power-bi-integration#registration-process>

1. Integrate the Power BI file into Dynamics 365 Supply chain management. Path is **System administration \> Setup \> PowerBI.com configuration.**

    - Click Edit button
    - Mark 'Enable [PowerBI.Com](http://powerbi.com/) integration.
    - Enter the Application ID.
    - Application key.
    - Save

1. Refresh the page and you can see the Power BI login dialog.

1. Click **Options** tab

    - Click Open report catalog button
    - Select your report file "**Global Inventory Accounting"** which you have uploaded.

1. Refresh the page and you can see your report has been added

1. Click on the **Global Inventory Accounting** link under **Power BI reports**

For more information, see [Configure PowerBI.com integration](../../fin-ops-core/dev-itpro/analytics/configure-power-bi-integration.md)
