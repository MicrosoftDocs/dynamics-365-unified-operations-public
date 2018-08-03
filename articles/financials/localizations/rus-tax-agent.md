---
# required metadata

title: Set up VAT for tax agents and tax agent transactions
description: This topic provides information about setting up the tax agent transactions for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
			
# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---
# Overview of VAT for tax agents

When a company is acknowledged as a tax agent it has to accrue and to deduct VAT correctly from funds, paid to taxpayers (or to accrue at the expense of own funds), and to transfer VAT to the tax authority. 
This functionality is required to support generation of invoices, factures, and payments to vendors for whom our company is defined as tax (fiscal) agents.
The following functions are supported: 
 - Creating vendors with whom we operate as tax agent.
 - Marking sales tax codes for tax agent transactions to determine if the VAT payments are to be made from the vendor's funds or at the expense of the company's own funds.
 - Creating payment proposals for  vendors' invoices.
 - Creating payments for tax authorities
 - Posting and settlement of payments to the vendor.
 - Creating and printing factures for VAT amount, being liable to the budget, and registering the factures in the sales book
 - Creating and printing factures for VAT deductions and registering the factures in the purchase book.

## Set up the tax agent transactions

You must set up the parameters for tax agent transactions in the Tax module before you can create the tax agent transactions.

### Set up the VAT operation code for the tax declaration

1.  Click **Tax** \> **Setup** \> **Sales tax** \> **VAT operation codes**.

2.  In the **VAT operation code** field, enter the operation code for the VAT declaration.

3.  In the **Description** field, enter a description of the transaction code.

4.  Press CTRL+S or close the form.

### Set up the sales tax code for tax agent transactions

1.  Click **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.

2.  Press CTRL+N to create a new tax code.

3.  In the **Sales tax code** field, enter a code for sales tax.

4.  In the **Settlement period** field, select the time period for which the tax is calculated and paid to the tax authority.

5.  In the **Ledger posting group** field, select the ledger posting group for the sales tax code.

6.  In the **Type of tax** field, select **Standard VAT** or **Reduced VAT**.

7.  In the **VAT charge** field, select the source of VAT accrual from the following options:
    
      - **From vendor funds** − VAT payment is made from the vendor's income.
    
      - **From own funds** − VAT payment is made from the tax agent's funds.

8.  Click **Values** to open the **Values** form.

9.  In the **Value** field, enter the VAT percentage.

10. Press CTRL+S or close the form.

11. Click **Indirect taxes** \> **Sales tax** \> **Sales tax groups**.

12. Press CTRL+N to create a sales tax group, and enter the necessary information.

13. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code created in steps 1 through 10.
    

    > [!NOTE]
    > If you select the sales tax code for the <STRONG>From own funds</STRONG> option, the <STRONG>Exempt</STRONG> check box is selected by default on the <STRONG>Setup</STRONG> tab.


14. Press CTRL+S or close the form.

15. Click **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.

16. Press CTRL+N to create an item sales tax group, and enter the necessary information.
    
17. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code created in steps 1 through 10.

18. Press CTRL+S or close the form.

### Set up a vendor tax authority

1.  Click **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.

2.  Press CTRL+N to create a tax authority, and enter the required details.

3.  In the **Vendor account** field, select the vendor who operates as the tax authority.

4.  Press CTRL+S or close the form.

## Create vendor for which our company acts as a tax agent and post transactions

You can define a vendor as a tax agent in the Vendors form and perform transactions with this vendor.

1. Click **Accounts payable** \> **Vendors** \> **All vendors**.

2. Press CTRL+N to create a vendor for which our company acts as a tax agent, and enter the necessary information.

3. On the **General** tab, select the **Tax agent** check box to define the vendor as a tax agent.

4. In the **Vendor type** field, select the type of vendor from the following options:

   - **Blank** – common vendor.
   - **Non resident** – If the vendor is a foreigner.
   - **State authority** – If the vendor is a governmental or municipal authority.
   
5. In the **VAT operation code** field, select the operation code for VAT declaration.

6. Press CTRL+S or close the form.

7. Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.

8. Press CTRL+N to create a purchase order for the vendor. Enter the necessary information.

9. Click the **Header** view, and then, on the **Setup tab**, in the **VAT operation code field**, view or modify the code for VAT declarations. Select the source for VAT accrual, From vendor funds or From own funds in the VAT charge.

10. Confirm purchase order and post invoice.

## Create tax payments

In the Vendor payment journal, two options for paying VAT as a tax agent are implemented:

 1) Payment for a specific invoice.
 
 2) Prepayment (invoice is unknown).

### Create a payment proposal for a tax agent invoice 

You can use the **Vendor payment proposal** form to create payment proposals that you can use to generate payments to a vendor tax agent. You can also generate payments of value-added tax (VAT) to a tax authority.

1.  Click **Accounts payable** \> **Payments** \> **Payment journal**.

2.  Press CTRL+N to create a new journal, and then click **Lines** to open the **Vendor payments** form.

3.  Click **Payment proposal** \> **Create payment proposal** to open the **Vendor payment proposal** form.

4.  In the **Select invoices by** field, select the type of payment proposal to create. You can create the proposal by due date, cash discount date, or both due date and cash discount date.

5.  Click **Records to include** and then **Filter** to define the criteria for the payment proposal, e.g. Vendor account.

6.  Click **OK** to open the **Vendor payment proposal** form. In the upper pane, you can view the open invoice transactions that contribute to the payment proposal line. On the **VAT Proposal** tab, you can view the details of the tax transaction for the VAT payment to the tax authorities.
    
7.  Click **Create payments** to transfer the proposal lines to the payment journal. In the **Vendor payments** form, two payment lines are displayed for each invoice. One line is for payment to a vendor, and the other line is for tax payment to a tax authority. On the second journal line, the purpose of the VAT payment is displayed in the **Purpose text** field, including vendor account number and address.

    > [!NOTE]
    > For the line which is a tax payment to a tax authority, the sales tax code is displayed in the <STRONG>Sales tax code</STRONG> field on the <STRONG>General</STRONG> tab and the vendor account for whom the tax is paid is displayed in the <STRONG>Vendor account</STRONG> field on the <STRONG>Payment</STRONG> tab.

8. In the **VAT operation code** field, view or modify the operation code for the VAT declaration.

9. Click **Generate payments** to open the **Generate payments** form.

10. Select the payment method or the export format, depending on the method of payment on the journal line. Then select the bank account to draw the payment from, and enter the required information. 

11. Click **OK**.

12. Click **Print** \> **Payment order** to print the payment order report.

13. In the **Journal voucher** form, click **Validate** \> **Validate** to validate the journal line. Then click **Post** \> **Post** to post the journal lines.
    

    > [!NOTE]
    > After payments to the vendor are completed, you can view the settled transactions in the <STRONG>Transactions on settlement</STRONG> form. You can view the posted sales tax transactions in the <STRONG>Sales tax transactions</STRONG> form.

## Create a prepayment

1.  Click **Accounts payable** \> **Payments** \> **Payment journal**.

2.  Press CTRL+N to create a new journal, and then click **Lines** to open the **Vendor payments** form.

3.  Press CTRL+N to create a new journal line, select vendor and enter a prepayment amount.

4.  Set **Sales tax group** and **Item sales tax group** that contain sales tax code with necessary setup of VAT charge.

    > [!NOTE]
    > VAT amount to be paid is calculated based on the value of the sales tax code.
    > To avoid tax calcilation on prepayment itself, <STRONG>Sales tax on prepayment in payment journal</STRONG> should be swithed off in the <STRONG>Accounts payable parameters</STRONG> form on the <STRONG>Ledger and sales tax</STRONG> tab.

5.  Click **Payment proposal** \> **VAT Proposal**. In the created tax payment line there will be information on the tax code, the VAT operation code and the supplier for which we pay the tax.
 

## Create and print factures for VAT deductions 

Before you can create and print a facture report for received invoices, issued invoices, purchases, or sales in estimates of value-added tax (VAT), you must complete the following tasks:

1.  Set up the parameters for a tax agent transaction.

2.  Define a vendor as a tax agent.

3.  Create and post a purchase order that has a sales tax group and an item sales tax group.

4.  Create a payment proposal, and post the payment.

The facture report displays the number and date of the payment order, the base amount without VAT, and the computational tax rate (VAT value / VAT value + 100).


