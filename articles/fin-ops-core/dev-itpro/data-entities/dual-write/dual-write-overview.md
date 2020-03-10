---
# required metadata

title: Dual-write overview
description: This topic provides an overview dual-write. Dual-write is an infrastructure that provides near-real-time interaction between Microsoft Dynamics 365 model-driven apps and Finance and Operations apps.
author: RamaKrishnamoorthy
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

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between model-driven apps in Microsoft Dynamics 365 and Finance and Operations apps. When data about customers, products, people, and operations flows beyond application boundaries, all departments in an organization are empowered.

Dual-write provides tightly coupled, bidirectional integration between Finance and Operations apps and Common Data Service. Any data change in Finance and Operations apps causes writes to Common Data Service, and any data change in Common Data Service causes writes to Finance and Operations apps. This automated data flow provides an integrated user experience across the apps.

![Data relationship between apps](media/dual-write-overview.jpg)

Dual-write has two aspects: an *infrastructure* aspect and an *application* aspect.

### Infrastructure

The dual-write infrastructure is extensible and reliable, and includes the following key features:

+ Synchronous and bidirectional data flow between applications
+ Synchronization, together with play, pause, and catchup modes to support the system during online and offline/asynchronous modes.
+ Ability to sync initial data between the applications
+ Consolidated view of activity and error logs for data admins
+ Ability to configure custom alerts and thresholds, and to subscribe to notifications
+ Intuitive user interface (UI) for filtering and transformations
+ Ability to set and view entity dependencies and relationships
+ Extensibility for both standard and custom entities and maps
+ Reliable application lifecycle management
+ Out-of-box setup experience for new customers

### Application

Dual-write creates a mapping between concepts in Finance and Operations apps and concepts in model-driven apps in Dynamics 365. This integration supports the following scenarios:

+ Integrated customer master
+ Access to customer loyalty cards and reward points
+ Unified product mastering experience
+ Awareness of organization hierarchy
+ Integrated vendor master
+ Access to finance and tax reference data
+ On-demand price engine experience
+ Integrated prospect-to-cash experience
+ Ability to serve both in-house assets and customer assets through field agents
+ Integrated procure-to-pay experience
+ Integrated activities and notes for customer data and documents
+ Ability to look up on-hand inventory availability and details
+ Project-to-cash experience
+ Ability to handle multiple addresses and roles through the party concept
+ Single source management for users
+ Integrated channels for retailing and marketing
+ Visibility into promotions and discounts
+ Request-for-service functions
+ Streamlined service operations

## Top reasons to use dual-write

Dual-write provides data integration across Microsoft Dynamics 365 applications. This robust framework links environments and enables different business applications to work together. Here are the top reasons why you should use dual-write:

+ Dual-write provides tightly coupled, near-real-time, and bidirectional integration between Finance and Operations apps and model-driven apps in Dynamics 365. This integration makes Microsoft Dynamics 365 the one-stop shop for all your business solutions. Customers who use Dynamics 365 Finance and Dynamics 365 Supply Chain Management, but who use non-Microsoft solutions for customer relationship management (CRM), are moving toward Dynamics 365 for its dual-write support.
+ Data from customers, products, operations, projects, and the Internet of Things (IoT) automatically flows to Common Data Service through dual-write. This connection is very useful for businesses that are interested in Microsoft Power Platform expansions.
+ The dual-write infrastructure follows the no-code/low-code principle. Minimal engineering effort is required to extend the standard table-to-table maps and to include custom maps.
+ Dual-write supports both online mode and offline mode. Microsoft is the only company that offers support for online and offline modes.

## What does dual-write mean for users and architects of CRM products?

Dual-write automates the data flow between Finance and Operations apps and Common Data Service. In future releases, concepts in model-driven apps in Dynamics 365 (for example, customer, contact, quotation, and order) will be scaled to mid-market and upper-mid-market customers.

In the first release, most of the automation is handled by dual-write solutions. In future releases, those solutions will become part of Common Data Service. By understanding the upcoming changes to Common Data Service, you can save yourself effort in the long term. Here are some of the crucial changes:

+ Common Data Service will have new concepts, such as company and party. These concepts will affect all apps that are built on Common Data Service, such as Dynamics 365 Sales, Dynamics 365 Marketing, Dynamics 365 Customer Service, and Dynamics 365 Field Service.
+ Activities and notes are unified and expanded to support both C1s (users of the system) and C2s (customers of the system).
+ Here are some of the upcoming changes in Common Data Service:

    - The decimal data type will replace the money data type.
    - Date effectivity will support past, present, and future data in the same place.
    - There will be more support for currency and exchange rates, and the **Exchange Rate** application programming interface (API) will be revised.
    - Unit conversions will be supported.

For more information about upcoming changes, see [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-common-data-service-phase-1).
