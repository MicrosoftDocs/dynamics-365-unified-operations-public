---
title: Understand and control costs
description: Learn about the various cost and pricing options.
author: kennysaelen
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Understand and control costs

[!include [banner](../includes/banner.md)]

Management of telemetry costs in finance and operations apps is crucial, because data that is sent to Azure Application Insights incurs charges based on many factors. By implementing effective strategies, you can help control these expenses and also maintain robust monitoring. The guidelines and resources in this article come from both the Microsoft Dynamics 365 Application Insights team and the [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] team.

## Understand telemetry costs

[!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] is an extension on top of Azure Monitor. Although many factors drive the cost of Azure Monitor, the main drivers are the ingestion and retention of data. [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] provides the tools that you need to gain insights into the current usage. It also provides ways to automate the retrieval of usage cost information, and ways to set thresholds and alert when those thresholds are exceeded.

Learn more about all the cost factors in [Azure Monitor cost and usage](/azure/azure-monitor/cost-usage).

## Strategies for controlling telemetry costs

You can use the following strategies to control telemetry costs.

### Selective telemetry collection

- **Production environment focus** – Configure Application Insights to collect only essential telemetry in production environments. This approach reduces data volume and associated costs.
- **Custom telemetry management** – Be careful when you add custom telemetry. Ensure that any other data that is collected provides value that is significant enough to justify the cost.

### Data retention policies

- **Archiving practices** – Regularly archive telemetry data that is more than 30 days old to more cost-effective storage solutions. This approach helps you manage storage costs and also lets you retain access to historical data.
- **Retention configuration** – Adjust data retention settings in Application Insights to align them with your organization's compliance and analysis requirements. This approach helps optimize storage expenses.

### Sampling techniques

Sampling provides a way to reduce telemetry traffic, data costs, and storage costs, and also preserve a statistically correct analysis of application data. It's intended for scenarios where measurements are done, and single entries might not be statistically relevant. (For example, the average posting time that is tracked for an invoice remains relevant for only 70% of the invoices.)

- **Implementation of sampling** – Use sampling to collect a representative subset of telemetry data. This approach reduces data ingestion volumes and costs without significantly compromising insights.
- **Adaptive sampling** – Use adaptive sampling features to automatically adjust the sampling rate based on traffic patterns. This approach ensures efficient data collection.

Learn more about sampling in [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] in [Sampling in Azure Application Insights](/azure/azure-monitor/app/sampling-classic-api).

### Monitoring and alerts

- **Cost monitoring** – Use Azure Cost Management tools to monitor Application Insights usage and set up alerts for unusual spending patterns.
- **Daily caps** – To prevent unexpected cost overruns, consider setting daily caps on data ingestion. Be careful, because data loss might occur if the cap is reached.

## Best practices from the Azure Application Insights team

- **[Workspace-based resources](/azure/azure-monitor/best-practices-cost)** – Ensure that your Application Insights resources are workspace-based, so that you can take advantage of cost-saving features such as Basic Logs and commitment tiers.
- **Data ingestion management** – Configure data collection to avoid unnecessary ingestion. Regularly review and adjust the types and amounts of data that are collected, to align them with your monitoring needs.
- **Retention and archiving configuration** – Set appropriate retention periods for different data types. Use archiving for long-term storage to manage costs effectively.

## Related information

- **[Well-Architected Framework perspective on Application Insights](/azure/well-architected/service-guides/application-insights)** – This article provides best practices for Application Insights, based on the five pillars of the Azure Well-Architected Framework.
- **[Cost optimization in Azure Monitor](/azure/azure-monitor/best-practices-cost)** – This article offers recommendations for configuring data collection and retention to optimize costs in Azure Monitor. Those recommendations are applicable to Application Insights.
- **[Monitoring and telemetry using Application Insights](/dynamics365/fin-ops-core/dev-itpro/sysadmin/monitoring-and-telemetry-appinsights)** – This article explains how to set up and use Application Insights for monitoring in [!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)].

By implementing the strategies that are described in this article and adhering to best practices, organizations can effectively control telemetry costs in [!INCLUDE[finops-product-name-short](includes/finops-product-name-short.md)] and also maintain comprehensive monitoring capabilities.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
