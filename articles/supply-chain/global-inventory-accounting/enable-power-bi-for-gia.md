---
title: Enable Power BI for Global Inventory Accounting
description: This topic describes how to enable Microsoft Power BI for Global Inventory Accounting.
author: JennySong-SH
ms.date: 06/18/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Enable Power BI for Global Inventory Accounting

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!--KFM: Preview until 4/30/2022 -->

You can pin tiles, dashboards, and reports from your [PowerBI.com](https://powerbi.com/) account to your Microsoft Dynamics 365 application workspace.

## Prerequisites

The following prerequisites must be in place before you can enable Power BI reporting:

- You must be a system administrator in the Dynamics 365 application.
- You must have a [PowerBI.com](https://powerbi.com/) account.
- You must have at least one dashboard and one report in your Power BI account.
- You must be an administrator for your Azure Active Directory (Azure AD) account.
- The Azure AD domain must be the same domain that you used for your [PowerBI.com](https://powerbi.com/) account.

## Setup

To set up the Power BI integration, follow these steps.

1. Sign in to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index).
1. Go to **Shared asset library**, select **Power BI report model** as the asset type, and download the **Global Inventory Accounting** package. 
1. Sign in to [PowerBI.com](https://app.powerbi.com/), and upload the **Global Inventory Accounting** Power BI report file by following these steps:

    1. Select **New**.
    1. Select **Upload a file**.
    1. Select the **Global Inventory Accounting** Power BI report file.

1. Configure the **Global Inventory Accounting** Power BI report by following these steps:

    1. Go to **My workspace**, find the dataset for Global Inventory Accounting, and then, on the **Options** menu, select **Settings**.
    1. In **Settings for Global Inventory Accounting**, expand **Parameters**, and update all parameters as required. In particular, be sure to check the following settings:
        1. Overwrite the default **Dataverse URL** values using the values found under **Power platform environment information** in LCS (in the **Power platform integration** section).
        1. Overwrite the default **Environment ID** values using the values found under **Environment details** in LCS (in the **Manage environment** section).
        1. Select the **Edit credentials** link next to the **CDS** label in the **Data source credentials** section. Then sign in to your Dataverse account using the **OAuth2** authentication method.
    1. Verify that the Power BI reports found at **My workspace \> Reports \> Global Inventory Accounting** are now working correctly and display content from your system.

1. Register the application as described in [Configure PowerBI.com integration](../../fin-ops-core/dev-itpro/analytics/configure-power-bi-integration.md#registration-process).
1. Integrate the **Global Inventory Accounting** Power BI report file into Dynamics 365 Supply Chain Management by following these steps:

    1. Go to **System administration \> Setup \> PowerBI.com configuration**.
    1. Select **Edit**.
    1. Select **Enable PowerBI.Com integration**.
    1. In the **Application ID** field, enter the application ID.
    1. In the **Application key** field, enter the application key.
    1. Select **Save**.

1. Refresh the page so that the Power BI sign-in dialog box appears.
1. On the **Options** tab, select **Open report catalog**, and then select the **Global Inventory Accounting** Power BI report file that you uploaded earlier.
1. Refresh the page. You should see that your report has been added.
1. Under **Power BI reports**, select the **Global Inventory Accounting** link.

For more information, see [Configure PowerBI.com integration](../../fin-ops-core/dev-itpro/analytics/configure-power-bi-integration.md).
