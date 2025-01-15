---
title: Get started with Monitoring and Telemetry
description: This article explains how to get started with the Application Insights integration for finance and operations apps.
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Get started with telemetry for finance and operations apps

[!include [banner](../includes/banner.md)]

This article describes how to get started to send telemetry from [!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] environments to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)].

To configure your environments to send telemetry to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], follow these steps. 

1. Set up an Application Insights resource in Azure.
1. Enable the **Monitoring and Telemetry** feature in [!INCLUDE[finops-product-name-short](includes/finops-product-name-short.md)].
1. Configure environments to link to the right [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resources.
1. Configure the type of telemetry to be sent to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)].

## Set up Application Insights resource in Azure

The first thing needed to get started is to create a [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resource in Azure if you don't have one. For more information, see [Workspace-based Application Insights resources](/azure/azure-monitor/app/create-workspace-resource?tabs=bicep).

## Enable the Monitoring and Telemetry feature

To enable the Monitoring and Telemetry feature, follow these steps.

1. In Dynamics 365 for Finance and Supply Chain Management, go to the **Feature Management** workspace.
1. In the **Feature list**, filter the list to find the **Monitoring and Telemetry** feature and click **Enable**.

[![Monitoring and Telemetry Feature.](images/monitoring-getting-started-enable-feature.png)

## Configure environments and link to Application Insights

Environments are categorized into either of the following environment modes: development, test, and production. To link environments to specific modes, follow these steps.

1. In Dynamics 365 for Finance and Supply Chain Management, go to **System administration** \> **Monitoring and Telemetry parameters**.
1. In the **Environments** tab, create one record for each environment want to emit telemetry for. Multiple environments can be entered here. Entering all your environments ensures that database refresh operations would include this configuration and be synchronized across environments.<br>
Provide the following configuration:

   | Field name | Description |
   | ---------- | ----------- |
   | **Environment ID** | The unique identifier for your environment |
   | **Environment Mode** | Specifies whether this environment is a development, test, or production environment. <br>This field is used to separate telemetry in different Application Insight instances intended for development, test, or Production. |

   [![Application Insights Environments.](images/monitoring-getting-started-application-insights-environments.png)

1. On the **Application Insights Registry** tab, create a record for each of the used environment modes.

   | Field name | Description |
   | ---------- | ----------- |
   | **Environment Mode** | Specifies whether this environment is a development, test, or Production environment. |
   | **Instrumentation Key** | The instrumentation key used for connecting to Application Insights.<br>If a connection string is specified, the instrumentation is ignored. |
   | **Connection String** | The connection string is used to connect to Application Insights.  |

   [![Application Insights Registry.](./images/monitoring-getting-started-application-insights-registry.png)](./images/monitoring-getting-started-application-insights-registry.png)

## Configure the type of telemetry to be emitted

1. In Dynamics 365 for Finance and Supply Chain Management, go to **System administration** \> **Monitoring and Telemetry parameters**.
1. On the **Configure** tab, enable each of the types of telemetry that need to be emitted.

   [![Application Insights Signal Configuration.](images/monitoring-getting-started-configure-signals.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
