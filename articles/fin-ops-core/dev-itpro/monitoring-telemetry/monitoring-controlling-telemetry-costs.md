---
title: Controlling Telemetry Costs
description: Provides information on how to control costs incurred due to usage of Application Insights.  
author: kesaelen
ms.topic: overview
ms.search.keywords: Costs, Application Insights, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: kesaelen
ms.custom: bap-template
---
# Controlling telemetry Costs
Managing telemetry costs in Dynamics 365 is crucial, as data sent to Azure Application Insights incurs charges based on usage. Implementing effective strategies can help control these expenses while maintaining robust monitoring. Below are guidelines from both the D365 F&O Application Insights team and the Azure Application Insights team, along with additional resources.

---

## Strategies for Controlling Telemetry Costs

### 1. Selective Telemetry Collection

- **Production Environment Focus**: Configure Application Insights to collect only essential telemetry in production environments. This approach reduces data volume and associated costs.
- **Custom Telemetry Management**: Exercise caution when adding custom telemetry. Ensure that any additional data collected provides significant value to justify the cost.

### 2. Data Retention Policies

- **Archiving Practices**: Regularly archive telemetry data older than 30 days to more cost-effective storage solutions. This practice helps in managing storage costs while retaining access to historical data.
- **Retention Configuration**: Adjust data retention settings in Application Insights to align with your organization's compliance and analysis requirements, thereby optimizing storage expenses.

### 3. Sampling Techniques

- **Implement Sampling**: Use sampling to collect a representative subset of telemetry data. This method reduces data ingestion volumes and costs without significantly compromising insights.
- **Adaptive Sampling**: Leverage adaptive sampling features to automatically adjust the sampling rate based on traffic patterns, ensuring efficient data collection.

### 4. Monitoring and Alerts

- **Cost Monitoring**: Utilize Azure Cost Management tools to monitor Application Insights usage and set up alerts for unusual spending patterns.
- **Daily Caps**: Consider setting daily caps on data ingestion to prevent unexpected cost overruns. Be cautious, as this may lead to data loss if the cap is reached.

---

## Best Practices from Azure Application Insights Team

- **Workspace-Based Resources**: Ensure that your Application Insights resources are workspace-based to take advantage of cost-saving features like Basic Logs and commitment tiers. ([learn.microsoft.com](https://learn.microsoft.com/en-us/azure/azure-monitor/best-practices-cost?utm_source=chatgpt.com))
- **Data Ingestion Management**: Configure data collection to avoid unnecessary ingestion. Regularly review and adjust the types and amounts of data collected to align with your monitoring needs.
- **Retention and Archiving Configuration**: Set appropriate retention periods for different data types and utilize archiving for long-term storage to manage costs effectively.

---

## Additional Resources

- **Well-Architected Framework Perspective on Application Insights**: Provides best practices for Application Insights based on the five pillars of the Azure Well-Architected Framework. ([learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/service-guides/application-insights?utm_source=chatgpt.com))
- **Cost Optimization in Azure Monitor**: Offers recommendations on configuring data collection and retention to optimize costs in Azure Monitor, applicable to Application Insights. ([learn.microsoft.com](https://learn.microsoft.com/en-us/azure/azure-monitor/best-practices-cost?utm_source=chatgpt.com))
- **Monitoring and Telemetry Using Application Insights**: Discusses how to set up and use Application Insights for monitoring in D365 F&O. ([learn.microsoft.com](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/monitoring-and-telemetry-appinsights?utm_source=chatgpt.com))

---

By implementing these strategies and adhering to best practices, organizations can effectively control telemetry costs in D365 F&O while maintaining comprehensive monitoring capabilities.
