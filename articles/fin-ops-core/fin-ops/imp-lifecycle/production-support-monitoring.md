---
# required metadata

title: Production support and monitoring
description: This topic describes the types of support involved in the lifecycle of the project and best practices on monitoring your environments.
author: PedroTubal
manager: AnnBe
ms.date: 03/26/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: v-petbal
ms.search.validFrom: 2021-03-31
ms.dyn365.ops.version: 10.0.14

---

# Production support and monitoring

[!include[banner](../includes/banner.md)]

To ensure a good experience during the implementation and after the go-live of the project, it's important to understand the several types of servicing available and how to get the proper support for every scenario. The following will provide you with an overview of how to engage each type of support and how some of the tools will help you keep your business continually accounting for all business needs.

Microsoft tools and support ensure the stability and effectiveness of your enivornment by providing infrastructural and application support. However, the effectiveness of this support is dependent on partner/client responsibility to correctly develop, test, configure, manage, and monitor the implemented system and its environments.

![Support Provided by Microsoft](./media/support-provided-microsoft.png)
 
## Supporting actions
Supporting actions can be grouped into three categories:

- Self-service
- Service request
- Support request

Depending on the category, the actions are triggered in different ways and may encompass different lead times.

### Self-service
Self-service action can be triggered by the user at any moment with no lead time. The reasons to initiate a self-service action include:

- Promote code (non-production)
- [Move databases between non-production environments](../../dev-itpro/database/dbmovement-operations.md)
- [Upgrade production](../../dev-itpro/migration-upgrade/upgrade-latest-update.md)
- [Maintenance mode](../../dev-itpro/sysadmin/maintenance-mode.md)
- Pause upcoming automatic deployment of a service update
- Restart services on non-production environments
- Performance actions

### Service request
A service request is usually triggered by a creating a Support ticket. It involves the cooperation of the Dynamics Service Engineering (DSE) team  and each request will have a designated lead time. Some of the reasons to create a service request are:

- Environment deployment request

#### Recommended practices when working with the DSE team:
- Consider that there are turn-around times or Service Level Agreements (SLAs) for each type of service request.
- Don't use a service request if a support request better suits your case.
- Consult the [Service request types and SLAs](../../dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team.md#service-request-types-and-slas) to make sure that you're making the right type of request

### Support request 
There are other scenarios that can usually be resolved by opening a support request. These requests have a lead time. Some of the reasons to create a support request are:

- Production point-in-time restore after Go-Live
- Flag a regression in a Service Update and ask for an exception opt-out
- Performance related requests (for tasks not possible through self-service)
- Flighting feature activation (for example customer and vendor master data sharing)
- Production resizing (update and upload a new usage profile in the LCS subscription estimator first)
- Additional LCS project on the same tenant
- Moving tenant of Production environments

## Requesting support

For an effective support process, a clear escalation path must be defined. Project teams (client/partner) should be able to monitor and read environment telemetry and be capable of conducting initial troubleshooting when necessary.

A well-identified problem and a well-defined resolution process can make a difference in the effectiveness of the outcome.

An effective support request should include:

- Environment where the issue occurs
- The process in which the issue was identified
- Reproducible steps to show where the issue occurred
- The expected result and the actual result
- Pre-investigation of the issue
- Additional elements (error message, screenshots, session ID, trace, …)

### High severity support requests
A high severity support request should include:

- **Business impact**: What is the impact of the issue on your business activities?
- **Financial impact**: How does this issue impact your business on a financial level?

A thorough analysis of the problem should be done before reporting the issue. When the request for support includes detailed information, using all available tools and telemetries, the incident resolution will be much quicker. Including the proper information up-front will save a great deal of time in back-and-forth communications that often takes place to identify the problem and replicate the issue.

There are various [support plans](https://go.microsoft.com/fwlink/?LinkId=871952) to choose from, there will always be the right one for each business.

Before requesting support, you should remember that it's important to choose the proper level of severity.

To identify the correct severity level and estimate the initial response time for you request, please consult the [Support overview](https://docs.microsoft.com/power-platform/admin/support-overview?toc=/dynamics365/fin-ops-core/dev-itpro/toc.json&amp;bc=/dynamics365/breadcrumb/toc.json#what-is-initial-response-time-and-how-quickly-can-i-expect-to-hear-back-from-someone-after-submitting-my-support-request) and [Report a production outage](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/report-production-outage) documentation.

## Monitoring elements

LCS has integrated a set of tools that can be used to properly monitor LCS projects.

### Service health dashboard

The [Service health dashboard](https://portal.office.com/servicestatus) provides the health status for Office 365 Services.

You can also view the service health through the admin center. Go to **Health** > **Service health** or select the **Service health** card on the **Home dashboard**.

The **All services** tab (the default view) shows all services and their current health state. An icon and the **Status** column indicate the state of each service.

If you're experiencing an issue with a Microsoft 365 service and you don't see it listed on the **Service health** page, tell us about it by selecting **Report an issue**, and completing the short form.

These reports will help to identify issues. Once identified, incidents will be shown in the report.

You can sign up to receive email communication, ensuring quick alerts on identified issues in the tenant and their status change.

### Environment monitoring

Environment monitoring is a set of tools that help you to monitor and [troubleshoot the health of your environments through LCS portal](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/monitoring-diagnostics).

Within a specific environment page of the project, you'll find a link that will guide you to this dashboard on the monitoring section.

Some of the tools available are:

#### Overview 
Common to most of the environment types, provides a filterable way to trace user activity, and load by activity during a defined period.

#### Activity
Tab will enable you to query through raw logs with the help of predefined queries for the most common events and metrics useful to monitor your environment. This tab has the additional functionality of adding your own custom filters and letting you export the logs into a csv file for analysis.

![Activity screen](./media/activity.png)
 
Some of the pre-defined queries are for:

- Slow queries
- Deadlocks
- Crashes
- Financial reporting issues
- Batch throttle
- Distinct user sessions

#### Health Metrics
This Dashboard provides a series of line charts, filtered by instance (AOS or Batch AOS) and time frame through which it's possible to observe SQL execution in the **AOS** tab and system memory and CPU utilization over time in the **System tab**. Through this tool, you can easily identify behavioral changes that may help you to trace in time issues and the impact of changes in the solution.

#### SQL Insights
SQL Insights provide advanced SQL troubleshooting tools to enable performance analysis. Some of these tools are similar to the DynPerf tool that was used for SQL troubleshooting in Microsoft Dynamics AX 2012. For a more detailed analysis, see [Performance troubleshooting using tools](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/performancetroubleshooting) and watch the [TechTalk](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-performance-troubleshooting-tools-for-dynamics-365-12-14-18).

SQL Insights is a reliable way to collect performance metrics on demand and enables customers and partners to execute a predefined set of actions that can be used to mitigate issues in a sandbox or production environment. This feature queries SQL Server directly, so you get query store metrics in near real time.

While it's important to monitor your environments, it doesn't mean that you must always be on constant lookout. Microsoft also uses the emails provided to you in the LCS notification list to alert you to important issues and actions that you need to take, as well as to provide preventive guidance for the implementation itself.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
