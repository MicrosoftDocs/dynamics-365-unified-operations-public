---
# required metadata
title: Set up the tax agent transactions
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

# (RUS) Set up the tax agent transactions

You must set up the parameters for tax agent transactions in the general ledger module before you can create the tax agent transactions.



### Set up the VAT operation code for the tax declaration

1.  Click **General ledger** \> **Setup** \> **Sales tax** \> **External** \> **VAT operation codes**.

2.  In the **VAT operation code** field, enter the operation code for the VAT declaration.

3.  In the **Description** field, enter a description of the transaction code.

4.  Press CTRL+S or close the form.

### Set up the sales tax code for tax agent transactions

1.  Click **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax codes**.

2.  Press CTRL+N to create a new tax code.

3.  In the **Sales tax code** field, enter a code for sales tax.

4.  In the **Settlement period** field, select the time period for which the tax is calculated and paid to the tax authority.

5.  In the **Ledger posting group** field, select the ledger posting group for the sales tax code.

6.  In the **Type of tax** field, select **Standard VAT**.

7.  In the **VAT charge** field, select the source of VAT accrual from the following options:
    
      - **From vendor funds** − VAT payment is made from the vendor's income.
    
      - **From own funds** − VAT payment is made from the tax agent's funds.

8.  Click **Values** to open the **Values** form.

9.  In the **Value** field, enter the VAT percentage.

10. Press CTRL+S or close the form.

11. Click **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax groups**.

12. Press CTRL+N to create a sales tax group, and enter the necessary information.

13. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code created in steps 1 through 10.
    

    > [!NOTE]
    > <P>If you select the sales tax code for the <STRONG>From own funds</STRONG> option, the <STRONG>Exempt</STRONG> check box is selected by default on the <STRONG>Setup</STRONG> tab.</P>



14. Press CTRL+S or close the form.

15. Click **General ledger** \> **Setup** \> **Sales tax** \> **Item sales tax groups**.

16. Press CTRL+N to create an item sales tax group, and enter the necessary information.
    
17. On the **Setup** tab, in the **Sales tax code** field, select the sales tax code created in steps 1 through 10.

18. Press CTRL+S or close the form.

### Set up a vendor tax authority

1.  Click **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax authorities**.

2.  Press CTRL+N to create a tax authority, and enter the required details.

3.  In the **Vendor account** field, select the vendor who operates as the tax authority.

4.  Press CTRL+S or close the form.



## (RUS) Create a payment proposal for a tax agent invoice 

You can use the **Vendor payment proposal** form to create payment proposals that you can use to generate payments to a vendor tax agent. You can also generate payments of value-added tax (VAT) to a tax authority.

1.  Click **Accounts payable** \> **Journals** \> **Payments** \> **Payment journal**.

2.  Press CTRL+N to create a new journal, and then click **Lines** to open the **Journal voucher** form.

3.  Click the **General** tab, and then, in the **Agreement company** field, select the legal entity that the purchase agreement is created for.

4.  In the **Agreement ID**, select the identification code for the purchase agreement.

5.  Click **Payment proposal** \> **Create payment proposal** to open the **Vendor payment proposal** form.

6.  In the **Proposal type** field, select the type of payment proposal to create. You can create the proposal by due date, cash discount date, or both due date and cash discount date.
    

    > [!NOTE]
    > <P>By using payment grouping, you can specify the invoices that must be paid to a specific vendor, and then combine the invoices into one payment. You can periodically settle open customer transactions that include the invoices that belong to different agreement numbers.</P>



7.  Click **Select** to define the criteria for the payment proposal.

8.  Click **OK** to open the **Vendor payment proposal** form. In the upper pane, you can view the open invoice transactions that contribute to the payment proposal line On the **VAT Proposal** tab, you can view the details of the tax transaction for the VAT payment to the tax authorities. The **Account number** field displays the account number of the vendor tax agent.

9.  Click **Transfer** to transfer the proposal lines to the payment journal. In the **Journal voucher** form, two payment lines are displayed for each invoice. One line is for payment to a vendor, and the other line is for tax payment to a tax authority. On the second journal line, the purpose of the VAT payment is displayed in the **Purpose text** field. The second line also displays the account number and address of the tax agent.
    

    > [!NOTE]
    > <P>The vendor account of the tax agent is displayed in the <STRONG>Vendor account</STRONG> field on the <STRONG>Payment</STRONG> tab.</P>



10. In the **VAT operation code** field, view or modify the operation code for the VAT declaration.

11. Click **Functions** \> **Settlement** to open the **Settle open transactions** form.

12. Select open vendor transactions, and mark them for settlement. 

13. Close the form.

14. Click **Functions** \> **Generate payments** to open the **Generate payments** form.

15. Select the payment method or the export format, depending on the method of payment on the journal line. Then select the bank account to draw the payment from, and enter the required information. 

16. Click **OK**.

17. Click **Print** \> **Payment order** to print the payment order report.

18. In the **Journal voucher** form, click **Validate** \> **Validate** to validate the journal line. Then click **Post** \> **Post** to post the journal line. Payments to tax authorities can also be made by using the **Periodic settlement** form.
    

    > [!NOTE]
    > <P>After payments to the vendor tax agent are completed, you can view the settled transactions in the <STRONG>Transactions on settlement</STRONG> form. You can view the posted sales tax transactions in the <STRONG>Sales tax transactions</STRONG> form.</P>


## (RUS) Create vendor tax agent transactions 

You can define a vendor as a tax agent in the **Vendors** form and perform transactions with this vendor.



1.  Click **Accounts payable** \> **Common** \> **Vendors** \> **All vendors**.

2.  Press CTRL+N to create a vendor tax agent, and enter the necessary information.

3.  On the **General** tab, select the **Tax agent** check box to define the vendor as a tax agent.

4.  In the **Vendor type** field, select the type of vendor from the following options:
    
      - **Blank** – If the vendor is not a tax agent.
    
      - **Non resident** – If the vendor is a foreigner.
    
      - **State authority** – If the vendor is a governmental or municipal authority.

5.  In the **VAT operation code** field, select the operation code for VAT declaration.

6.  Press CTRL+S or close the form.

7.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

8.  Press CTRL+N to create a purchase order for the vendor tax agent. Enter the necessary information.

9.  Click the **Header** view, and then, on the **Setup** tab, in the **VAT operation code** field, view or modify the code for VAT declarations.

10. Click **Posting** \> **Invoice** to open the **Posting invoice** form.

11. In the **Invoice** field, enter the invoice number.

12. Click **OK** to post the invoice.


## (RUS) Create and print factures for VAT deductions 

You can use the **Update facture** form to create and print factures for journals that have been posted. You can then view the factures that you created or updated in the **Facture journal** form.

Before you can create and print a facture report for received invoices, issued invoices, purchases, or sales in estimates of value-added tax (VAT), you must complete the following tasks:

1.  Set up the parameters for a tax agent transaction.

2.  Define a vendor as a tax agent.

3.  Create and post a purchase order that has a sales tax group and an item sales tax group.

4.  Create a payment proposal, and post the payment.

The facture report displays the number and date of the payment order, the base amount without VAT, and the computational tax rate (VAT value / VAT value + 100).


> [!NOTE]
> <P>If the source of the facture is <STRONG>Tax correction</STRONG>, enter an explanatory note about the details of the invoice line in the <STRONG>Note</STRONG> field in the <STRONG>Facture journal</STRONG> form. This information is displayed on the facture report.</P>



1.  Click **Accounts payable** \> **Inquiries** \> **Journals** \> **Invoice journal**.

2.  Select the journal line for the posted journal, and then click **Create facture** \> **Update facture**.

3.  In the **Facture** field, enter an identification number for the facture.

4.  In the **Date of the registration** field, select the date when the facture is registered.

5.  In the **Facture date** field, select the date when the facture is created.
    

    > [!NOTE]
    > <P>You can select the facture date only if you clear the <STRONG>Same as</STRONG> check box. Otherwise, this field displays the same date that you select in the <STRONG>Date of the registration</STRONG> field.</P>



6.  In the lower pane, on the **Invoice** tab, select the **To facture** check box to update the facture by using the selected invoice.

7.  In the upper pane, click **Posting** \> **Update and print** to update and print the facture.
    

    > [!TIP]
    > <P>Click <STRONG>Posting</STRONG> &gt; <STRONG>Update</STRONG> to update changes to the facture, but without printing the facture.</P>
    > <P>–or–</P>
    > <P>Click <STRONG>Posting</STRONG> &gt; <STRONG>Print</STRONG> to print the facture without posting it.</P>



8.  Click **Accounts payable** \> **Inquiries** \> **Journals** \> **Facture**. You can view the facture that you created or updated in the **Facture journal** form. These factures can be registered in the sales book. 
