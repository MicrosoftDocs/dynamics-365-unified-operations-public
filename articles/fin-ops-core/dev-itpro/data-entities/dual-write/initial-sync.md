---
# required metadata

title: Execution order for initial synchronization of Finance and Operations apps and Common Data Service
description: This topic specifies the order of synchronization that you must follow to create the initial data.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/25/2019
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

# Execution order for initial synchronization of Finance and Operations apps and Common Data Service

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

Before you use data integration, you must create the initial data that is required for customers, vendors, and contacts. For example, you want to create a new **Vendor group** item and set its **Terms of Payment** value to **Net30**. In this case, before you try to create the **Vendor group** item, you must make sure that **Net30** exists in both the application and Common Data Service. (In the future, Microsoft will release dual-write platform functionality that is named Initial Sync. This functionality will do a one-time data synchronization between the application and Common Data Service as part of the dual-write setup.)

> [!TIP]
> Microsoft is releasing a dual-write map for all reference data, including **Terms of Payment** (payment terms). If you already have the initial data in one system, a small update operation on a record can trigger dual-write on that record.

You must follow the following order of precedence and make sure that the initial data is available in the application and Common Data Service.

## Vendor

Here is the order of execution for the **Vendor** entity:

1. Vendor group

    1. Terms of payment

        1. Payment day and lines
        2. Payment schedule

2. Vendor payment method

## Customer (Organization)

Here is the order of execution for the **Customer** entity:

1. Customer group

    1. Terms of payment

        1. Payment day and lines
        2. Payment 

2. Customer payment method

## Contact (Person)

Here is the order of execution for the **Contact** entity:

1. Customer
2. Vendor
