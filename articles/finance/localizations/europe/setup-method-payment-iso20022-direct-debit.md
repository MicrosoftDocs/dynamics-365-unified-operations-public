--- 
title: Set up method of payment for ISO20022 direct debit
description: Learn how to set up the customer method of payment for ISO20022 direct debit or any other payment type using electronic reporting in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/04/2025
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustPaymMode
---

# Set up method of payment for ISO20022 direct debit

[!include [banner](../../includes/banner.md)]

This article explains how to set up the customer method of payment for ISO20022 direct debit or any other payment type using electronic reporting in Microsoft Dynamics 365 Finance.

Before you complete the following procedure, you must first set up export format configurations and payment accounts.

The procedure was created using the demo data company DEMF.

To set up the customer method of payment for ISO20022 direct debit, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments setup \> Methods of payment**.
1. Use the Quick Filter to find records. For example, filter on the **Method of payment field** with a value of "ELECTRONIC".
1. Select **Edit**.
1. In the **Payment account** field, enter the value "DEMF OPER".
1. Expand the **File formats** section.
1. In the **Generic electronic reporting** field, select **Yes**.
1. In the **Export format configuration** field, enter or select **ISO20022 Direct debit (DE)**. If the list is empty, the customer payment export format configuration hasn't been imported and activated.  
1. In the **Require mandate** field, select **Yes** for customer payment formats that require including mandate information in the payment message, like SEPA direct debit.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
