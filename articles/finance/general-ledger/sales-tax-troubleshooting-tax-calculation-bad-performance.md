---
# required metadata

title: Tax Calculation performance impacts the transaction
description: This topic provides troubleshooting information related to Tax Calculation performance and the impact on transactions.
author: shtao
manager: beya
ms.date: 04/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# Tax Calculation performance impacts the transaction

[!include [banner](../includes/banner.md)]

There are times when a transaction is impacted by Tax Calculation performance issues. For example, TaxCalculation::calculateTax(), TaxUncommitted::deleteForDocumentLine().

Complete the steps in the following sections as needed, to troubleshoot the issue.

## Check transaction line count
Check whether the transaction has a large number of lines, for example more than several hundred. If the transaction does have several hundred lines, choosing to delay the tax calculation. For more information, see [Enable delayed tax calculation on journals](enable-delayed-tax-calculation.md). If the transaction doesn't have that many lines, move to the next section. 

  1. Import transactions from large files.
  2. Multiple sessions process the same transaction tax calculation at the same time.
  3. The transaction has multiple lines, and there are views refresh in real-time, for example, the 'Calculated sales tax amount' in General journal form, the 'Calculated sales tax amount' refresh in real-time when line's fields changed.

     [![Calculated sales tax amount field on the Jounal voucher page](./media/tax-calculation-bad-performance-impacts-transaction-Picture1.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture1.png)

## Check call stack to see whether tax calculation is called multiple times. If yes, try to reduce tax calculation times according to the below steps; otherwise, go to step 3.**

- 1. If the doc [Enable delayed tax calculation on journals](enable-delayed-tax-calculation.md) has considered the transaction, please refer it to delay tax calculation; otherwise, go to the next step in development level.
  2. If it is a purchase order and the customer's application version is higher than 10.0.15, enable flighting PurchTableChangeMgmtDistributionUpdateOnToggle_KillSwitch can delay tax calculation until the final calculation.

## Check the call stack timeline 
Check the call stack timeline to confirm whether the issues below exist. If they do, enable the flighting, **TaxUncommittedDoIsolateScopeFlighting** to resolve the issue.

- The transaction leads in the system hang until the session ends and the transaction can't calculate the tax result.

     [![Direct taxes (tab)](./media/tax-calculation-bad-performance-impacts-transaction-Picture2.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture2.png)

- The **TaxUncommitted** methods cost significantly more time than other methods. For example, **TaxUncommitted::updateTaxUncommitted()** costs 43347.42 seconds, but other methods cost 0.09 seconds.

     [![Direct taxes (tab)](./media/tax-calculation-bad-performance-impacts-transaction-Picture3.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture3.png)

## Customizing and calling Tax Calcuation
When you are customizing, don't call tax calculation at the insert() or update() for each line. Tax calculation should be called at the transaction level.

## Verify customization
If you have completed the steps in the previous sections and no issue is found, check whether customization exists. If it doesn't, create a Microsoft service request for further support.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
