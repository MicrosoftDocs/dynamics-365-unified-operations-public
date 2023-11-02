---
title: Set up consolidated invoices
description: In Japan, consolidated invoices can be enabled to fit the Japanese business practices.
author: kfend
ms.date: 08/01/2023
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: CustParameters, PaymDay, PaymTerm
---
# Set up consolidated invoices

[!include [banner](../../includes/banner.md)]

In Japan, consolidated invoices can be enabled to fit the Japanese business practices. This article walks you through setting up consolidated invoice functionality.

## Configure Accounts receivable parameters for consolidated invoices
1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2. Expand the **Customer** section and enable the consolidated invoice for customers.
3. On the **Number sequences** tab, specify the number sequence to use for the **Consolidation ID**.  

## Configure Payment days
1. Go to **Accounts receivable** > **Payments setup** > **Payment days**.
2. Select **New** to configure a Payment day.  

## Configure Terms of payment
1. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**.
2. Use the **Quick Filter** to find records. For example, filter on the Terms of payment field with a value of **COD**.
3. Select **Edit**.
4. In the **Payment method** field, select **Cutoff day**.
5. In the **Payment day** field, enter a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
