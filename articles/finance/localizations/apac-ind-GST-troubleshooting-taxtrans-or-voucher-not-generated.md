---
# required metadata

title: TaxTrans or voucher isn't generated
description: This topic provides troubleshooting information to help resolve this issue when TaxTrans or voucher isn't generated.
author: shaoling
manager: beya
ms.date: 04/30/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# TaxTrans or voucher isn't generated

[!include [banner](../includes/banner.md)]

Complete the steps in this topic if after posting tax, when you check the voucher and posted sales tax there are records missing.

## Check if the subledger journal transferred. 

1. Go to **General ledger** > **Periodic tasks** > **Subledger journal entries not yet transferred**.
2. Transfer any record in the list, and then check the voucher and posted sales tax again.

## Check tax configuration

To check the tax configuration, see [Open the designer for the current tax configuration](apac-ind-GST-troubleshooting-open-designer-current-used-tax-configuration.md).  

1. Check the posting profile of expected measure. Select the posting type in **Debit/Credit** column, and then select **Edit**. 
2. Check the value of tax accounting provider.

    ![Tax accounting provider value](./media/taxtrans-voucher-notgenerated-Picture3.png)

  The following is the rule for posting tax transactions and voucher decided by tax accounting provider. Correct the configuration if it's not working as expected.

- | **Tax accounting provider** | **Posting tax transaction** | **Posting voucher** |
  | --------------------------- | --------------------------- | ------------------- |
  | Tax                         | Yes                         | Yes                 |
  | Ledger                      | No                          | Yes                 |
  | Other                       | No                          | No                  |

## Check the formula

1. Select **Condition** to open the formula. 
2. Check the condition, and correct the tax configuration if it's not working as expected.

  ![Condition field](./media/taxtrans-voucher-notgenerated-Picture4.png)

  ![Formula](./media/taxtrans-voucher-notgenerated-Picture5.png)

## Check the posting code logic
Set a breakpoint in **TaxAccountingPostFacade::post()**, and debug for the logic of generating tax transaction and voucher. 

  ![Breakpoint](./media/taxtrans-voucher-notgenerated-Picture6.png)

## Determine whether customization exists

If you've completed the steps in the previous section but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
