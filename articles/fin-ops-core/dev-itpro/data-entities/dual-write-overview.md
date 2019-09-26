---
# required metadata

title: Near-real-time data integration between Finance and Operations and Common Data Service
description: This topic provides an overview of the integration between Finance and Operations and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/15/2019
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
ms.search.validFrom: 2019-07-15

---

# Near-real-time data integration with Common Data Service

[!include [banner](../includes/banner.md)]

[!include [preview](../includes/preview-banner.md)]

In the current digital world, business ecosystems use Microsoft Dynamics 365 applications as a whole. Because data from people, customers, operations, and Internet of Things (IoT) devices flows into one source, there is an opportunity for digital feedback loops. To achieve this experience, integration between Finance and Operations apps and other Dynamics 365 applications is essential. Some applications are built on top of Common Data Service. Integration between Finance and Operations apps data with Common Data Service lets other applications communicate coherently and fluently with Finance and Operations.

Finance and Operations apps and Common Data Service provide near-real-time data synchronization between Finance and Operations apps and other Dynamics 365 applications via a dual-write framework. The coverage is broad and spans 28 surface areas of the application. The goal is to provide a "One Dynamics 365" user experience through seamless data flows that connect business processes across applications.

![Architecture overview diagram](media/dual-write-overview.jpg)

The following value propositions are available for customers:

+ [Organization hierarchy in Common Data Service](dual-write-organization.md)
+ [Company concept in Common Data Service](dual-write-company.md)
+ [Integrated customer master](dual-write-customer.md)
+ [Integrated vendor master](dual-write-vendor.md)
+ Unified product master

## System requirements

Synchronous, bidirectional, near-real-time data flows require the following versions:

+ Microsoft Dynamics 365 for Finance and Operations version 10.0.4 (July 2019) with Platform update 28, or later
+ Microsoft Dynamics 365 for Customer Engagement, Platform version 9.1 (4.2) or later

## Setup instructions

Follow these steps to set up integration between Finance and Operations apps and Common Data Service.
	
1. For the setup of the dual-write system, see the [step-by-step guide](https://aka.ms/dualwrite-docs) on Announcing Dual Write Preview.
2. Download and install the solution from the [Finance and Operations, Common Data Service, and Customer Engagement Integration](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=66052096) Yammer group. The package contains five solutions:

    + Dynamics365Company
    + CurrencyExchangeRates
    + Dynamics365FinanceAndOperationsCommon
    + Dynamics365FinanceCommon
    + Dynamics365SupplyChainCommon

3. Follow the execution order for [synchronizing initial reference data](dual-write-initial.md).
4. If you encounter dual-write synchronization issues, see the [Troubleshooting guide for data integration](dual-write-troubleshooting.md).

> [!IMPORTANT]
> You can’t run dual-write and [Prospect to cash](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/accounts-template-mapping-direct) side-by-side. If you're running the Prospect to cash solution, you must uninstall it. You must also disable the customer and vendor dual-write templates that are part of the Prospect to cash solution.
