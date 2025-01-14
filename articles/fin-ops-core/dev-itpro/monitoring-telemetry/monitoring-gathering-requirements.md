---
title: Gathering monitoring requirements
description: Provides information on how to identify monitoring requirements.  
author: kesaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Gathering monitoring requirements

Defining the correct set of requirements is crucial to building an effective monitoring and telemetry solution in D365 and ensures that the solution aligns with your team’s needs and delivers actionable insights to maintain the health of your applications. Use this guide to establish a strong foundation for your monitoring and telemetry strategy.

## Understand Your Business Objectives
Begin by identifying the overarching goals that your monitoring solution should support. These objectives should align with the strategic priorities of your organization.

- **Example Objectives:**
  - Reduce downtime and improve system availability.
  - Optimize performance to enhance user experience.
  - Monitor compliance with SLAs (Service Level Agreements).
  - Gain visibility into key business processes.

## Identify Key Stakeholders
Gather input from all stakeholders who will use or benefit from the monitoring solution.

- **Common Stakeholders:**
  - IT Operations teams
  - Development teams
  - Product managers
  - Customer support teams
  - Executive leadership

- **Sample Questions to Ask Stakeholders:**
  - What information is critical for your role?
  - What issues or pain points do you face today?
  - How do you plan to use telemetry data in your workflows?

## Define Use Cases
Document specific scenarios where monitoring and telemetry are required. Use cases help ensure the solution meets real-world needs.

- **Sample Use Cases:**
  - Monitoring API call success and failure rates.
  - Alerting on anomalous increases in response time.
  - Monitoring P50, P95, P99 etc for Purchase order processing
  - Tracking customer interactions through a sales pipeline.
  - Measuring resource consumption to optimize costs.

## Determine Metrics and KPIs
Define the key metrics and performance indicators that provide insights into the health and performance of your application.

- **Categories of Metrics:**
  - **Performance Metrics:** Response time, throughput, latency.
  - **Error Metrics:** Exception rates, failed transaction counts.
  - **Business Metrics:** Conversion rates, revenue impact.
  - **Infrastructure Metrics:** CPU usage, memory usage, disk I/O.

## Establish Alerting and Notification Requirements
Identify the conditions under which alerts should be triggered and determine how notifications are managed.

- **Alerting Best Practices:**
  - Set thresholds that balance sensitivity and relevance.
  - Use severity levels to prioritize alerts.
  - Define escalation paths for unresolved alerts.

- **Notification Channels:**
  - Email
  - SMS
  - Microsoft Teams/Slack integrations

## Consider Data Retention and Privacy
Define how long telemetry data should be retained and ensure compliance with data privacy regulations.

- **Retention Periods:** Align with business and compliance needs. Take costs into consideration and set archiving policy.
- **Privacy Considerations:** Ensure PII (Personally Identifiable Information) is excluded or anonymized where necessary.

## Evaluate Visualization Needs
Determine how telemetry data is to be visualized to provide actionable insights.

- **Dashboards:** Create role-specific dashboards (e.g. operational, business).
- **Reports:** Define periodic reporting needs (e.g. weekly SLA compliance).
- **Custom Queries:** Use tools like Azure Data Explorer to explore data interactively.

## Align with Organizational Governance
Ensure your monitoring solution adheres to your organization’s governance policies.

- **Key Governance Areas:**
  - Access control for telemetry data.
  - Audit trails for changes to monitoring configurations.
  - Budgetary constraints and cost management.

## Document Requirements Thoroughly
Create a detailed requirements document that can guide the design and implementation of your monitoring solution.

- **Include:**
  - Objectives
  - Stakeholder inputs
  - Use cases
  - Metrics and KPIs
  - Alerting policies
  - Data retention policies
  - Scalability and resilience plans

## Additional Resources for Further Learning

Explore these Microsoft resources for additional guidance on building monitoring and telemetry solutions:

- [Azure Architecture Center: Monitoring and Diagnostics Guidance](https://learn.microsoft.com/azure/architecture/best-practices/monitoring)
- [Azure Well-Architected Framework: Designing a Reliable Monitoring and Alerting Strategy](https://learn.microsoft.com/azure/well-architected/reliability/monitoring-alerting-strategy)
- [Azure Well-Architected Framework: Designing and Creating a Monitoring System](https://learn.microsoft.com/azure/well-architected/operational-excellence/observability)
- [Azure Monitor: Planning Your Implementation](https://learn.microsoft.com/azure/azure-monitor/best-practices-plan)

By following these steps, you can ensure that your monitoring and telemetry solution is tailored to your team’s needs and provides maximum value. Engage all relevant stakeholders and revisit these requirements periodically to adapt to changing business and technical needs.
