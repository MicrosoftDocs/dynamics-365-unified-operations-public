---
# required metadata

title: Tax posted to wrong ledger account in voucher
description: This topic provides troubleshooting information that can help when tax is posted to the wrong ledger account in voucher. 
author: qire
manager: beya
ms.date: 04/12/2021
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


# Tax posted to wrong ledger account in voucher

[!include [banner](../includes/banner.md)]

During posting, tax may be posted to wrong ledger account in voucher. To troubleshoot this issue, follow the steps in the following sections as required. The examples in this topic use a sales order as the business document.

## Find the tax code of the incorrectly posted tax transaction

1. On the **Voucher transactions** page, select the transaction you want to work with and then select **Posted sales tax** to find the tax code.

     [![Voucher transactions page, Posted sales tax button](./media/tax-posted-to-wrong-ledger-account-Picture1.png)](./media/tax-posted-to-wrong-ledger-account-Picture1.png)

In this example, the tax code is, **VAT 19**.

   [![Sales tax code field](./media/tax-posted-to-wrong-ledger-account-Picture2.png)](./media/tax-posted-to-wrong-ledger-account-Picture2.png)

## Check the ledger posting group of the tax code

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Find the specific tax code, and find the ledger posting group. In this example, it's **VAT**.

     [![Sales tax codes page, Ledger posting group field](./media/tax-posted-to-wrong-ledger-account-Picture3.png)](./media/tax-posted-to-wrong-ledger-account-Picture3.png)

3. To view the detail configuration, select **VAT**, or right click **Ledger posting group** > **View details**.

     [![View details](./media/tax-posted-to-wrong-ledger-account-Picture4.png)](./media/tax-posted-to-wrong-ledger-account-Picture4.png)

4. Verify that the account number in the **Sales tax payable** field is correct according to the transaction type. In this case, the sales tax of the sales order should be posted to sales tax payable account, 222200. If this isn't the expected account, select the correct account to post to.

     [![Sales tax payable field](./media/tax-posted-to-wrong-ledger-account-Picture5.png)](./media/tax-posted-to-wrong-ledger-account-Picture5.png)

     The following table provides details for each field.
     |   Field                 | Description                                                  |
     | ----------------------- | ------------------------------------------------------------ |
     | Sales tax payable       | The main account for outgoing sales taxes that are payable to the tax authority.  |
     | Sales tax receivable   | The main account for incoming taxes that are  received from the tax authority.  |
     | Use tax expense         | The ain account for posting deductible use taxes that aren't claimed or reported to the tax authority by vendors as part of EU reverse charge GST/HST. **Use tax** must be selected for the sales tax code in the sales tax group that's used in the transaction. This field isn't available if **Apply sales tax taxation rules** is selected on the **General ledger parameters** page.) |
     | Use tax payable         | The main account for posting incoming use taxes that are payable to tax authorities. |
     | Settlement account      | The main account that the net balance of the ledger accounts specified in the **Use tax payable** and **Sales tax receivable** fields will be posted. |
     | Vendor cash discount   | The main account to post a cash discount for sales tax codes that are associated with this ledger posting  group. |
     | Customer case discount | The main account to a post cash discount for sales tax codes that are associated with this ledger posting  group. |

     For more information, see, [Set up Ledger posting groups for sales tax](tasks/set-up-ledger-posting-groups-sales-tax.md)

## Debug in code to check ledger dimensions 

In the code, the posting account is determined by the ledger dimension. The ledger dimension saves the record ID of an account in the databse. You can query the account by the ledger dimension using the following SQL query:

     ```sql
     select * from DIMENSIONATTRIBUTEVALUECOMBINATION where Recid={the value of _ledgerDimension}
     ```

1. For a sales order, add a breakpoint at the *Tax::saveAndPost()* and *Tax::post()* methods. Pay attention to the value of *_ledgerDimension*.

     [![Sales order code sample with breakpoint](./media/tax-posted-to-wrong-ledger-account-Picture6.png)](./media/tax-posted-to-wrong-ledger-account-Picture6.png)

2. For a purchase order, add a breakpoint at the *TaxPost::saveAndPost()* and *TaxPost::postToTaxTrans()* methods. Track the value of *_ledgerDimension*.

     [![Purchase order code sample with breakpoint](./media/tax-posted-to-wrong-ledger-account-Picture7.png)](./media/tax-posted-to-wrong-ledger-account-Picture7.png)

3. Query in the database to find the display value of this account by the record ID of *_ledgerDimension*.

     ```sql
     select * from DIMENSIONATTRIBUTEVALUECOMBINATION where recid={the value of _ledgerDimension}
     ```

     [![Display value of record ID](./media/tax-posted-to-wrong-ledger-account-Picture8.png)](./media/tax-posted-to-wrong-ledger-account-Picture8.png)

4. Examine the callstack to find where the *_ledgerDimension* is assigned. Usually, it's from **TmpTaxWorkTrans**. In this case, add a breakpoint at *TmpTaxWorkTrans::insert()* and *TmpTaxWorkTrans::update()* to find where it is assigned.

## Determine whether customization exists
If you've completed the steps in the previous sections but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
