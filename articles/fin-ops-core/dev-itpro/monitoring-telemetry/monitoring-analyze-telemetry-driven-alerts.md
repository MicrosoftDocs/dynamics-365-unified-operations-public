---
title: Telemetry based alerts
description: Learn how to create alerts in Azure Application Insights.  
author: kesaelen
ms.topic: how-to-guide
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: kesaelen
ms.custom: bap-template
---

# Telemetry based alerts
When a [!INCLUDE[finops-product-name-long](../monitoring-telemetry/includes/finops-product-name-long.md)] environment is emitting telemetry to [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)], this telemetry can be used to proactive alert on. Examples of alerting include:
- Notify stakeholders when someone changes a customer bank account.
- Notify system administrators when certain form loads are taking longer than usual.
- Get notifications when certain errors are occurring in nightly batch jobs.

You can use the following tools to define and set up alerts on telemetry events:

- [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)] Alerts
- Power BI metrics
- Azure Logic Apps
- Power Automate

## No-code alerting with Power BI Metrics

[!INCLUDE[pbimetrics](../monitoring-telemetry/includes/include-telemetry-alerting-powerbi-metrics.md)]

### Create alerts in [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)]

If you want to create alerts in [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)], then do as follows:

1. Open the [Azure portal](https://portal.azure.com) and locate your Application Insights resource.
2. In the navigation pane on the left, select **Alerts**.
3. Add a KQL alerting condition query in the condition for a custom log search.

To read more about alerts and how to create them, go to [Azure Application Insights Alerts Overview](https://learn.microsoft.com/azure/azure-monitor/alerts/alerts-overview) in the Azure documentation. 

### Create alerts using Azure Logic Apps and Power Automate

Azure Logic Apps and Power Automate have built-in connectors to query telemetry in [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)] for setting up custom notifications or automating certain actions that are triggered by events or trends happening within [!INCLUDE[finops-product-name-long](../monitoring-telemetry/includes/finops-product-name-long.md)].

The samples below can help getting started with customization and automation using Application Insights.

> [!IMPORTANT]
> Deploying a Logic App to Azure also creates the API Connection Resources necessary to authenticate certain actions in the Logic Apps.
>
> After deploying the Logic App, navigate to the created API Connection Resources in the Azure Portal to authenticate them. The Application Insights API Connection Resource can be authenticated using the Application ID and an API Key. These can be found and generated on the API Access page of the [!INCLUDE[appinsights](../monitoring-telemetry/includes/azure-appinsights-name.md)] resource in the Azure Portal.
>
> If you have already have API Connection Resources deployed in the selected Resource Group for the connections needed to run the Logic App you can reuse them by entering the same resource name before deploying the Logic App.

### TODO : create 2 examples for F&O and link them here

#### Example - Run an alerting query every "n" days and send an email

This Logic App runs every number of days (specified in app deployment). It lists all updates made available to environments that emit telemetry to the specified Application Insights resource during the period. Administrators can use this app to replace email notifications they'd receive for environments when set up as notification recipient.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FBCTech%2Fmaster%2Fsamples%2FAppInsights%2FAlerts%2FAvailableUpdatesNotification.json)

#### Example - Run an alerting query every "n" minutes and send a message to Teams

This Logic App queries Application Insights every number of minutes (specified in app deployment). It notifies a user (also specified in deployment) of any deleted environments in Microsoft Teams. The action that sends the notification in Teams can be updated to notify a Channel or Group Chat instead.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmicrosoft%2FBCTech%2Fmaster%2Fsamples%2FAppInsights%2FAlerts%2FDeletedEnvironmentNotification.json)




## See also
[Telemetry overview](telemetry-overview.md)  
[Enabling telemetry](telemetry-enable-application-insights.md)  
[Available telemetry](telemetry-available-telemetry.md)  
[Telemetry FAQ](telemetry-faq.md)