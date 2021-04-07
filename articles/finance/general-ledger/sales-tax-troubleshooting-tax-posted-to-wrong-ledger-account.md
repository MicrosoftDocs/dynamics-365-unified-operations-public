---
# required metadata

title: Tax is posted to wrong ledger account in voucher
description:
author: qire
manager: beya
ms.date: 04/01/2021
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
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---



# Tax is posted to wrong ledger account in voucher

[!include [banner](../includes/banner.md)]

## Symptom

- Tax is posted to wrong ledger account in voucher.

## Trouble shooting guide

**Here take sales order as an example.**

- **Step 1: Find the tax code of wrongly posted tax transaction**

- 1. Click posted sales tax button to find the tax code:

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture1.png)](./media/tax-posted-to-wrong-ledger-account-Picture1.png)

  2. In this case, that tax code is VAT19:

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture2.png)](./media/tax-posted-to-wrong-ledger-account-Picture2.png)

- **Step 2: please check the ledger posting group of the tax code**

- 1. Go to *Tax -> Indirect taxes -> Sales tax -> Sales tax codes*

  2. Find the specific tax code     and check Ledger posting group. In this example it is "VAT".

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture3.png)](./media/tax-posted-to-wrong-ledger-account-Picture3.png)

  3. To check out the detail configuration, click the "VAT" or right click on the title *Ledger posting group* and click *View details.*

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture4.png)](./media/tax-posted-to-wrong-ledger-account-Picture4.png)

  4. Check the account number filled according to the transaction type. In this case, the sales tax of sales order should be posted to sales tax payable account 222200. If this is not the expected account, please fill in the right account to post to.(the other account is used for, list)

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture5.png)](./media/tax-posted-to-wrong-ledger-account-Picture5.png)

     Details for each field:

     | Sales tax payable       | Main account for  outgoing sales taxes that are payable to the tax authority. Used for Sales  order, Free text invoice and etc. |
     | ----------------------- | ------------------------------------------------------------ |
     | Sales tax  receivable   | Main account for incoming taxes that are  received from the tax authority. Used for vendor transactions like Purchase  order. |
     | Use tax expense         | Main account for  posting deductible Use taxes that are not claimed or reported to the tax  authority by vendors as part of EU reverse charge GST/HST.  (The Use tax  option must be selected for the Sales tax code in the Sales tax group that is  used in the transaction. This field won't be available if the Apply sales tax  taxation rules option is selected on the General ledger parameters page.) |
     | Use tax payable         | Main account for  posting incoming Use taxes that are payable to tax authorities. |
     | Settlement account      | Main account that  the net balance of the ledger accounts specified in the Use tax payable and  Sales tax receivable fields will be posted. |
     | Vendor cash  discount   | main account to  post cash discount for Sales tax codes associated with this Ledger posting  group. |
     | Customer case  discount | main account to  post cash discount for Sales tax codes associated with this Ledger posting  group |

     Please find more detail at: https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/set-up-ledger-posting-groups-sales-tax

- **Step 3: If no issue is found in above steps, debug in code and check whether the     issue is related to ledger dimension.**

  - In code, the account to post to is determined by the ledger dimension. The ledger dimension saved a record ID of an account in databse. We can query the account out by the ledger dimension by below SQL query:

    select * from DIMENSIONATTRIBUTEVALUECOMBINATION where Recid={the value of _ledgerDimension}

  1. For sales order, add breakpoint at Tax::saveAndPost() and Tax::post() methods, and pay     attention to the value of _ledgerDimension.

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture6.png)](./media/tax-posted-to-wrong-ledger-account-Picture6.png)

  2. For purchase order, add breakpoint at TaxPost::saveAndPost() and TaxPost::postToTaxTrans() methods. Similarly, track the value of _ledgerDimension.

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture7.png)](./media/tax-posted-to-wrong-ledger-account-Picture7.png)

  3. Query in Database to find the display value of this account by the record ID of _ledgerDimension:

     ```sql
     select * from DIMENSIONATTRIBUTEVALUECOMBINATION where recid={the value of _ledgerDimension}
     ```

     [![Direct taxes (tab)](./media/tax-posted-to-wrong-ledger-account-Picture8.png)](./media/tax-posted-to-wrong-ledger-account-Picture8.png)

  4. Examine the callstack to find where the _ledgerDimension is assigned. Usually, it's from TmpTaxWorkTrans. In this case add a breakpoint at TmpTaxWorkTrans::insert() and TmpTaxWorkTrans::update() to find where it is assigned.

- **Step 4: If no issue is found in above steps, check whether customization exists. If not, create a service request to Microsoft for further support.**



[!INCLUDE[footer-include](../../includes/footer-banner.md)]