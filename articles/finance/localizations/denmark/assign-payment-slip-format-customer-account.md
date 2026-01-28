--- 
title: Assign a payment slip format to a customer account
description: This article describes how to set up the payment slip attachment format for customers in Denmark with Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable
ms.custom: 
  - bap-template
---

# Assign a payment slip format to a customer account

[!include [banner](../../includes/banner.md)]

This article describes how to set up the payment slip attachment format for customers in Denmark with Microsoft Dynamics 365 Finance. This functionality is available for legal entities whose primary address is in Denmark.

The following procedure walks you through how to set up the payment slip attachment format for a selected customer. The procedure was created using the demo data company DEMF. 

To assign a payment slip format to a customer account, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the list, mark the selected row.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Invoice and delivery** section.
1. Select **Edit**.
1. In the **On a customer invoice** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.     
1. In the **On a free text invoice** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.    
1. In the **On an interest note** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.    
1. In the **On a collection letter** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.   
1. In the **On a project invoice** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.     
1. In the **On an account statement** field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.    
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
