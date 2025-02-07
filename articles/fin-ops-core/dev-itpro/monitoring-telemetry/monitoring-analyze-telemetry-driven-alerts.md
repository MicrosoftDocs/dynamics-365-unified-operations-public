---
title: Use telemetry-based alerts
description: Learn how to create alerts in Azure Application Insights.
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Use telemetry-based alerts

[!include [banner](../includes/banner.md)]

When a [!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] environment is emitting telemetry to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], that telemetry can be used to create proactive alerts. Here are some examples of alerting:

- Notify stakeholders when someone changes a customer bank account.
- Notify system administrators when specific form loads are taking longer than usual.
- Get notifications when specific errors occur in nightly batch jobs.

You can use the following tools to define and set up alerts on telemetry events:

- [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] Alerts
- Power BI metrics
- Azure Logic Apps
- Power Automate

## No-code alerting with Power BI Metrics

[!INCLUDE[pbimetrics](includes/include-telemetry-alerting-powerbi-metrics.md)]

### Create alerts in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)]

To create alerts in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], follow these steps.

1. In the [Azure portal](https://portal.azure.com), find your Application Insights resource.
1. In the left pane, select **Alerts**.
1. In the condition for a custom log search, add an alerting condition query in Kusto Query Language (KQL).

Learn more about alerts and how to create them in [What are Azure Monitor alerts?](/azure/azure-monitor/alerts/alerts-overview)

### Create alerts by using Azure Logic Apps and Power Automate

Azure Logic Apps and Power Automate have built-in connectors that can be used to query telemetry in [!INCLUDE[appinsights](includes/azure-application-insights-name.md)]. You can configure custom notifications. You can also automate specific actions that are triggered by events or trends that occur in [!INCLUDE[finops-product-name-short](./includes/finops-product-name-short.md)].

> [!IMPORTANT]
> When you deploy a logic app to Azure, the API Connection Resources that are required to authenticate specific actions in the logic app are also created.
>
> After you deploy the logic app, go to those API Connection Resources in the Azure portal to authenticate them. The Application Insights API Connection Resource can be authenticated by using the application ID and an API key. You can find and generate it on the **API Access** page of the [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resource in the Azure portal.
>
> If API Connection Resources for the connections that are required to run the logic app are already deployed in the selected resource group, you can reuse them. Just enter the same resource name before you deploy the logic app.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
