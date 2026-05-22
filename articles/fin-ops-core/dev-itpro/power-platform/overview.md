---
title: Microsoft Power Platform integration with finance and operations apps
description: Learn about Microsoft Power Platform integration via Microsoft Dynamics Lifecycle Services for finance and operations apps and Microsoft Dataverse.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.0
---

# Microsoft Power Platform integration with finance and operations apps

[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> Beginning **May 1, 2025**, all environments for finance and operations apps must have the Power Platform Integration enabled. Before this date, environment administrators should enable the Power Platform Integration by following the steps in this article, selecting the Power Platform environment to which the environment for your finance and operations apps should be linked. After this date, any finance and operations apps environments that aren't linked to a Power Platform environment through the Power Platform Integration have the Power Platform Integration automatically enabled for the environment. During automated enablement, the environment is either linked to a newly provisioned Power Platform environment, or linked to an existing Power Platform environment if either [dual-write](../data-entities/dual-write/dual-write-home-page.md) or [virtual entities for finance and operations apps](../power-platform/virtual-entities-overview.md) has already been enabled for the environment.
> Learn more about enabling and configuring the integration in [Enabling the Power Platform integration](./enable-power-platform-integration.md).

Microsoft Power Platform provides a suite of capabilities for Dynamics 365 applications via the Power Platform admin center. Today, the Power Platform admin center doesn't manage finance and operations apps. However, over time, Microsoft is migrating more management capabilities from Microsoft Dynamics Lifecycle Services to the admin center. In the interim, you can unlock features such as dual-write functionality, virtual entities, add-ins, and more by using Microsoft Power Platform integration functionality in Lifecycle Services.

## Getting started

To learn more about how to connect your environment to either a new or an existing Power Platform environment, see [Enable Power Platform Integration](enable-power-platform-integration.md).

## Prerequisite reading

To understand the architecture of Microsoft Power Platform, Dataverse, dual-write, and virtual entities for finance and operations apps, you must understand how they work. Therefore, the following documentation is a prerequisite:

- [Administer Power Platform](/power-platform/admin/admin-documentation)
- [What is Dataverse?](/powerapps/maker/common-data-service/data-platform-intro)
- [Tables in Dataverse](/powerapps/maker/common-data-service/entity-overview)
- [Entity relationships overview](/powerapps/maker/common-data-service/relationships-overview)
- [Create and edit virtual tables that contain data from an external data source](/powerapps/maker/common-data-service/create-edit-virtual-entities)
- [What is Power Apps portals?](/powerapps/maker/portals/overview)
- [Overview of creating apps in Power Apps](/powerapps/maker/)

## Tools and services unlocked with Microsoft Power Platform integration
The following tools and services are unlocked by using the Power Platform integration, which enables new features in finance and operations apps. As Microsoft continues to unify finance and operations applications with the Microsoft Power Platform, services within the Power Platform ecosystem power an increasing number of capabilities. This integration enables greater flexibility, automation, and intelligence, so businesses can streamline operations and enhance decision-making through low-code applications, process automation, and advanced analytics. As this evolution progresses, organizations can expect improved interoperability between Dynamics 365 applications and Power Platform services, which drives efficiency and innovation across financial and operational workflows.

### Integration tools for data and business logic
Together, virtual entities, dual-write, business events, and data events make up the shared data layer for the convergence of finance and operations apps and the Dataverse platform. They're complementary technologies that work together. 

**Virtual entities** enable scenarios where you need to access finance and operations data from Microsoft Power Platform or native Dataverse apps. You can query that data, bind forms to it, and generally use the full power of Microsoft Power Platform against the full breadth of finance and operations apps. Data isn't copied between systems. Instead, you access it directly through the standard virtual entity infrastructure that Microsoft Power Platform technologies can already bind to. For more information, see [Virtual entities overview](virtual-entities-overview.md). 

**Business events** let you use Microsoft Power Platform to respond to events that occur in finance and operations apps. These events occur when you run a process in the application with business logic. You can raise business events from any app, including finance and operations apps, and Microsoft Power Platform business logic can handle them. This handling often includes querying or interacting with additional data through either native entities or virtual entities. 

**Data events**, similar to business events, enable external applications to receive notifications from finance and operations apps when events occur. Data events occur when there's a change to a record in the application data. External systems can react to notifications when a create, update, or delete (CUD) operation occurs in the data.

For a subset of scenarios, you must physically copy data between finance and operations apps and native Dataverse entities. These scenarios are for overlapping entities that already have a large amount of bound logic in both native Dataverse apps and finance and operations apps, so the data must reside in the local database of each type of app. Although the number of these entities is relatively small, it includes some of the most important entities, such as Account/Customer, Company, Product, and Sales order. For these scenarios, **dual-write** enables near-real-time synchronous copying of data. This capability enables existing apps to continue to operate against local data, as designed, and also ensures that the corresponding overlapping entity stays in sync. For more information, see the [Dual-write home page](../data-entities/dual-write/dual-write-home-page.md). 

Together, virtual entities, dual-write, business events, and data events let you build apps and business processes that span the boundaries between finance and operations apps and native Dataverse apps. Most apps and business processes use either a combination of these three parts of the shared data layer or all of them. As always, extension and customization should reduce the amount of data that you copy between databases as much as possible, and should also optimize for the best possible user experience when you use these tools. 

### AI capabilities enabled by the Power Platform
Finance and operations apps utilize the Power Platform to enable AI features. The features depend on AI services like [Microsoft Copilot Studio](/microsoft-copilot-studio/fundamentals-what-is-copilot-studio), [AI Builder](/ai-builder/overview), and capabilities in [Microsoft Dataverse](/power-apps/maker/data-platform/data-platform-intro) to light up powerful AI features in finance and operations apps. You must enable the Power Platform integration in the environment to access the services for the AI features.

Learn more about some of the AI-driven capabilities in finance and operations apps that the Power Platform enables in [Overview of Copilot capabilities in finance and operations apps](../../fin-ops/copilot/copilot-for-finance-operations.md).

### Data archival
Integration with the Power Platform enables archival of data for finance and operations apps with custom retention policies for securely archiving and retaining unlimited data. By using this feature, you move data from the database for finance and operations apps into Dataverse long-term retention, which enables greater scale for finance and operations apps. To learn more, see [Archive data in Dynamics 365 finance and operations apps with Dataverse](../sysadmin/archive-data.md).

### Add-ins functionality

Add-ins provide a way to extend the functionality of finance and operations apps. You can install and manage all add-ins through Lifecycle Services on the environment details page for sandbox and production-type environments. The Microsoft Dataverse database that is provisioned as part of the Microsoft Power Platform integration stores the metadata regarding which add-ins are installed and the configuration options for each add-in. Some add-ins also store business data in the Dataverse database. To learn more about available add-ins, see [Add-ins overview](add-ins-overview.md).

## Typical scenarios and patterns that use dual-write

Here are some typical scenarios that use dual-write.

### Customer service representatives can facilitate a change of address for finance and operations customers

A customer relocates and wants to change their billing and shipping address information. This customer contacts a customer service representative and requests a change of address. The customer service representative takes the call and changes the customer's billing and shipping address information.

| Decision | Information | 
|----------|-------------|
| Is real-time data required? | Yes |
| Peak data volume | Not applicable |
| Frequency | Ad hoc |

#### Recommended solution

Implement this scenario that involves near-real-time data synchronization by using dual-write.

1. Source the customer's information in a finance and operations app.
1. A customer calls customer service and asks to change their billing and shipping address information.
1. A customer service representative retrieves the customer's record in Dynamics 365 Customer Service.
1. The customer service representative updates the billing and shipping addresses, and saves the data.
1. The new billing and shipping addresses sync back to the finance and operations app in real time.

### Sales representatives can change customer credit limits without signing in to a finance and operations app

A customer has a credit limit of $2,000 and wants to increase it to $5,000. This customer calls and requests the increase. The ticket is assigned to the sales department. The head of sales reviews the request, reviews the customer's payment history, and determines that the customer is eligible for an increased credit limit. The head of sales approves the request and responds to the ticket. The customer receives an email about the approval of the $5,000 credit limit.

| Decision | Information | 
|---------|--------------|
| Is real-time data required? | Yes |
| Peak data volume | Not applicable |
| Frequency | Ad hoc |

#### Recommended solution

Use dual-write to implement this scenario.

1. A customer calls and wants to increase their credit limit from $2,000 to $5,000.
1. A customer support representative creates a ticket in Dynamics 365 Customer Service.
1. The ticket is assigned to the sales unit.
1. A sales representative from the sales unit reviews and approves the request.
1. The customer's credit limit is increased to $5,000 in Dynamics 365 Sales.
1. The credit limit in the finance and operations app is updated to $5,000.
1. The sales representative responds to the ticket and resolves it.
1. The customer receives an email about the increased credit limit.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

