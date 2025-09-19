---
title: Generate EFT payment file with JBA format
description: Learn how to generate an EFT file with the JBA file format for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/25/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym
ms.custom: 
  - bap-template
---

# Generate EFT payment file with JBA format

[!include [banner](../../includes/banner.md)]

This article explains how to generate an EFT file with the Japanese Bankers Association (JBA) file format for Japan in Microsoft Dynamics 365 Finance.

In Japan, the Japanese Bankers Association (JBA) file format is commonly used for electronic funds transfer (EFT) among banks. 

The following procedure uses the JPMF demo company data.

To generate an EFT file with the JBA file format, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, enter "VendPay".
1. Select **Lines**.
1. In the **Account** field, enter "JPMF-000001".
1. In the **Debit** field, enter a number.
1. Copy the value in the **Offset account** field to use later.
1. Select **Save**.
1. Select **Generate payments**.
1. In the **Method of payment** field, select a method of payment that is enabled for the JBA file format..
1. In the **File name** field, enter a file name for the generated file.
1. In the **Bank account** field, enter the **Offset account** field value you copied previously. 
1. Select **OK**. Toggle the slider if you want to print the payment control report.  
1. Select **OK**.
    - A .zip file is generated and you're prompted to download the file.  
    - The payment status changes to **Sent**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
