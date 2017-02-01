---
# required metadata

title: Delays | Microsoft Docs
description: This article provides information about delayed dates in master planning. A delayed date is a realistic due date that a transaction receives if the earliest fulfillment date that master planning calculates is later than the requested date.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 09:17:45
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: ReqTransFuturesListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 19311
ms.assetid: 6d38b248-83c4-4e60-a0a6-aef5d29365c7
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Delays

This article provides information about delayed dates in master planning. A delayed date is a realistic due date that a transaction receives if the earliest fulfillment date that master planning calculates is later than the requested date.

Master planning can calculate the earliest fulfillment date for a transaction, based on lead times, material availability, capacity availability, and various planning parameters. If master planning calculates an order date that precedes the current date, the order can't be fulfilled on time. Therefore, the order is delayed. In this case, master planning forward-plans the order from the current date and includes lead times. These lead times start with any lower-level component items. The order then receives a delayed date. A delayed date is a realistic due date, based on the current data. Master planning also calculates the number of delay days. In some situations, you might choose not to calculate delays, such as when users know that they can expedite lead times by selecting alternative modes of delivery. You can configure how delays are calculated for a coverage group. You can then attach the coverage group to an item later. On the **Master planning parameters** page, you can set the start time for the calculation of delays. If an order is fulfilled after this time, a delay of one day is added to the delay date of the order. **Note:** In earlier versions, calculated delays were known as *futures messages*, the delayed date was known as the *futures date*, and a delayed transaction was referred to as *a transaction that was future set*.

See also
--------

[Coverage settings](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/coverage-settings)

