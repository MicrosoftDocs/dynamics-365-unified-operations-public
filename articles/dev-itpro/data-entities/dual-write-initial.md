---
# required metadata

title: Execution order for initial sychronization of Finance and Operations and Common Data Service
description: This topic specifies the order of synchronization you must follow to create the initial data.
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

# Execution order for initial sychronization of Finance and Operations and Common Data Service

Before you use data integration, you must create the initial data required for customers, vendors and contacts. For example, if you want to create a new **Vendor group** item and set its **Terms of Payment** as **Net30**, then before you attempt to create the **Vendor group** item you need to make sure that **Net30** exists in both Finance and Operations and Common Data Service. (In the future, we will release a  dual-write platform functionality called **Initial Sync**. It will do a one-time data synchronization between Finance and Operations and Common Data Service as part of the dual-write setup.)

Tips: We are releasing a dual-write map for all reference data including **Terms of Payment** (Payment Terms). If you already have the initial data in one system, a small update operation on a record can trigger dual-write on that record. 

You must follow the following order of precedence and make sure that the initial data is available on both Finance and Operations and Common Data Service.   

## Vendor

The order of execution for Vendor is:

```
Vendor Group
    Terms of payment
        Payment day & lines
        Payment schedule
Vendor payment method
```

## Customer (Organization)

The order of execution for Customer is:

```
Customer Group
    Terms of payment
        Payment day & lines
        Payment 
Customer payment method
```

## Contact (Person)

The order of execution for Contact is:

```
Customer
Vendor               
```
