---
title: Understanding and controlling cost.
description: Provides information about the various cost and pricing options.
author: kesaelen
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: kesaelen
ms.custom: bap-template
---

# Understanding and controlling cost

Managing telemetry cost in Dynamics 365 is crucial, as data sent to Azure Application Insights incurs charges based on many aspects. Implementing effective strategies can help control these expenses while maintaining robust monitoring. Below are guidelines from both the Dynamics 365 Application Insights team and the Azure Application Insights team, along with additional resources.

## Understanding Telemetry Costs
Azure Application Insights is an extension on top of Azure Monitor and the cost of Azure Monitor is including many aspects, but the main driver is ingestion and retention of data. Azure Application Insights provides the necessary tools to gain insights into the current usage, provides ways to automate retrieval of usage cost information and provides ways to set thresholds and alert when exceeding those thresholds.

To have a better understanding of all the cost aspects, see [Azure Monitor cost and usage](https://learn.microsoft.com/azure/azure-monitor/cost-usage).

## Strategies for Controlling Telemetry Costs

### Selective Telemetry Collection

- **Production Environment Focus**: Configure Application Insights to collect only essential telemetry in production environments. This approach reduces data volume and associated costs.
- **Custom Telemetry Management**: Exercise caution when adding custom telemetry. Ensure that any additional data collected provides significant value to justify the cost.

### Data Retention Policies

- **Archiving Practices**: Regularly archive telemetry data older than 30 days to more cost-effective storage solutions. This practice helps in managing storage costs while retaining access to historical data.
- **Retention Configuration**: Adjust data retention settings in Application Insights to align with your organization's compliance and analysis requirements, thereby optimizing storage expenses.

### Sampling Techniques
Sampling provides way to reduce telemetry traffic, data costs, and storage costs, while preserving a statistically correct analysis of application data. It works particularly well in scenarios where measurements are done and where single entries might not be statistically relevant. (Example: Tracking the average posting time for an invoice can be still be relevant on only 70% of the invoices.)

- **Implement Sampling**: Use sampling to collect a representative subset of telemetry data. This method reduces data ingestion volumes and costs without significantly compromising insights.
- **Adaptive Sampling**: Leverage adaptive sampling features to automatically adjust the sampling rate based on traffic patterns, ensuring efficient data collection.

For more information about sampling in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)], see [Sampling in Azure Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/sampling-classic-api).

### Monitoring and Alerts

- **Cost Monitoring**: Utilize Azure Cost Management tools to monitor Application Insights usage and set up alerts for unusual spending patterns.
- **Daily Caps**: Consider setting daily caps on data ingestion to prevent unexpected cost overruns. Be cautious, as this may lead to data loss if the cap is reached.

## Best Practices from Azure Application Insights Team

- **[Workspace-Based Resources](https://learn.microsoft.com/azure/azure-monitor/best-practices-cost)**: Ensure that your Application Insights resources are workspace-based to take advantage of cost-saving features like Basic Logs and commitment tiers. 
- **Data Ingestion Management**: Configure data collection to avoid unnecessary ingestion. Regularly review and adjust the types and amounts of data collected to align with your monitoring needs.
- **Retention and Archiving Configuration**: Set appropriate retention periods for different data types and utilize archiving for long-term storage to manage costs effectively.

## Additional Resources

- **[Well-Architected Framework Perspective on Application Insights](https://learn.microsoft.com/azure/well-architected/service-guides/application-insights)**
Provides best practices for Application Insights based on the five pillars of the Azure Well-Architected Framework. 
- **[Cost Optimization in Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/best-practices-cost)**
Offers recommendations on configuring data collection and retention to optimize costs in Azure Monitor, applicable to Application Insights. 
- **[Monitoring and Telemetry Using Application Insights](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/sysadmin/monitoring-and-telemetry-appinsights)**
Discusses how to set up and use Application Insights for monitoring in [!INCLUDE[finops-product-name-short](./includes/finops-product-name-short.md)].

By implementing these strategies and adhering to best practices, organizations can effectively control telemetry costs in [!INCLUDE[finops-product-name-short](./includes/finops-product-name-short.md)] while maintaining comprehensive monitoring capabilities.
