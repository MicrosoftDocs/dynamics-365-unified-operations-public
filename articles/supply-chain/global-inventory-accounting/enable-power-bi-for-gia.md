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

- You must be a system administrator in the Dynamics 365 application.
- You must have a [PowerBI.com](http://powerbi.com/) account.
- You must have at least one dashboard and one report in your Power BI account.
- You must be an administrator for your Microsoft Azure Active Directory (Azure AD) account.
- The Azure AD domain must be the same domain that you used for your [PowerBI.com](http://powerbi.com/) account.

## Setup procedure

To set up the Power BI integration, do the following steps:

1. Sign in to Microsoft Dynamics Lifecycle Services ([LCS](https://lcs.dynamics.com/Logon/Index)).

1. Under **Shared asset library \> Power BI report model**, download the *Global Inventory Accounting* package. 

1. Sign in to [https://app.powerbi.com/](https://app.powerbi.com/) and upload the *Global Inventory Accounting* Power BI file by doing the following steps:

    1. Select **New** .
    1. Select **Upload a file**
    1. Select your *Global Inventory Accounting* Power BI file

1. Configure the *Global Inventory Accounting* Power BI report and get it ready for use. Do the following steps:

    1. Find the dataset for Global Inventory Accounting in **My workspace** and select **Settings** from the **Option** menu.
    1. Expand **Parameters** in **Settings for Global inventory accounting** and update all parameters as needed.

1. Register the application as described in [Configure PowerBI.com integration](../../fin-ops-core/dev-itpro/analytics/configure-power-bi-integration.md#registration-process)

1. Integrate the Power BI file into Dynamics 365 Supply chain management by doing the following steps:

    1. Go to **System administration \> Setup \> PowerBI.com configuration**.
    1. Select **Edit**.
    1. Select **Enable PowerBI.Com integration**.
    1. Enter the **Application ID**.
    1. Enter the **Application key**.
    1. Select **Save**.

1. Refresh the page to see the Power BI login dialog.

1. Open the **Options** tab and then do the following steps:

    1. Select **Open report catalog**.
    1. Select the report file that you uploaded (*Global Inventory Accounting*).

1. Refresh the page to see that your report has been added.

1. Select the **Global Inventory Accounting** link under **Power BI reports**

For more information, see [Configure PowerBI.com integration](../../fin-ops-core/dev-itpro/analytics/configure-power-bi-integration.md)
