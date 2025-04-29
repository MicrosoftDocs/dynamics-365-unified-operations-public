---
title: Configure consolidated invoice parameters and setup for accounts payable
description: Learn how to set up and configure consolidated invoices for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendParameters, PaymDay, PaymTerm
ms.custom: 
  - bap-template
---

# Configure consolidated invoice parameters and setup for accounts payable

[!include [banner](../../includes/banner.md)]

This article explains how to set up and configure consolidated invoices for Japan in Microsoft Dynamics 365 Finance.

In Japan, consolidated invoices can be enabled to fit the Japanese business practices.

The following procedures walk you through how to set up and configure consolidated invoice functionality. The procedures ere created using the demo data company JPMF.

## Configure accounts payable parameters for consolidated invoices

To configure accounts payable parameters for consolidated invoices, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Setup \> Accounts payable parameters**.
1. Expand the **Vendor** section.
1. Select the **Consolidated invoice for vendor** checkbox.
1. Select the **Number sequences** tab.
1. Specify the number sequence to use for the consolidation ID.  

## Configure payment days

To configure payment days, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Payment days**.
1. Configure a payment day.  

## Configure terms of payment

To configure terms of payment, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Terms of payment**.
1. Use the Quick Filter to find records. For example, filter on the **Terms of payment** field with a value of "COD".
1. Select **Edit**.
1. For the **Payment Method**, select **Cutoff day**. You can choose **Current month** as an alternative. This may result in slight difference, which needs to adjusted manually.   
1. In the **Payment day** field, enter a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
