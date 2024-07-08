--- 
title: Free text invoice optimization
description: This article explains how to optimize free text invoices in Dynamics 365 finance. 
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

This article describes how to speed up the performance of free text invoices page in Dynamics 365 Finance. Starting in Dynamics 365 Finance version 10.0.41, the performance of free text invoices can be optimized.

## Performance challenges of free text invoices
An increase in the volume of data leads to the free text invoice page loading slowly in Dynamics 365 Finance. 

To address these performance challenges, two changes have been introduced in Dynamics 365 Finance version 10.0.41:
1. The **All free text invoices** page displays invoices with a **Not posted** status. This reduces the initial data load and improve loading times.
2. A new **Optimized invoice loading** page is available that provides an enhanced performance, faster data loading, and more efficient workflow processing.

### Optimized invoice loading feature

The **Optimize invoice loading** feature highlights include:
 - Enhanced free text invoice page - Improved performance and usability of the Free text invoice in Dynamics 365 Finance.
 - Faster data loading - Addresses the slow loading of the free text invoice due to increased volume of data.
 - Optimized workflow - When the workflow is enabled, performance is enhanced.
 - **Not posted** invoices - When **All free text invoices** is selected, the page automatically displays invoices with a**Not posted** status.
 - **Optimized invoice loading page** -  A new **Optimised invoice loading page** provides users with a streamlined interface for free text invoices.

This feature enhancement improves the performance and usability of the free text invoice, addressing challenges by the growing volume of data and ensuring a more efficient workflow experience for users. 


