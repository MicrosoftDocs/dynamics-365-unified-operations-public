---
title: Commerce Operational Insights
description: This article describes the Operational Insights feature in Microsoft Dynamics 365 Commerce.
author: ashishMSFT
ms.date: 12/05/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28

---

# Commerce Operational Insights

[!include [banner](../includes/banner.md)]

This article describes the Operational Insights feature in Microsoft Dynamics 365 Commerce.

Operational Insights is a Dynamics 365 Commerce feature designed to help provide customers better visibility into their service health and business functionality by sending telemetry directly to a customer-owned Application Insights account.

Enabling Operational Insights for your environments in Commerce headquarters allows you to collect a curated list of events from both Commerce Scale Unit (CSU) and your point-of-sale (POS) devices. These events help you better understand how your systems are performing and allow you to monitor key technical and business metrics. In cases where you don't want to always be collecting this telemetry, you can still benefit by quickly enabling or disabling the collection for specific environments to help with troubleshooting or debugging scenarios during development or in production.

## Access logs in Application Insights

Diagnostic events for Commerce CSU and POS components can be accessed in Application Insights.

### Commerce Scale Unit minimum version requirements

Commerce Scale Unit has the following minimum version requirements:

- 10.0.23 (Retail Server version 9.33.22062.15 and later)
- 10.0.24 (Retail Server version 9.34.22062.14 and later)
- 10.0.25 (Retail Server version 9.35.22062.13 and later)
- 10.0.26 and later (all versions)

### Enable diagnostic events in Application Insights

> [!IMPORTANT]
> If you used System Operational Insights Preview, you must complete the following procedure to enable System Operational Insights. That way, you ensure that reliable and secure access to events can continue.

To enable Commerce component diagnostic events, you must have an Application Insights account. You can use an existing account or [create a new account](/azure/azure-monitor/app/create-workspace-resource#create-workspace-based-resource). For data privacy reasons, we recommend that you use separate Application Insights accounts for production, sandbox, and development environments. After you have an account, you must enable the **Operational Insights** feature in Commerce headquarters.

To enable diagnostic events in Application Insights in Commerce headquarters, follow these steps. 

1. In the **Feature Management** workspace, enable the **Operational Insights** feature.
1. Go to **System administration \> Setup \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **Yes**.
1. On the **Environments** tab, enter **LCS Environment ID** and **Environment mode** values for every environment where you plan to use Application Insights. You can find each environment's LCS environment ID on the **Environment details** page for that environment in LCS. This step is required to prevent diagnostic events from being inadvertently sent to an incorrect environment when database copy operations are performed.
1. On the **Application Insights registry** tab, specify the Application Insights instrumentation key and corresponding environment mode of the environments where you plan to use each Application Insights account.
1. After you've completed the preceding configuration, the **CDX Job 1110** job must be run. You can wait for this job to run on its own schedule, or you can manually run it.
1. Restart each Commerce Scale Unit. In LCS, go to **Environment details \> Commerce \> Manage**, select a Commerce Scale Unit instance, and then select **Restart**.
1. Repeat the preceding steps for each environment where you plan to use Application Insights.

> [!NOTE]
> The telemetry events in Operational Insights are subject to change. We recommend that you use Operational Insights events to perform preliminary analysis and troubleshooting on your own, and not to define dashboards or alerts. If you choose to use events beyond self-service troubleshooting, we recommend that you validate and update your queries with each Commerce Scale Unit/POS release.
> 
> Starting Commerce version 10.0.29 and later, the procedures in this section also enable streaming of POS Operational Insights events to your Application Insights account. More details for Operational Insights for POS can be found here - 
> https://download.microsoft.com/download/9/2/b/92be35b0-0e24-4a4d-940d-6f4db29791c0/Operational-Insights-Commerce-POS-events-queries.pdf
>
> To use the config file to control POS Operational Insights events, complete the following steps.
>
> 1. With a text editor, open the "DLLHost.exe.config" file that is located at “C:\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker”.
>
> 1. Remove the sink XML element with the class name “Microsoft.Dynamics.Retail.Diagnostics.OperationalInsights.OperationalInsightsLogger” from the “diagnosticsSection”. 

### Disable diagnostic events in Application Insights

If you no longer want to send diagnostic events to Application Insights, you must disable the feature.

> [!IMPORTANT]
> If you want to disable diagnostic events, it isn't enough that you turn off the feature in **Feature management**.

To disable diagnostic events in Application Insights in Commerce headquarters, follow these steps.

1. Go to **System administration \> Operational Insights**.
1. On the **Configure** tab, set the **Commerce channel events** option to **No**.
1. After you've completed the preceding configuration, the **CDX Job 1110** job must be run. You can wait for this job to run on its own schedule, or you can manually run it.
1. Restart each Commerce Scale Unit. In LCS, go to **Environment details \> Commerce \> Manage**, select a Commerce Scale Unit instance, and then select **Restart**.
1. Repeat the preceding steps for each environment where you plan to turn off Application Insights.

To disable diagnostic events for a single environment, delete the instrumentation key on the **Application Insights registry** tab of the **Operational Insights** page. Then complete steps 3 and 4 of the preceding procedure.

> [!NOTE]
> In Commerce version 10.0.29 and later, the steps in this section also disable streaming of POS operational insights events to your Application Insights account. 
