---
# required metadata

title: Tax Calculation bad performance heavily impacts the transaction
description:
author: shtao
manager: beya
ms.date: 02/04/2021
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



# Tax Calculation bad performance heavily impacts the transaction

[!include [banner](../includes/banner.md)]

## **Symptom**

- The transaction operation meets bad performance and the most consumer point is tax calculation, e.g. TaxCalculation::calculateTax(), TaxUncommitted::deleteForDocumentLine().

 

## **Trouble shooting guide**

- **Step 1: Check whether the transaction with a large number of lines (e.g., more than hundreds of lines) in the below scenarios. If yes, delay the tax calculation ([reference](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/enable-delayed-tax-calculation)) can resolve this issue; otherwise, check step 2.**

  1. Import transactions from large files.

  2. Multiple session process the same transaction tax calculation at the same time.

  3. The transaction has multiple lines, and there are views refresh in real-time, e.g., the 'Calculated sales tax amount' in General journal form, the 'Calculated sales tax amount' refresh in real-time when line's fields changed.

     [![Direct taxes (tab)](./media/tax-calculation-bad-performance-impacts-transaction-Picture1.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture1.png)

- **Step 2: Check call stack to see whether tax calculation is called multiple times. If yes, try to reduce tax calculation times according to the below steps; otherwise, go to step 3.**

- 1. If the doc [Enable delayed tax calculation on journals](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/enable-delayed-tax-calculation) has considered the transaction, please refer it to delay tax calculation; otherwise, go to the next step in development level.
  2. If it is a purchase order and the customer's application version is higher than 10.0.15, enable flighting PurchTableChangeMgmtDistributionUpdateOnToggle_KillSwitch can delay tax calculation until the final calculation.

- **Step 3: Check call stack timeline to confirm the below issue. If yes, enabled flighting TaxUncommittedDoIsolateScopeFlighting to mitigate the issue.**

- 1. The transaction leads in the system hang until the session ended, and the transaction can't calculate the tax result anymore.

     [![Direct taxes (tab)](./media/tax-calculation-bad-performance-impacts-transaction-Picture2.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture2.png)

  2. TaxUncommitted's methods cost too much time than other methods, e.g., TaxUncommitted::updateTaxUncommitted() cost 43347.42 seconds, but other methods just cost 0.09 second.

     [![Direct taxes (tab)](./media/tax-calculation-bad-performance-impacts-transaction-Picture3.png)](./media/tax-calculation-bad-performance-impacts-transaction-Picture3.png)

- **Step 4: When customization, don't call tax calculation at each line's insert() or update(). Tax calculation should be called at the transaction level.**

- **Step 5: If no issue is found in above steps, check whether customization exists. If not, create a service request to Microsoft for further support5**



[!INCLUDE[footer-include](../../includes/footer-banner.md)]