---
title: Value-added tax (VAT) for tax agents (Russia)
description: Learn how to set up VAT and perform transactions for tax agent for Russia, including outlines and processes on setting up tax agent transactions.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.search.form: TaxAuthority, VATOperationCodeTable_RU
ms.dyn365.ops.version: 8.1
---

# Value-added tax (VAT) for tax agents (Russia)

[!include [banner](../../includes/banner.md)]

When a company is acknowledged as a tax agent, it must correctly accrue and deduct value-added tax (VAT) from funds that are paid to taxpayers, or it must accrue VAT at the expense of its own funds. It must then transfer VAT to the tax authority.

This functionality is required in order to generate invoices, factures, and payments to vendors that the company is defined as a tax agent (fiscal agent) for.

The following functions are supported:

- Create vendors that your company operates as a tax agent for.
- Mark sales tax codes for tax agent transactions to specify whether the VAT payments must be made from the vendor's funds or at the expense of your company's own funds.
- Create payment proposals for vendor invoices.
- Create payments for tax authorities.
- Post and settle payments to the vendor.
- Create and print factures for the VAT amount that is to be remitted to tax authorities, and register the factures in the sales book 
- Register factures for VAT deduction in the purchase book.

## Set up tax agent transactions

Before you can create tax agent transactions, you must set up the parameters for them in the **Tax** module.

### Set up the VAT operation code for the tax declaration

1. Select **Tax** \> **Setup** \> **Sales tax** \> **VAT operation codes**.
2. In the **VAT operation code** field, enter the operation code for the VAT declaration.
3. In the **Description** field, enter a description for the transaction code.
4. Close the page.

### Set up the sales tax code for tax agent transactions

1. Select **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
2. Create a tax code.
3. In the **Sales tax code** field, enter a code for sales tax.
4. In the **Settlement period** field, select the period that the tax is calculated and paid to the tax authority for.
5. In the **Ledger posting group** field, select the ledger posting group for the sales tax code.
6. In the **Type of tax** field, select either **Standard VAT** or **Reduced VAT**.
7. In the **VAT charge** field, select the source of VAT accrual:

    - **From vendor funds** − The VAT payment is made from the vendor's income.
    - **From own funds** − The VAT payment is made from the tax agent's funds.

8. Select **Values** to open the **Values** page.
9. In the **Value** field, enter the VAT percentage.
10. Close the page.
11. Select **Indirect taxes** \> **Sales tax** \> **Sales tax groups**.
12. Create a sales tax group, and enter the required information.
13. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code that you created in steps 1 through 10.

    > [!NOTE]
    > If you selected the **From own funds** option for the sales tax code in step 7, the **Exempt** option is selected by default on the **Setup** tab.

14. Close the page.
15. Select **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.
16. Create an item sales tax group, and enter the required information. 
17. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code that you created in steps 1 through 10.
18. Close the page.

### Set up a vendor tax authority

1. Select **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
2. Create a tax authority, and enter the required information.
3. In the **Vendor account** field, select the vendor that operates as the tax authority.
4. Close the page.

## Create a vendor that your company acts as a tax agent for, and post transactions

On the **Vendors** page, you can define a vendor as a tax agent. You can then perform transactions with this vendor.

1. Select **Accounts payable** \> **Vendors** \> **All vendors**.
2. Create a vendor that your company acts as a tax agent for, and enter the required information.
3. On the **General** tab, set the **Tax agent** option to **Yes** to define the vendor as a tax agent.
4. In the **Vendor type** field, select the type of vendor:

    - **Blank** – The vendor is a common vendor.
    - **Non resident** – The vendor is a foreigner.
    - **State authority** – The vendor is a governmental or municipal authority.

5. In the **VAT operation code** field, select the operation code for the VAT declaration.
6. Close the page.
7. Select **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
8. Create a purchase order for the vendor, and enter the required information.
9. Select **Header** to open the Header view, and then, on the **Setup** tab, in the **VAT operation code** field, view or modify the code for the VAT declaration.
10. In the **VAT charge** field, select the source of VAT accrual: **From vendor funds** or **From own funds**.
11. Confirm the purchase order, and post the invoice.

## Create tax payments

In the Vendor payment journal, two options for paying VAT as a tax agent are implemented:

- Payment for a specific invoice
- Prepayment (invoice is unknown)

### Create a payment proposal for a tax agent invoice

On the **Vendor payment proposal** page, you can create payment proposals that you can use to generate payments to a vendor tax agent. You can also generate VAT payments to a tax authority.

1. Select **Accounts payable** \> **Payments** \> **Payment journal**.
2. Create a journal, and then select **Lines** to open the **Vendor payments** page.
3. Select **Payment proposal** \> **Create payment proposal** to open the **Vendor payment proposal** page.
4. In the **Select invoices by** field, select the type of payment proposal to create. You can create the proposal by due date, by cash discount date, or by both due date and cash discount date.
5. Select **Records to include**, and then select **Filter** to define the criteria for the payment proposal. For example, you can use the vendor account as a criterion.
6. Select **OK** to open the **Vendor payment proposal** page. In the upper pane, you can view the open invoice transactions that contribute to the payment proposal line. On the **VAT Proposal** tab, you can view the details of the tax transaction for the VAT payment to the tax authorities.
7. Select **Create payments** to transfer the proposal lines to the payment journal.

    The **Vendor payments** page shows two payment lines for each invoice. One line is for a payment to a vendor, and the other line is for a tax payment to a tax authority. On the second journal line, the **Purpose text** field shows the purpose of the VAT payment. The vendor account number and address are included.

    > [!NOTE]
    > For the line that is a tax payment to a tax authority, the **Sales tax code** field on the **General** tab shows the sales tax code. The **Vendor account** field on the **Payment** tab shows the vendor account that the tax is paid for.

8. In the **VAT operation code** field, view or modify the operation code for the VAT declaration.
9. Select **Generate payments** to open the **Generate payments** page.
10. Select either the payment method or the export format, depending on the method of payment on the journal line. Then select the bank account to draw the payment from, and enter the required information. 
11. Select **OK**.
12. Select **Print** \> **Payment order** to print the payment order report.
13. On the **Journal voucher** page, select **Validate** \> **Validate** to validate the journal line. Then select **Post** \> **Post** to post the journal lines.

    > [!NOTE]
    > After payments to the vendor are completed, you can view the settled transactions on the **Transactions on settlement** page. You can view the posted sales tax transactions on the **Sales tax transactions** page.

### Create a prepayment

1. Select **Accounts payable** \> **Payments** \> **Payment journal**.
2. Create a journal, and then select **Lines** to open the **Vendor payments** page.
3. Create a new journal line, select the vendor, and enter a prepayment amount.
4. Specify the sales tax group and item sales tax group that contain the sales tax code that has the required setup of the VAT charge.

    > [!NOTE]
    > - The VAT amount that must be paid is calculated based on the value of the sales tax code.
    > - To prevent tax from being calculated on the prepayment itself, on the **Accounts payable parameters** page, on the **Ledger and sales tax** tab, set the **Sales tax on prepayment in payment journal** option to **No**.

5. Select **Payment proposal** \> **VAT Proposal**. The tax payment line that is created includes information about the tax code, the VAT operation code, and the supplier that you pay the tax for.
 

## Create and print factures for VAT deductions

Before you can create and print a facture report for received invoices, issued invoices, purchases, or sales in estimates of VAT, you must complete the following tasks.

1. Set up the parameters for a tax agent transaction.
2. Define a vendor as a tax agent.
3. Create and post a purchase order that has a sales tax group and an item sales tax group.
4. Create a payment proposal, and post the payment.

    As a result of tax payment posting, sales tax transactions are created that have the following tax directions:

    - **Tax agent – charged** – Accrued VAT that must be paid. A facture document is created on this sales tax transaction and will be reflected in the sales book.
    - **Sales tax receivable** – VAT that must be deducted because the VAT amount was transferred to the tax authority. The facture is created on the sales tax transaction and will be reflected in the purchase book after VAT incoming is processed.

5. Select **Accounts payable** \> **Inquiries and reports** \> **Facture**.
6. Select **Print** \> **Original** for the facture that is created on the **Tax agent - charged** sales tax transaction.

The facture report shows the number and date of the payment order, the base amount without VAT, and the computational tax rate (VAT value ÷ VAT value + 100).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
