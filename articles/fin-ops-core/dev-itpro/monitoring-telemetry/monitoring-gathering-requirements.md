---
title: Gather monitoring requirements
description: Provides information on how to identify monitoring requirements.  
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Gather monitoring requirements

[!include [banner](../includes/banner.md)]

Defining the correct set of requirements is crucial to building an effective monitoring and telemetry solution in finance and operations apps and ensures that the solution aligns with your team’s needs and delivers actionable insights to maintain the health of your applications. Use this guide to establish a strong foundation for your monitoring and telemetry strategy.

## Understand your business objectives

Begin by identifying the overarching goals that your monitoring solution should support. These objectives should align with the strategic priorities of your organization.

- **Example objectives:**
  - Reduce downtime and improve system availability.
  - Optimize performance to enhance user experience.
  - Monitor compliance with SLAs (Service Level Agreements).
  - Gain visibility into key business processes.

## Identify key stakeholders

Gather input from all stakeholders who will use or benefit from the monitoring solution.

- **Common stakeholders:**
  - IT Operations teams
  - Development teams
  - Product managers
  - Customer support teams
  - Executive leadership

- **Sample questions to ask stakeholders:**
  - What information is critical for your role?
  - What issues or pain points do you face today?
  - How do you plan to use telemetry data in your workflows?

## Define use cases

Document specific scenarios where monitoring and telemetry are required. Use cases help ensure the solution meets real-world needs.

- **Sample use cases:**
  - Monitoring API call success and failure rates.
  - Alerting on anomalous increases in response time.
  - Monitoring P50, P95, P99, etc. for Purchase order processing
  - Tracking customer interactions through a sales pipeline.
  - Measuring resource consumption to optimize costs.

## Determine metrics and KPIs

Define the key metrics and performance indicators that provide insights into the health and performance of your application.

- **Categories of metrics:**
  - **Performance Metrics:** Response time, throughput, latency.
  - **Error Metrics:** Exception rates, failed transaction counts.
  - **Business Metrics:** Conversion rates, revenue impact.
  - **Infrastructure Metrics:** CPU usage, memory usage, disk I/O.

## Establish alerting and notification requirements

Identify the conditions under which alerts should be triggered and determine how notifications are managed.

- **Alerting best practices:**
  - Set thresholds that balance sensitivity and relevance.
  - Use severity levels to prioritize alerts.
  - Define escalation paths for unresolved alerts.

- **Notification channels:**
  - Email
  - SMS
  - Microsoft Teams/Slack integrations

## Consider data retention and privacy

Define how long telemetry data should be retained and ensure compliance with data privacy regulations.

- **Retention Periods:** Align with business and compliance needs. Take costs into consideration and set archiving policy.
- **Privacy Considerations:** Ensure PII (Personally Identifiable Information) is excluded or anonymized where necessary.

## Evaluate visualization needs

Determine how telemetry data is to be visualized to provide actionable insights.

- **Dashboards:** Create role-specific dashboards (for example, operational, business).
- **Reports:** Define periodic reporting needs (for example, weekly SLA compliance).
- **Custom Queries:** Use tools like Azure Data Explorer to explore data interactively.

## Align with organizational governance

Ensure your monitoring solution adheres to your organization’s governance policies.

- **Key governance areas:**
  - Access control for telemetry data.
  - Audit trails for changes to monitoring configurations.
  - Budgetary constraints and cost management.

## Document requirements thoroughly

Create a detailed requirements document that can guide the design and implementation of your monitoring solution.

- **Include:**
  - Objectives
  - Stakeholder inputs
  - Use cases
  - Metrics and KPIs
  - Alerting policies
  - Data retention policies
  - Scalability and resilience plans

## Related information

Explore these Microsoft resources for more guidance on building monitoring and telemetry solutions:

- [Azure Architecture Center: Monitoring and Diagnostics Guidance](/azure/architecture/best-practices/monitoring)
- [Azure Well-Architected Framework: Designing a Reliable Monitoring and Alerting Strategy](/azure/well-architected/reliability/monitoring-alerting-strategy)
- [Azure Well-Architected Framework: Designing and Creating a Monitoring System](/azure/well-architected/operational-excellence/observability)
- [Azure Monitor: Planning Your Implementation](/azure/azure-monitor/best-practices-plan)

By following these steps, you can ensure that your monitoring and telemetry solution is tailored to your team’s needs and provides maximum value. Engage all relevant stakeholders and revisit these requirements periodically to adapt to changing business and technical needs.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
