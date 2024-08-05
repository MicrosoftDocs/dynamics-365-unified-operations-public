---
title: Set up Operational Insights
description: This article describes how to set up and use the Operational Insights feature in Microsoft Dynamics 365 Commerce.
author: ashishMSFT
ms.date: 06/20/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28

---

# Set up Operational Insights

[!include [banner](../includes/banner.md)]

This article describes how to set up and use the Operational Insights feature in Microsoft Dynamics 365 Commerce.

Operational Insights is a Dynamics 365 Commerce feature that's designed to give customers better visibility into their service health and business functionality by sending telemetry directly to a customer-owned Application Insights account.

By enabling Operational Insights for your environments in Commerce headquarters, you can collect a curated list of events from both Commerce Scale Unit (CSU) and your point-of-sale (POS) devices. These events can help you better understand how your systems are performing, and they let you monitor key technical and business metrics.

Even if you don't want to collect this telemetry all the time, you can benefit by quickly enabling or disabling collection for specific environments. In this way, the telemetry can help you troubleshoot or debug during development or in production.

## Access logs in Application Insights

To access diagnostic event logs for Commerce CSU and POS components via Application Insights, complete the procedures in this section.

### Minimum version requirements for CSU

CSU has the following minimum version requirements:

- 10.0.23 (Retail Server version 9.33.22062.15 and later)
- 10.0.24 (Retail Server version 9.34.22062.14 and later)
- 10.0.25 (Retail Server version 9.35.22062.13 and later)
- 10.0.26 and later (all versions)

### Enable diagnostic events in Application Insights

> [!IMPORTANT]
> If you previously used a preview version of Operational Insights, you must use the following procedure to enable Operational Insights. In this way, you ensure that reliable and secure access to events can continue.

To enable Commerce component diagnostic events, you must have an Application Insights account. You can use an existing account or [create a new account](/azure/azure-monitor/app/create-workspace-resource#create-workspace-based-resource). For data privacy reasons, we recommend that you use separate Application Insights accounts for production, sandbox, and development environments. After you create an account, you must enable the **Operational Insights** feature in headquarters.

To enable diagnostic events in Application Insights, follow these steps.

1. In headquarters, open the **Feature management** workspace, and enable the **Operational Insights** feature.
1. Go to **System administration \> Setup \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **Yes**.
1. On the **Environments** tab, enter **LCS Environment ID** and **Environment mode** values for every environment where you plan to use Application Insights. You can find each environment's environment ID on the **Environment details** page for that environment in Microsoft Dynamics Lifecycle Services. This step is required to help prevent diagnostic events from being inadvertently sent to an incorrect environment when database copy operations are performed.
1. On the **Application Insights registry** tab, specify the Application Insights **Instrumentation Key** value and the corresponding **Environment Mode** value of the environments where you plan to use each Application Insights account.
1. After you've completed the preceding configuration, you must run the **CDX Job 1110** job. You can wait for this job to run on its own schedule, or you can run it manually.
1. In Lifecycle Services, go to **Environment details \> Commerce \> Manage**, select a CSU instance, and then select **Restart**. Repeat this step for each CSU.
1. Repeat the preceding steps for each environment where you plan to use Application Insights.

> [!NOTE]
> - The telemetry events in Operational Insights are subject to change. We recommend that you use Operational Insights events to do preliminary analysis and troubleshooting on your own, not to define dashboards or alerts. If you use events for purposes beyond self-service troubleshooting, we recommend that you validate and update your queries after each CSU/POS release.
> - As of Commerce version 10.0.29, the procedures in this section also enable streaming of POS Operational Insights events to your Application Insights account. For more information, see [Operational Insights for POS – Events and queries](https://download.microsoft.com/download/9/2/b/92be35b0-0e24-4a4d-940d-6f4db29791c0/Operational-Insights-Commerce-POS-events-queries.pdf).

#### Use the DLLHost.exe.config file to control POS Operational Insights events

To use the DLLHost.exe.config file to control POS Operational Insights events, follow these steps.

1. In a text editor, open the **DLLHost.exe.config** file at **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker**.
1. In the **diagnosticsSection** section, remove the sink XML element that has the class name **Microsoft.Dynamics.Retail.Diagnostics.OperationalInsights.OperationalInsightsLogger**.
1. Save the file.

### Disable diagnostic events in Application Insights

> [!IMPORTANT]
> If you want to disable diagnostic events and no longer send them to Application Insights, you must complete the following procedure. You can't just disable the feature in Feature management.

To disable diagnostic events in Application Insights, follow these steps.

1. In headquarters, go to **System administration \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **No**.
1. After you've completed the preceding configuration, you must run the **CDX Job 1110** job. You can wait for this job to run on its own schedule, or you can run the job manually.
1. In Lifecycle Services, go to **Environment details \> Commerce \> Manage**, select a CSU instance, and then select **Restart**. Repeat this step for each CSU.
1. Repeat the preceding steps for each environment where you plan to turn off Application Insights.

To disable diagnostic events for a single environment, delete the instrumentation key on the **Application Insights registry** tab of the **Operational Insights** page. Then complete steps 3 and 4 of the preceding procedure.

> [!NOTE]
> In Commerce version 10.0.29 and later, the steps in this section also disable streaming of POS Operational Insights events to your Application Insights account. 
