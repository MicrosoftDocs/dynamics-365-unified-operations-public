---
title: Configure consolidated invoice parameters and setup for accounts payable
description: Learn how to set up and configure consolidated invoices, including a step-by-step process and an outline on configuring terms of service.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 08/29/2018
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendParameters, PaymDay, PaymTerm
ms.dyn365.ops.version: Version 7.0.0
---

# Configure consolidated invoice parameters and setup for accounts payable

[!include [banner](../../includes/banner.md)]

In Japan, consolidated invoices can be enabled to fit the Japanese business practices.



This procedure walks you through setting up consolidated invoice functionality.



This procedure was created using the demo data company JPMF.


## Configure Accounts payable parameters for consolidated invoices
1. Go to Accounts payable > Setup > Accounts payable parameters.
2. Expand the Vendor section.
3. Check the Consolidated invoice for vendor check box.
4. Click the Number sequences tab.
    * Specify the number sequence to use for the Consolidation ID.  

## Configure Payment days
1. Go to Accounts payable > Payment setup > Payment days.
    * Configure a Payment day  

## Configure Terms of payment
1. Go to Accounts payable > Payment setup > Terms of payment.
2. Use the Quick Filter to find records. For example, filter on the Terms of payment field with a value of 'COD'.
3. Click Edit.
    * Select Cutoff day as the Payment Method  
    * The Cutoff day is not available at R1 release. You can choose Current month as an alternative. This may result in slight difference, which needs to adjusted manually.   
4. In the Payment day field, type a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
