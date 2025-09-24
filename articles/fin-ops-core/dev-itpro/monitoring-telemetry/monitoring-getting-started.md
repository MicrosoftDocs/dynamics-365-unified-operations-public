---
title: Get started with monitoring and telemetry
description: Learn how to get started with the Application Insights integration for finance and operations apps.
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Get started with telemetry for finance and operations apps

[!include [banner](../includes/banner.md)]

This article explains how to start to send telemetry from [!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] environments to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)].

To configure your environments to send telemetry to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], follow these steps.

1. Set up an Application Insights resource in Azure.
1. Enable the **Monitoring and Telemetry** feature in [!INCLUDE[finops-product-name-short](includes/finops-product-name-short.md)].
1. Configure environments to link to the correct [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resources.
1. Configure the type of telemetry that must be sent to [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)].

## Set up an Application Insights resource in Azure

To get started, you must create a [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] resource in Azure if you don't already have one. Learn more in [Workspace-based Application Insights resources](/azure/azure-monitor/app/create-workspace-resource?tabs=bicep).

## Enable the Monitoring and telemetry feature

To enable the Monitoring and telemetry feature, follow these steps.

1. In Finance and Supply Chain Management, open the **Feature management** workspace.
1. Filter the feature list to find the **Monitoring and Telemetry** feature. Select the feature, and then select **Enable**.

[![Screenshot that shows the Monitoring and Telemetry feature enabled in the Feature management workspace.](images/monitoring-getting-started-enable-feature.png)](images/monitoring-getting-started-enable-feature.png)

## Configure environments and link to Application Insights

Environments are categorized into one of the following environment modes: development, test, or production. To link environments to specific modes, follow these steps.

1. In Finance and Supply Chain Management, go to **System administration** \> **Monitoring and Telemetry parameters**.
1. On the **Monitoring settings** page, on the **Environments** tab, create a record for each environment that you want to emit telemetry for. Multiple environments can be entered here. By entering all your environments, you ensure that database refresh operations include this configuration and are synced across environments.

    For each environment, set the following fields.

    | Field name | Description |
    | ---------- | ----------- |
    | Environment ID | The unique identifier of the environment. |
    | Environment Mode | <p>A value that specifies whether the environment is a development, test, or production environment.</p><p>This field is used to separate telemetry in different Application Insight instances that are intended for development, test, or production.</p> |

    [![Screenshot that shows environments being added on the Environments tab of the Monitoring settings page.](images/monitoring-getting-started-application-insights-environments.png)](images/monitoring-getting-started-application-insights-environments.png)

1. On the **Application Insights Registry** tab, create a record for each environment mode that is used.

    For each environment mode, set the following fields.

     | Field name | Description |
     | ---------- | ----------- |
     | Environment Mode | A value that specifies whether the environment is a development, test, or production environment. |
     | Instrumentation Key | <p>The instrumentation key that is used to connect to Application Insights.</p><p><strong>Note:</strong> If a connection string is specified, the instrumentation key is ignored.</p> |
     | Connection String | The connection string that is used to connect to Application Insights. |

     [![Screenshot that shows an environment mode being added on the Application Insights Registry tab of the Monitoring settings page.](./images/monitoring-getting-started-application-insights-registry.png)](./images/monitoring-getting-started-application-insights-registry.png)

## Configure the type of telemetry that must be emitted

1. In Finance and Supply Chain Management, go to **System administration** \> **Monitoring and Telemetry parameters**.
1. On the **Monitoring settings** page, on the **Configure** tab, turn on the option for each type of telemetry that must be emitted.

    [![Screenshot that shows the setup of telemetry types on the Configure tab of the Monitoring settings page.](images/monitoring-getting-started-configure-signals.png)](images/monitoring-getting-started-configure-signals.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
