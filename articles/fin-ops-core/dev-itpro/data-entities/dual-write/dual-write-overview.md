---
# required metadata

title: Dual-write overview
description: Dual-write is an infrastructure that provides near-real-time interaction between Microsoft Dynamics 365 model-driven applications and Finance and Operations applications.
author: shsrav
manager: AnnBe
ms.date: 02/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# Dual-write overview

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

## What is dual-write?

Dual-write is an out-of-the-box infrastructure that provides near-real-time interaction between Microsoft Dynamics 365 model-driven applications and Finance and Operations applications. When data on customers, products, people, and operations flow beyond application boundaries, it empowers all departments in an organization.

Dual-write provides tightly-coupled, bi-directional integration between Dynamics 365 for Finance and Operations and the Common Data Service. Any data change in Finance and Operations apps results in writes to the Common Data Service and vice versa. This automated data flow provides an integrated user experience across the apps.

![Data relationship between apps](media/dual-write-overview-picture1.png)

![Aspects of dual-write](media/dual-write-aspects.PNG)

The dual-write infrastructure is extensible and reliable, and includes the following key features: 

+ Synchronous and bi-directional data flow between applications.
+ Synchronization with play, pause, and catchup modes supports the system during online and offline/async modes. 
+ Ability to synchronize initial data between the applications.
+ Consolidated view of activity and error logs for data administrators.
+ Ability to configure custom alerts and thresholds, and subscribe to notifications.
+ Intuitive user-interface for filtering and transformations.
+ Ability to set and view entity dependencies and relationships.
+ Extensible for both standard and custom entities and maps.
+ Reliable application lifecycle management.
+ Out-of-the-box setup experience for new customers.
 
Dual-write application orchestration harmonizes the concepts between Finance and Operations applications and model-driven apps in Dynamics 365. This integration supports these scenarios:

+ Integrated customer master.
+ Access to customer loyalty cards and reward points.
+ Unified product mastering experience.
+ Awareness of organization hierarchy.
+ Integrated vendor master.
+ Access to finance and tax reference data.
+ Experience price engine on-demand.
+ Integrated prospect to cash experience. 
+ Ability to serve both in-house and customer assets through field agents.
+ Integrated procure-to-pay experience.
+ Integrated activities and notes for customer data and documents.
+ Lookup on-hand inventory availability and details.
+ Project to cash experience.
+ Ability to handle multiple addresses and roles through the party concept.
+ Single source management for users.
+ Integrated channels for retailing and marketing.
+ Visibility to promotions and discounts.
+ Request for service functions.
+ Streamline service operations.
 
## Top reasons to use dual-write

Dual-write provides data integration across Microsoft Dynamics 365 applications. This robust framework links environments together and enables different business applications to work together. Here are the top reasons why you should use dual-write: 

+ Dual-write provides tightly-coupled, near-real-time, and bi-directional integration between Finance and Operations apps and model-driven applications in Dynamics 365. This integration makes Microsoft Dynamics 365 the one-stop-shop for all your business solutions. Customers using Dynamics 365 Finance and Dynamics 365 Supply Chain Management, but using non-Microsoft solutions for customer relationship management are moving towards Dynamics 365 for its dual-write support. 
+ Data from customers, products, operations, projects, and IoT flows automatically to Common Data Service through dual-write. This connection is a boon to businesses that are interested in Power Platform expansions.
+ Dual-write infrastructure follows our no-code/low-code principle. You can extend the standard table-to-table maps and include custom maps with minimal engineering effort.
+ Dual-write supports both online and offline modes. Microsoft is the only company offering support for online and offline modes.

## What does dual-write mean for users and architects of customer relationship management products? 

Dual-write automates the data flow between Finance and Operations apps and Common Data Service. In future releases, concepts in model-driven apps in Dynamics 365 like customer, contact, quotation, and order will scale to mid- and upper-mid market customers. 

In the first release, most of the automation is handled by dual-write solutions. In future releases, these solutions will become part of the Common Data Service. Understanding the upcoming changes to the Common Data Service will save you effort in the long run. Some of the crucial revisions are: 
+ Common Data Service will have new concepts like company and party. These concepts will impact all applications built on Common Data Service, including Sales, Marketing, Customer Service, and Field Service. 
+ Activities and notes are unified and expanded to support both C1s (users of the system) and C2s (customers of the system). 
+ Upcoming changes in the Common Data Service include:
    - The decimal data type will replace the money data type.
    - Date effectivity will support past, present, and future data in the same place.
    - There will be more support for currency and exchange rates, including a revision of the **Exchange Rate** API.
    - Unit conversions will be supported.

For more information on upcoming changes, see [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/extensibility/extensibility-roadmap).
