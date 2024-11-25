---
title: Prepayments management
description: Learn about paying value-added tax (VAT) when prepayments are received from customers, including an outline on processing prepayments from customers.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Prepayments management
[!include [banner](../../includes/banner.md)]

Sellers are legally required to pay value-added tax (VAT) from the prepayments that they receive from customers (buyers). They must then issue prepayment factures to the customers. Customers can then deduct the VAT, based on the prepayment facture that they receive from a seller.

![A screenshot of a cell phone description automatically generated.](../media/1%20Scheme%20english.jpg)


## Processing prepayments from customers
When sellers issue a facture for prepayment to a customer, they also pay the indicated VAT amount. When sellers issue a facture for goods, they also pay the indicated VAT amount and can then deduct the VAT amount from the prepayment facture.

The following table shows the general ledger (GL) transactions and user operations for VAT accounting in a prepayment scenario.

| GL transaction                         | GL transaction                        | User operation                                                                                  | Source of information                                                                                                                                      |
|----------------------------------------|---------------------------------------|--------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| D 51 [Bank]                            | C 62 [Debts]/Advances                 | Registration of a prepayment from a customer                                                           | **Customer payment journal** page                                                                                                     |
| D 76 [Other debts and liabilities]/VAT | C 68 [Taxes]/VAT                      | Facture registration                                                                                   | **Facture create** page (**Accounts receivable \> Periodic tasks \> Facture creation for prepayment**)                                |
| D 62 [Debts] D 90 [Sales]/VAT          | C 90 [Sales]/Revenue C 68 [Taxes]/VAT | Shipment of goods: Revenue Shipment of goods: Outgoing VAT                                             | Sales order and facture registration                                                                                                  |
| D 62 [Debts]/Advance D 68 [Taxes]/VAT  | D 62 [Debts] C 76 [Other]/VAT         | Settlement of the prepayment with the facture for shipment Reversal of VAT from the prepayment facture | Prepayment and invoice settlement                                                                                                     |
| None                                   | None                                  | Prepayment facture registration in the purchase book for VAT deduction                                 | **Purchase book (Incoming VAT processing)** page (**Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Incoming VAT processing**) |

The functionality for processing prepayments from customers lets you perform the following actions:

-   Set up separate ledger accounts to post prepayments.
-   Calculate VAT amount on prepayments.
-   Print factures for prepayments.
-   Include factures that were issued for prepayments in the sales book.
-   Automatically create a transaction for the reversal VAT amount from prepayments for settled payments and invoices, and include factures for prepayments in the purchase book.

## Setup
### Set up a posting profile for prepayments

To create a posting profile for prepayments, follow the procedure that is described in the article, [Customer posting profiles](../../accounts-receivable/customer-posting-profiles.md).

> [!NOTE]
> To satisfy the requirements of the Russian legislation, the following settings should be used:
>
> - The **Summary account** field should typically be set to ledger account **62 [Debts]**, subaccount **Advances received**.
> - The **Sales tax prepayments** field should typically be set to ledger account **76 [Taxes]**, subaccount **VAT**.

### Set up a sales tax payable ledger account

1.  Go to **Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**.
2.  Select a separate ledger posting group for advances that are received.
3.  In the **Sales tax payable** field, select the ledger account for sales taxpayable.

> [!NOTE]
> According to the requirements of the Russian legislation, this ledger account should typically be ledger account **68 [Taxes]**, subaccount **VAT**.

For more information about how to create ledger posting groups, see [Set up Ledger posting groups for sales
tax](../../general-ledger/tasks/set-up-ledger-posting-groups-sales-tax.md).

### Set up a number sequence for the facture
After a prepayment is registered, a facture is automatically created. The facture number is generated based on the number sequence that is set up in the General ledger parameters.

1.  Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2.  On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence code for the **Prepayment facture** reference.

> [!NOTE]
> Select the same number sequence for the **Prepayment facture** and **Facture** references. In this way, you help guarantee that you're following the legal requirement for sequential numbering of all factures.

### Set up Accounts receivable parameters for prepayments

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Ledger and sales tax** tab, on the **Payment** FastTab, set the following fields:

    - Set the **Sales tax on prepayment journal voucher** option to **Yes** to specify that sales tax must be calculated when the prepayment is posted. (This option is a standard field.)
    - In the **Posting profile with prepayment journal voucher** field, specify the posting profile for the prepayment. (This field is a standard field.)
    - Set the **Reverse on invoice date** option to **Yes** to post VAT on prepayment transaction cancellations during settlement of the prepayment and invoice on the invoice date.
    - In the **VAT transaction type** field, select the type of transaction to use
    for VAT on prepayment transaction cancellations during settlement:

        - **Reverse** – Post VAT transaction cancellations as reverses
        - **Reversing entry** – Post VAT transaction cancellations as "red" storno transactions.

    - In the **Tax group for prepayment** field, select the sales tax group for the prepayment.
    - In the **Item sales tax group** field, select the item sales tax group for the prepayment.
    - In the **Prepayment handling** field, select **Simple**.
    - Set the **Automatically facture creation** option to **Yes** to automatically create a facture when prepayments are posted.

> [!NOTE]
> If you set the **Automatically facture creation** option to **No**, the factures on prepayments are created in postponed mode. The setting of this parameter is inherited and can be changed in the following places:
>
> - On the **Payments** tab of the **Customer payments** page. (To open this page, go to **Accounts receivable \> Payments \> Customer payment journal**, and then, on the **Customer payment journal** page, on the Action Pane, select **Lines**.)
>
> - In the **Convert to prepayment** dialog box. (To open this dialog box, go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Sales books journal**, and then, on the **Sales book journal** page, on the Action Pane, select **Functions \> Transform to prepayment**. Then, on the **Unsettled payments** page, on the Action Pane, select **Prepayment handling**.)
>
> - Set the **Inherit invoice dimensions** option to **Yes** to copy financial dimensions from the invoice to the payment when the payment proposal is used.

3. Close the page.

## Operations

### Register a prepayment from a customer and print the facture

1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**.
2. Select **New** to create a payment journal, and then, in the **Name** field, select the payment name.
3. On the Action Pane, select **Lines** to create a payment journal line, and then, on the **List** tab, enter the required details.
4. On the **General** tab, in the **Account** section, in the **Agreement ID** field, specify the code for the agreement that the prepayment was received for.
5. On the **Payment** tab, in the **Document** section, in the **Document** and **Document date** fields, specify the number and date of the payment document.
6. Make sure that the **Prepayment journal voucher** option is set to **Yes**.

> [!NOTE]
> When the **Prepayment journal voucher** option is set to **Yes**, the **Sales tax group** and **Item sales tax group** fields on the **General** tab, and the **Posting profile** field on the **Payment** tab, are automatically set, based on the setup of your system.

7. Make sure that the **Automatically facture creation** option is set to **Yes**, so that a facture is automatically created when prepayments are posted.

> [!NOTE]
> If you set the **Automatically facture creation** option to **No**, the factures on prepayments are created in postponed mode.

8. On the Action Pane, select **Post** \> **Post** to post the prepayment.
9. Go to **Accounts receivable \> Inquiries and reports \> Facture** to review the payment facture that is generated.
10. In the lower part of the **Facture journal** page, on the **General** tab, in the **Note** field, enter the list of goods that the prepayment is registered for.
11. Select **Fill line details**, and then, in the **Journal of invoices for payment** dialog box, select the **Mark** check box for every invoices for payment for which the names of goods (works and services) should be included in the description of the prepayment facture. For more information, see [Invoices for payment](rus-invoice-payment.md)

![Journal of invoices for payment dialog box.](../media/2%20Journal%20of%20invoices%20for%20payment.png)

12.  Select **OK**. The names of goods are added to the **Note** field.
13.  Select the line for the facture, and then, on the Action Pane, select **Print**.

### Transform a customer payment to a customer prepayment

If unsettled payment documents (that is, part of the payment amount) remain at the end of reporting period, the payment documents (or part of the documents) must be converted to prepayments and included in the sales book.

1. Post a customer payment in standard way.
2. Go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Sales books journal**.
3. On the Action Pane, select **Functions** \> **Transform to prepayment** to open the **Unsettled payments** page.
4. Select the **Mark** check box for the payment line that you want to convert to a prepayment, and then, on the Action Pane, select **Prepayment handling** to open the **Convert to prepayment** dialog box.
5. In the **Date** field, select the transaction date.

> [!NOTE]
>If you must create a prepayment on the transaction date of the main payment, you can set the **Same date** field to **Yes**. Prepayment transactions and factures will then be generated on the transaction date.

6. Set the **Automatically facture creation** option to **Yes** so that a facture is automatically created on the prepayment.

> [!NOTE]
> If you set the **Automatically facture creation** option to **No**, you should create the factures on prepayments in postponed mode.

7. Select **OK** to transform the customer payment to a customer prepayment.

> [!NOTE]
> When you select **OK**, the payment transactions are reversed, and prepayment transactions are created. The prepayment transactions are dated according to the settings in the **Convert to prepayment** dialog box. Prepayment factures are created and included in the sales book after it's updated.

You can also convert a payment to a prepayment by using the **Customer transactions** page. Go to **Accounts receivable** \> **Customers** \> **All customers**. On the Action Pane, on the **Customer** tab, in the **Transactions** group, select **Transactions** to open the **Customer transactions** page. Select a payment transaction, and then, on the Action Pane, select **Prepayment handling** \> **Post** to convert it to a prepayment.

Additionally, you can transform a prepayment back to a payment. In this case, the previously created prepayment facture will be deleted.

### Create factures at the end of a reporting period

At the end of the reporting period, you can view prepayments and create factures for any prepayments that factures weren't automatically created for at the posting stage.

1. Go to **Accounts receivable** \> **Periodic tasks** \> **Facture creation for prepayment**. The **Facture create** page shows the prepayments that factures weren't automatically created for.
2. Select the **Mark** check box for every prepayment that you want to create a facture for. (Alternatively, use the **Mark All** button on the Action Pane to select all the prepayments on the page.) Then, on the Action Pane, select **Create facture**.
3. In the **Facture create** dialog box, in the **Date of the registration** field, select the date of the facture registration.

> [!NOTE]
> The date that you select must be a date in the sales book period.

### Settle a customer prepayment with a facture for shipment

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. On the Action Pane, on the **Collect** tab, in the **Settle** group, select **Facture and payment settlement** to open the **Facture and payment settlement** page. This page lets you filter invoices by facture number.
3. Select the **Mark** check box for every transaction that you want to settle, and then, on the Action Pane, select **Update**. The invoice that is a source for the facture and payment is settled.

When the transactions are settled, the following events occur:

-  The payment amount from the **Advances received** subaccount is transferred to the **Debtor debts** subaccount.
-  The VAT amount that accrued from the prepayment is reversed.
-  The reversed prepayment is included on the **Incoming VAT processing** page when incoming VAT is processed.
-  After incoming VAT is processed and the purchase book lines are updated, a reverse entry for the customer advance payment appears in the purchase book.

## Processing prepayments to suppliers

Customers can take the indicated VAT for deduction when they receive a facture for prepayment from a seller. When customers receive a facture for goods from a seller, they take the indicated VAT for deduction. At the same time, they are required to recover VAT from the prepayment facture that was previously deducted.

The following table shows the GL transactions and user operations for VAT accounting.

| GL transaction                             | Gl transaction                                         | User operation                                      | Source of infomration                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|--------------------------------------------|--------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| D 60 [Liabilities]/Advances                | К 51 [Bank]                                            | Prepayment is sent to the supplier.                        | **Vendor payment journal** page                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                                            |                                                        | Prepayment facture registration                            | **Create prepayment facture** page (**Accounts payable** \> **Periodic tasks** \> **Facture** \> **Facture creation for prepayment**)                                                                                                                                                                                                                                                                                                                                       |
| D 68 [Taxes]/VAT                           | К 76 [Other debts and liabilities]/VAT from Prepayment | VAT is deducted from the prepayment facture.               | **Purchase book (Incoming VAT processing)** page (**Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Incoming VAT processing**) The general ledger account for the **debit** posting is taken from the **Payment offset account** field, and the general ledger account for the **credit** posting is taken from the **Incoming tax payment** field of the posting group for the sales tax code (**Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**). |
| D 41 [Goods] D 19 [VAT from purchase]      | К 60 [Liabilities] К 60 [Liabilities]                  | Purchase: Goods cost Purchase: Reflection of incoming VAT  | Purchase order and facture registration                                                                                                                                                                                                                                                                                                                                                                                                                         |
| D 60 [Liabilities]                         | К 60 [Liabilities]/Advances                            | Facture and prepayment settlement                          | Prepayment and invoice settlement                                                                                                                                                                                                                                                                                                                                                                                                                               |
| D 68 [Taxes]/VAT                           | К 19 [VAT from purchase]                               | Deduction of VAT from received goods                       | **Purchase book (Incoming VAT processing)** page (**Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Incoming VAT processing**)                                                                                                                                                                                                                                                                                                                           |
| D 76 [Other debts and liabilities]/VAT Pr. | К 68 [Taxes]/VAT                                       | Recovery of VAT accepted for deduction from the prepayment | **Sales book (Outgoing VAT processing)** page (**Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Outgoing VAT processing**)                                                                                                                                                                                                                                                                                                                              |

> [!NOTE]
> To post VAT on prepayments to a dedicated ledger account, such as 76/VAT, from a prepayment, we recommend that you set up a separate sales tax code for prepayments on the **Sales tax codes** page (**Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**) and a separate posting group on the **Ledger posting groups** page (**Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**).


### Set up a posting profile for prepayments

To create a posting profile for prepayments, follow the procedure that is described in [Vendor posting profiles](../../accounts-payable/vendor-posting-profiles.md).

> [!NOTE]
> To satisfy the requirements of the Russian legislation, the following settings should be used:
>
>  - The **Summary account** field should typically be set to ledger account **60 [Liabilities]**, subaccount **Advances paid**.
>  - The **Sales tax prepayments** field should typically be set to ledger account **68 [Taxes]**, subaccount **VAT**.

### Set up an incoming tax payment ledger account

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**.
2. Select a separate ledger posting group for advances that are paid.
3. In the **Incoming tax payment** field, select the ledger account for incoming tax payments.

> [!NOTE]
> According to the requirements of the Russian legislation, this ledger account should typically be ledger account **76 [Other debts and liabilities]**, subaccount **VAT from prepayment**.

### Set up Accounts payable parameters for prepayments

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Ledger and sales tax** tab, on the **Payment** FastTab, set the following fields:

    - Set the **Sales tax on prepayment in payment journal** option to **No** to prevent taxes from being posted before the incoming facture is registered.
    - In the **Posting profile for payment journal with prepayment** field, specify the posting profile for the payment. 
    - Set the **Reverse on the invoice date** option to **Yes** to post a VAT reverse transaction on the invoice date.
    - In the **VAT transaction type** field, select the type of transaction to use for VAT on prepayment transaction cancellations during settlement:

        - **Reverse** – Post VAT transaction cancellations as reverses.
        - **Reversing entry** – Post VAT transaction cancellations as "red" storno transactions.

    - In the **Tax group for prepayment** field, select the sales tax group for the prepayment.
    - In the **Item sales tax group** field, select the item sales tax group for the prepayment.
    - In the **Prepayment handling** field, select **Simple**.
    - Set the **Create facture on nonposted payments** option to **Yes** to register a facture for unposted prepayments.

3. On the **Purchase book** FastTab, in the **Facture issue period** field, enter the number of days to exclude factures that are issued by a supplier. The exclusion must be later than the statutory deadline.

> [!NOTE]
> This option is valid only for prepayment factures. If you enter **0** (zero), factures are reflected on the **Purchase book (Incoming VAT processing)** page independently of the facture date.

4. Close the page.

### Set up a number sequence for incoming VAT processing

1.  Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2.  On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence code for the **VAT processing voucher** reference.

### Register a supplier's facture for a prepayment

1. Go to **Accounts payable** \> **Payments** \> **Vendor payment journal**, and create a journal.
2. On the Action Pane, select **Lines**, and then, on the **List** tab, on the payment journal line, set the **Date**, **Account**, **Description**, **Debit**, **Offset account type**, **Offset account**, and **Currency** fields.
3. On the **General** tab, in the **Account** section, in the **Agreement ID** field, specify the code of the agreement that the prepayment was received for.
4. On the **Payment** tab, in the **Document** section, in the **Document** and **Document date** fields, specify the number and date of the payment document.
5. Make sure that the **Prepayment journal voucher** option is set to **Yes**.

> [!NOTE]
> When the **Prepayment journal voucher** is set to **Yes**, the **Sales tax group** and **Item sales tax group** fields on the **General** tab, and the **Posting profile** field on the **Payment** tab, are automatically set, based on the setup of your system.

> [!IMPORTANT]
> To prevent sales tax from being posted before incoming prepayment factures are processed, you must set the **Sales tax on prepayment in payment journal** option to **No** on the **Accounts payable parameters** page, and you must also select the ledger account for incoming tax payments in the **Incoming tax payment** field on the **Ledger posting groups** page.

6. Post the journal that has a prepayment to the supplier.
7. Go to **Accounts payable \> Periodic tasks \> Facture \> Facture creation for prepayment**.
8. On the Action Pane, select **Select** to open the **Select prepayments** dialog box. You can use this dialog box to find the required payment by, for example, the supplier's code and the payment order details. The **Create prepayment facture** page shows prepayments to suppliers that factures haven't yet been created for. You can register a facture for an unposted prepayment.

9. Select **OK** to add the lines for processing. Then, on the **General** tab, in the **Facture** section, in the **Facture** field, enter the number of received factures.
10. In the **Date of the registration** field, enter the facture date of the registration.
11. If the registration date differs from the document date, set the **Facture date** field.
12. Set the **Sales tax group** and **Item sales tax group** fields.

> [!NOTE]
>
> - The calculated tax will be recorded on the line for the generated facture. Select the **Marked** check box for each line for the facture, and then, on the Action Pane, select **Create**.
>   
> - If dates or facture numbers aren't set, you receive a warning message.

The generated facture will be reflected on the **Facture journal** page, where the **Facture source** field will be set to the **Prepayment journal voucher** type.

### Process incoming VAT on the received facture for the prepayment

After you register a prepayment facture, the VAT amount from the prepayment facture can be processed for deduction.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Incoming VAT processing**.
2. On the Action Pane, select **Select** to find the required facture.

> [!NOTE]
> The prepayment facture has a value of **Prepayment** in the **Operation** field.

3. Mark the facture, and post the operation. After posting, there are a tax transaction and a general ledger transaction for the VAT amount:

    - **Debit 68 [Tax] / VAT – Credit 76 [Other debts and liabilities] / VAT from prepayment – on VAT amount**

> [!NOTE]
> After the input VAT is processed, you can't delete the prepayment facture. To cancel the processing of incoming VAT, use the **Purchase book (Canceling processed VAT)** page (**Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Canceling processed VAT**).

4. Go to **Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **VAT processing log** to view the processed prepayment facture.
5. Go to **Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Purchase books journal** to create and update the purchase book for the reporting period. To view the processed facture in the purchase book, select **Lines** on the Action Pane.

### Recover previously accepted deductible VAT on prepayment

When a facture for the purchase of goods is received from a seller, the customer deducts the specified VAT on the purchase facture. In that same tax period, the facture must recover the VAT in the budget that was deducted from the received prepayment.

Additional actions are required after the incoming facture for goods, work, and services is posted. For example, if a seller makes a delivery, the incoming invoice and the incoming facture for this delivery are updated, and the invoice and the previously registered prepayment are settled.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Purchase book** \> **Incoming VAT processing**.
2. On the Action Pane, select **Select** to find the required payment, and then select **OK** to add lines for processing.
3. Mark the facture, and post the operation.
4. To restore previously deducted VAT from the received prepayment facture, you must configure the parameters for VAT recovery. Go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Parameters of VAT process**, and create a line.
5. In the **VAT operation code** field, enter the operation code for VAT processing.
6. In the **Operation type** field, enter **VAT restoration**.
7. In the **Restoration type** field, select **Prepayment journal voucher**.
8. Set the **By default** option to **Yes** to indicate that this transaction is the default transaction for VAT processing.
9. Set the **Include in book** option to **Yes** if factures that are processed by using this transaction code should be included in the sales book.
10. To process the outgoing VAT, go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Outgoing VAT processing**.

For settled payments where the incoming VAT was previously processed, the factures have a transaction type of **Prepayment's storno**. The facture number corresponds to the number of the registered prepayment facture. The amount of VAT to recover equals the amount of the processed incoming VAT on the received goods that falls in the settled part of the invoice.

11. Mark the facture, and post the operation. The system creates a tax transaction and a general ledger transaction for the processed tax amount.

> [!NOTE]
> The VAT recovery general ledger transaction is a reversal of the VAT deduction general ledger transaction:
>
>  **Debit 76 [Other debts and liabilities] / VAT on prepayment – Credit 68 [Taxes] / VAT – on VAT amount**

12. Go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **VAT processing log** to view the processed facture.
13. Go to **Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Sales books journal**. Update the sales book, and verify that the facture is reflected in the Sales books journal for the processed amount.

By default, if there were several VAT restorations for the same prepayment facture in the same period, the prepayment facture will be reflected on several line in the Sales books journal. Use the **Group by factures** option when you print the sales book. In that way, the facture report will reflect one line that has the total value of the VAT that was recovered in the period.

You can't close the Sales books journal if there are any incoming prepayment factures in the period that VAT hasn't been restored for.

You can't cancel the prepayment settlement and the invoice if the VAT was restored in the period. You must first cancel the VAT recovery in this period.
To cancel the VAT recovery, use the **Sales book (Canceling processed VAT)** page (**Accounts receivable** \> **Periodic tasks** \> **Sales book** \> **Canceling processed VAT**).

You can't cancel the processing of incoming VAT unless the VAT recovery is canceled on the prepayment that is settled to the invoice.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
