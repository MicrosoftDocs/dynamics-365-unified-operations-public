---
# required metadata

title: Post Go-live FAQ
description: types of support involved in the lifecycle of the project and best practices on monitoring your environments.
author: PedroTubal
manager: AnnBe
ms.date: 03/08/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer:
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: v-petbal
ms.search.validFrom: 2021-03-03
ms.dyn365.ops.version: AX 10.0.14
---

# Production Support and Monitoring

[!include[banner](../includes/banner.md)]

To ensure a good experience during the implementation and after the go-live of the project it is important to understand the several types of servicing available and how to get the proper support for every scenario. Let&#39;s take a look into how to properly engage into each type of support and learn about some of the tools that will help you to keep the business continuity accounting for all the needs.

Microsoft tools and support ensure the stability and effectiveness of implemented platform by providing infrastructural and applicational support, but the effectiveness of those is dependent on Partner/Client responsibility to correctly develop, test, configure, manage and monitor the implemented system and its environments.

:::row:::
   :::column span="":::
![Support Provided by Microsoft](./media/support-provided-microsoft.png)
   :::column-end:::
:::row-end:::

The servicing actions provided can be inserted in one three categories: Self-service, Service Request and Support Request; depending on the category of the action they are triggered in different ways and may encompass a lead time.

The servicing actions provided can be inserted in one three categories:

### Self-service
Can be triggered by the user at any moment with no lead time, the self-service actions include:

- Code promotion (non-production)
- [Database](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/database/dbmovement-operations)[movement](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/database/dbmovement-operations)[between](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/database/dbmovement-operations)[non-production](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/database/dbmovement-operations)[environments](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/database/dbmovement-operations)
- [Production upgrade](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/migration-upgrade/upgrade-latest-update)
- [Maintenance mode](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/sysadmin/maintenance-mode)
- Pause upcoming automatic deployment of a service update
- Restarting services on non-production environments
- Performance actions

### Service Request
Usually triggered by a ticked involve the cooperation of the Dynamics Service Engineering team (DSE) and have a lead time, some of these actions include:

- FastTrack assessment process for the PRODUCTION environment
- Code promotion to production
- Production Point in Time restore prior to go-live
- Sandbox to Production prior to go-live

#### Some of the recommended practices when working with the DSE team:
- Account for the team SLAs
- Not using service request when a support request is more adapted
- Consulting the service [request catalog](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team#service-request-types-and-slas) to make sure that it&#39;s the right type of request you are making

### Support Request 
Remaining not Self-service scenarios usually triggered by opening a ticket, generally have a lead time, included in the category are:

- Production point-in-time restore after Go-Live
- Flag a regression in a Service Update and ask for an exception opt-out
- Performance related requests (for tasks not possible through self service)
- Flighting feature activation (e.g. customer and vendor master data sharing)
- Production resizing (Update and upload a new usage profile in the LCS subscription estimator first)
- Additional LCS project on the same tenant
- Moving tenant of PRODUCTION environments

## Requesting Support

For an effective support process a clear escalation path has to be defined, project supporting teams (client/partner) should be able to monitor and read environment telemetry as well as being capable of doing an initial troubleshooting.

A well identified problem and well-defined resolution process can make the difference on the effectiveness of the resolution scenario.

An **effective support request** should mention:

### Quality input

#### Quality investigation:

- Environment where the issue occurs
- The process
- The reproduction steps
- The expected result / actual result
- Pre-investigation
- Additional elements (error message, screenshots, session ID, trace, …)

#### If high severity:

- Business impact: what&#39;s the impact of your business activities?
- Financial impact: how does it impact you financially?

To effectively identify the reported issue, a pre-analysis of the problem should be done before reporting, providing the most detailed information, with the gathered telemetry using the available tools, the incident resolution will be much quicker, saving precious time on information gathering to identify and replicate the issue.

There is a verity of [support plans](https://go.microsoft.com/fwlink/?LinkId=871952&amp;clcid=0x409) to choose from, so that there will always be right one for each business.

Before requesting support, you should remember that it is important to choose the proper level of severity.

|     Severity level                                       	|     Customer's situation                                                                                                                                           	|     Initial Response Time                                                                   	|
|----------------------------------------------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------	|
|     Production Outage     (exclusive to LCS Projects)    	|     Critical business impact     Production   down scenarios (see   this Docs article)     Make sure to   inform the TAM / FastTrack SA via email for awareness    	|     <30   minutes, 24/7                                                                     	|
|     Critical                                             	|     Critical business impact   Customer's business has significant loss or degradation of services and   requires immediate attention.                             	|     Unified Core/Advanced: < 1 hour, 24/7    Unified Performance: < 30 minutes, 24/7        	|
|     Severity A                                           	|     Critical business impact   Customer's business has significant loss or degradation of services and   requires immediate attention.                             	|     Subscription: < 1 hour, 24/7    ProDirect: < 1 hour, 24/7    Premier: < 1 hour, 24/7    	|
|     Severity B                                           	|     Moderate business impact   Customer's business has moderate loss or degradation of services, but work   can reasonably continue in an impaired manner.         	|     Subscription: < 4 hours    ProDirect: < 2 hours    Premier: < 2 hours, 24/7             	|
|     Standard                                             	|     Standard business impact   Customer's business has moderate loss or degradation of services, but work   can reasonably continue in an impaired manner.         	|     Unified Core: < 8 hours, 24/7    Unified Advanced/Performance: < 4 hours, 24/7          	|
|     Severity C                                           	|     Minimum business impact   Customer's business is functioning with minor impediments of services.                                                               	|     Subscription: < 8 hours    ProDirect: < 4 hours    Premier: < 4 hours                   	|

## Monitoring elements

LCS has integration with set of tools that can be used to properly monitor LCS projects, those tools include:

### Service Health Dashboard

[Service Health Dashboard](https://portal.office.com/servicestatus) where the health status and incidents can be found for Office365 Services.

You can also view the service heath through admin center, go to  **Health**  >  **Service health** , or select the  **Service health**  card on the  **Home dashboard**.

The All services tab (the default view) shows all services and their current health state. An icon and the Status column indicate the state of each service.

If you're experiencing an issue with a Microsoft 365 service and you don&#39;t see it listed on the  **Service health**  page, tell us about it by selecting  **Report an issue** , and completing the short form.

Those reports will help identifying issues, once identified, incidents will be shown on the report.

You can signup to receive email communication, ensuring quick alert on identified issues on the tenant and their status change.

### Environment monitoring

Environment monitoring is a set of tolls that help you to monitor and troubleshoot the health of your environments through LCS portal.

Within a specific environment page of the project, you will find a link that will guide you to this dashboard on the monitoring section.

Some of the tools available are:

#### Overview 
Common to most of the environment types, provides a filterable way to trace user activity, load and load by activity during a defined period.

#### Activity
Tab will enable you to query through raw logs with the help of predefined queries for the most common events and metrics useful to monitor your environment. This tab has the additional functionality of adding your own custom filters and letting you export the logs into a csv file for analysis.

:::row:::
   :::column span="":::
![Activity screen](./media/activity.png)
   :::column-end:::
:::row-end:::

Some of the pre-defined queries are for:

- Slow queries
- Deadlocks
- Crashes
- Financial reporting issues
- Batch throttle
- Distinct user sessions

#### Health Metrics
Dashboard provides a series of line charts, filtered by instance (AOS or Batch AOS) and time frame through winch its possible to observe SQL execution in **AOS** tab and system memory and CPU utilization over time in the tab **System**. Through this toll you can easily identify behavioral changes that may help you to trace in time issues and the impact of changes in the solution.

#### SQL Insights
Provides advanced SQL troubleshooting tools to enable performance analysis. Some of these tools are similar to the DynPerf tool that was used for SQL troubleshooting in Microsoft Dynamics AX 2012. For a more detailed analysis, see [Performance troubleshooting using tools in Lifecycle Services (LCS)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/performancetroubleshooting).

It is a reliable way to collect performance metrics on demand. Enables customers and partners to execute a predefined set of actions that can be used to mitigate issues in a sandbox or production environment. This feature queries SQL Server directly, so you get query store metrics in near real-time.

Monitoring nature isn&#39;t always of active involvement, it&#39;s important to be aware that Microsoft also uses the provided emails in LCS notification list to directly inform about high importance issues, actions that need to be taken and to give preventive guidance for the implementation.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
