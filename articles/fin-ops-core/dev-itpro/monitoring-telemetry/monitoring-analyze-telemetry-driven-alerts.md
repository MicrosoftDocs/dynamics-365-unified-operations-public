---
title: Telemetry based alerts
description: Learn how to create alerts in Azure Application Insights.  
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Telemetry based alerts

When a [!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] environment is emitting telemetry to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], this telemetry can be used to proactive alert on. Examples of alerting include:

- Notify stakeholders when someone changes a customer bank account.
- Notify system administrators when certain form loads are taking longer than usual.
- Get notifications when certain errors are occurring in nightly batch jobs.

You can use the following tools to define and set up alerts on telemetry events:

- [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] Alerts
- Power BI metrics
- Azure Logic Apps
- Power Automate

## No-code alerting with Power BI Metrics

[!INCLUDE[pbimetrics](includes/include-telemetry-alerting-powerbi-metrics.md)]

### Create alerts in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)]

If you want to create alerts in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], then do as follows:

1. Open the [Azure portal](https://portal.azure.com) and locate your Application Insights resource.
1. In the navigation pane on the left, select **Alerts**.
1. Add a KQL alerting condition query in the condition for a custom log search.

To read more about alerts and how to create them, go to [Azure Application Insights Alerts Overview](/azure/azure-monitor/alerts/alerts-overview) in the Azure documentation. 

### Create alerts using Azure Logic Apps and Power Automate

Azure Logic Apps and Power Automate have built-in connectors to query telemetry in [!INCLUDE[appinsights](includes/azure-application-insights-name.md)]. It's possible to configure custom notifications or automating certain actions triggered by events or trends happening within [!INCLUDE[finops-product-name-long](./includes/finops-product-name-long.md)].

The samples below can help getting started with customization and automation using Application Insights.

> [!IMPORTANT]
> Deploying a Logic App to Azure also creates the API Connection Resources necessary to authenticate certain actions in the Logic Apps.
>
> After deploying the Logic App, navigate to the created API Connection Resources in the Azure Portal to authenticate them. The Application Insights API Connection Resource can be authenticated using the Application ID and an API Key. These can be found and generated on the API Access page of the [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resource in the Azure Portal.
>
> If you already have API Connection Resources deployed in the selected Resource Group for the connections needed to run the Logic App, you can reuse them by entering the same resource name before deploying the Logic App.
