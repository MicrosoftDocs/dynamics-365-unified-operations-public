---
title: Set up consolidated invoices
description: Learn how to set up consolidated invoices for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustParameters, PaymDay, PaymTerm
ms.custom: 
  - bap-template
---

# Set up consolidated invoices

[!include [banner](../../includes/banner.md)]

This article explains how to set up consolidated invoices for Japan in Microsoft Dynamics 365 Finance.

In Japan, consolidated invoices can be enabled to fit the Japanese business practices. The following procedures walk you through how to set up consolidated invoice functionality.

## Configure accounts receivable parameters for consolidated invoices

To configure accounts receivable parameters for consolidated invoices, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Expand the **Customer** section and enable the consolidated invoice for customers.
1. On the **Number sequences** tab, specify the number sequence to use for the **Consolidation ID**.  

## Configure payment days

To configure payment days, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments setup \> Payment days**.
1. Select **New** to create and configure a payment day.  

## Configure terms of payment

To configure terms of payment, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments setup \> Terms of payment**.
1. Use the **Quick Filter** to find records. For example, filter on the **Terms of payment** field with a value of "COD".
1. Select **Edit**.
1. In the **Payment method** field, select **Cutoff day**.
1. In the **Payment day** field, enter a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
