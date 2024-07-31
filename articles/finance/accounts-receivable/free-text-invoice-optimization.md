--- 
title: Free text invoice optimization
description: This article explains how to optimize free text invoices in Microsoft Dynamics 365 Finance.
author: prabhatb-ship-it
ms.author: prabhatb
ms.topic: how-to
ms.date: 07/08/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustPaymMode, BankAccountTableLookUp
ms.dyn365.ops.version: Version 7.0.0 
---

# Free text invoice optimization

[!include [banner](../../includes/banner.md)]

As of Microsoft Dynamics 365 Finance version 10.0.41, the performance of free text invoices can be optimized. This article describes changes that can help speed up the performance of the free text invoice page in Dynamics 365 Finance.

## Performance challenges of free text invoices

An increase in the volume of data causes the free text invoice page to be loaded slowly in Finance.

To address this performance challenge, two changes are introduced in Finance version 10.0.41:

- The **All free text invoices** page automatically shows invoices that have a **Not posted** status. This change reduces the initial data load and improves load times.
- A new **Optimized invoice loading** page provides enhanced performance, faster data loading, and more efficient workflow processing.

## Optimize invoice loading feature

Here are some highlights of the **Optimize invoice loading** feature:

- **Enhanced free text invoice page** – The feature improves the performance and usability of the free text invoice page in Finance.
- **Faster data loading** – The feature addresses the slow loading of free text invoices that is caused by increased data volume.
- **Optimized workflow** – When the workflow is enabled, performance is enhanced.
- **"Not posted" invoices** – When **All free text invoices** is selected, the page automatically shows invoices that have a **Not posted** status.
- **Optimized invoice loading page** – A new **Optimized invoice loading** page gives users a streamlined interface for free text invoices.

This feature enhancement improves the performance and usability of the free text invoice page, addresses the challenges that increased data volume causes, and ensures a more efficient workflow experience for users.
