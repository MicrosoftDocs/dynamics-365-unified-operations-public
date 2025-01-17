---
title: Gather monitoring requirements
description: Learn how to identify monitoring requirements.
author: kennysaelen
ms.topic: how-to
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Gather monitoring requirements

[!include [banner](../includes/banner.md)]

To build an effective monitoring and telemetry solution in finance and operations apps, it's crucial that you define the correct set of requirements. This approach also ensures that the solution is aligned with your team's needs and delivers actionable insights that help maintain the health of your applications. Use the information in this article to establish a strong foundation for your monitoring and telemetry strategy.

## Understand your business objectives

Begin by identifying the overarching goals (objectives) that your monitoring solution should support. These objectives should be aligned with the strategic priorities of your organization.

**Examples of objectives:**

- Reduce downtime, and improve system availability.
- Optimize performance to enhance the user experience.
- Monitor compliance with Service Level Agreements (SLAs).
- Gain visibility into key business processes.

## Identify key stakeholders

Gather input from all stakeholders who will use or benefit from the monitoring solution.

**Common stakeholders:**

- IT Operations teams
- Development teams
- Product managers
- Customer support teams
- Executive leadership

**Sample questions to ask stakeholders:**

- What information is critical for your role?
- What issues or pain points do you face today?
- How do you plan to use telemetry data in your workflows?

## Define use cases

Document specific scenarios where monitoring and telemetry are required. Use cases help ensure that the solution meets real-world needs.

**Sample use cases:**

- Monitoring API call success and failure rates
- Alerting about anomalous increases in response time
- Monitoring P50, P95, P99, and so on, for purchase order processing
- Tracking customer interactions through a sales pipeline
- Measuring resource consumption to optimize costs

## Determine metrics and KPIs

Define the key metrics and key performance indicators (KPIs) that provide insights into the health and performance of your application.

**Categories of metrics:**

- **Performance metrics** – Response time, throughput, and latency.
- **Error metrics** – Exception rates and failed transaction counts.
- **Business metrics** – Conversion rates and revenue impact.
- **Infrastructure metrics** – CPU usage, memory usage, and disk I/O.

## Establish alerting and notification requirements

Identify the conditions under which alerts should be triggered, and determine how notifications are managed.

**Alerting best practices:**

- Set thresholds that balance sensitivity and relevance.
- Use severity levels to prioritize alerts.
- Define escalation paths for unresolved alerts.

**Notification channels:**

- Email
- Text (SMS)
- Microsoft Teams/Slack integrations

## Consider data retention and privacy

Define how long telemetry data should be retained, and ensure compliance with data privacy regulations.

- **Retention periods** – Align retention periods with business and compliance needs. Consider costs, and establish an archiving policy.
- **Privacy considerations** – Ensure that personally identifiable information (PII) is excluded or anonymized where necessary.

## Evaluate visualization needs

Determine how telemetry data should be visualized to provide actionable insights.

- **Dashboards** – Create role-specific dashboards (for example, operational and business).
- **Reports** – Define periodic reporting needs (for example, weekly SLA compliance).
- **Custom queries** – Use tools such as Azure Data Explorer to explore data interactively.

## Align with organizational governance

Ensure that your monitoring solution adheres to your organization's governance policies.

**Key governance areas:**

- Access control for telemetry data
- Audit trails for changes to monitoring configurations
- Budgetary constraints and cost management

## Thoroughly document requirements

Create a detailed requirements document that can guide the design and implementation of your monitoring solution.

**Information to include:**

- Objectives
- Stakeholder input
- Use cases
- Metrics and KPIs
- Alerting policies
- Data retention policies
- Scalability and resilience plans

## Related information

Explore these Microsoft resources for more guidance about building monitoring and telemetry solutions:

- [Azure Architecture Center: Monitoring and diagnostics guidance](/azure/architecture/best-practices/monitoring)
- [Azure Well-Architected Framework: Recommendations for designing a reliable monitoring and alerting strategy](/azure/well-architected/reliability/monitoring-alerting-strategy)
- [Azure Well-Architected Framework: Recommendations for designing and creating a monitoring system](/azure/well-architected/operational-excellence/observability)
- [Azure Monitor: Plan your Azure Monitor implementation](/azure/azure-monitor/best-practices-plan)

By following the steps in this article, you can ensure that your monitoring and telemetry solution is tailored to your team's needs and provides maximum value. Engage all relevant stakeholders, and periodically revisit these requirements so that you can adapt to changing business and technical needs.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
