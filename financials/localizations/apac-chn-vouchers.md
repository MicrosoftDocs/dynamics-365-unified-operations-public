---
# required metadata

title: Chinese vouchers
description: This topic describes Chinese vouchers and how they are used in Microsoft Dynamics 365 for Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerVoucherType_CN, VoucherTypeWizard_CN
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261454
ms.assetid: b5a50142-b48c-4b1b-8828-6c436ea91238
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Chinese vouchers

[!include[banner](../includes/banner.md)]


This topic describes Chinese vouchers and how they are used in Microsoft Dynamics 365 for Operations.

You must create a voucher document for every posted journal. You can print a paper voucher and a posted journal. Based on your requirements, you can use the Voucher type setup wizard to set up the **Get**, **Pay** and **Transfer** voucher types that are often used, or you can create new voucher types on the **Voucher type setup** page. You can use booking vouchers to enter and group transactions into the Receipt voucher, Payment voucher, or Transfer voucher. 

A continuous number sequence that begins from the first day of every monthly period should be assigned to each voucher type. You can define a Chinese voucher type for ledger accounts only. You can assign the voucher types to specific ledger accounts. Then, on the **Voucher type setup** page, you can define validation rules for posting voucher transactions to the specified ledger accounts. During voucher posting, validation is run, based on the rules that are specified on the **Voucher type setup** page. You receive a message if the voucher type that is selected for the selected ledger account is incorrect. 

For example, you select a ledger account of the **Credit** type for the **Get** voucher type. However, the validation rule that you defined for the **Get** voucher type specifies that the ledger account must be a debit account. In this case, you receive a message that states that the Chinese voucher type isn't valid. You can then make the appropriate changes and post the voucher again. 

## Voucher creation methods
You can create voucher transactions on the **General journal** page by using the **Simple** or **Advanced** method. If you create journal vouchers of a single voucher type by using the **Simple** method, the voucher type that is selected on all the journal lines should be the same. The **Advanced** method lets you create multiple journal lines of different voucher types. 

## Check for continuity in voucher numbers
The Chinese voucher number should be sequential, and there should be no gaps in the fiscal period. You can run a batch process to determine whether there are gaps in the Chinese voucher numbers. The batch process verifies the transaction dates and then renumbers the vouchers for continuity. For tracking purposes, you can generate the **Chinese voucher continuity check** report. This report shows the history of renumbered Chinese vouchers. 

## Printing a Chinese voucher
You can print a Chinese voucher either before or after you post the voucher. The printed voucher shows information such as the history of renumbered Chinese vouchers, and tax information before or after the voucher was posted. You can review the printed information to verify that the information is the same before and after posting, and that the information is correct. For example, if you select sales tax in a journal voucher, the final voucher information includes the sales tax. However, the sales tax might differ from the sales tax that was part of the journal. The printed result must be accurate, and it must be the same as the result that is generated after the final posting. Therefore, you can print a Chinese voucher that has the correct information from both the journal voucher and the voucher transactions. You can also print Chinese vouchers in a batch after you filter the information by Chinese voucher type and fiscal period.




