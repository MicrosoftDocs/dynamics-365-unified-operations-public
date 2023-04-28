--- 
# required metadata 
 
title: Create accrual schemes
description: This article explains how to create an accrual scheme. 
author: aprilolson
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerAccrualTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create accrual schemes

[!include [banner](../../includes/banner.md)]

This article explains how to create an accrual scheme. This task uses the USMF demo company.

1. Go to **General ledger > Journal setup > Accrual schemes**.
2. Select **New**.
3. In the **Accrual identification** field, type a value.
4. In the **Description of accrual scheme** field, type a value.
5. In the **Debit** field, specify the desired values. The main account defined will replace the debit main account on the journal voucher line and it will also be used for the reversal of the deferral based on the ledger accrual transactions.  
6. In the **Credit** field, specify the desired values. The main account defined will replace the credit main account on the journal voucher line and it will also be used for the reversal of the deferral based on the ledger accrual transactions.  
7. In the **Voucher** field, select how you want the voucher determined when the transactions are posted.
8. In the **Description** field, type a value to describe the transactions that will be posted.
9. In the **Period frequency** field, select how often the transactions should occur.
10. In the **Number of occurrences by period** field, enter a number.
11. In the **Post transactions** field, select when the transactions should be posted, such as **Monthly**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
