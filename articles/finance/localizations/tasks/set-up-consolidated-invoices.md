--- 
# required metadata 
 
title: Set up consolidated invoices
description: In Japan, consolidated invoices can be enabled to fit the Japanese business practices. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustParameters, PaymDay, PaymTerm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up consolidated invoices

[!include [banner](../../includes/banner.md)]

In Japan, consolidated invoices can be enabled to fit the Japanese business practices.



This procedure walks you through setting up consolidated invoice functionality.



This procedure was created using the demo data company JPMF.


## Configure Accounts receivable parameters for consolidated invoices
1. Go to Accounts receivable > Setup > Accounts receivable parameters.
2. Expand the Customer section.
    * Enable Consolidated invoice for customers  
3. Click the Number sequences tab.
    * Specify the number sequence to use for the Consolidation ID.  

## Configure Payment days
1. Go to Accounts receivable > Payments setup > Payment days.
    * Configure a Payment day  

## Configure Terms of payment
1. Go to Accounts receivable > Payments setup > Terms of payment.
2. Use the Quick Filter to find records. For example, filter on the Terms of payment field with a value of 'COD'.
3. Click Edit.
    * Select Cutoff day as the Payment Method  
    * The Cutoff day is not available at R1 release. You can choose Current month as an alternative. This may result in slight difference, which needs to adjusted manually.  
4. In the Payment day field, type a value.

