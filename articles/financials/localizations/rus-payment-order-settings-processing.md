---
# required metadata
title: Set up a method of payment 
description: This topic provides information about payment order settings and processing for Russia. 
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


# Set up a method of payment 

[!include [banner](../includes/banner.md)]

The method of payment determines the format that is used for export of payment orders. Within the payment type, you can also set up bridging accounts when reconciliation is being done. In this case, when posting payment journals, the payments are reflected in off-balance Accounts payable and banking operations. After banking reconciliation, these transactions are reversed and reflected in Accounts payable and banking accounts. To link actual accounts with payment types, in most cases, the number of payment types created equals the number of accounts that the company holds.


1.  Click **Accounts payable** \> **Setup** \> **Payment** \> **Methods of payment**.

2.  Press CTRL+N to create a new line.

3.  In the **Method of payment** field, enter the code for the method of payment.

4.  In the **Description** field, enter a description for the method of payment.

5.  In the **Payment status** field, select the status for the payment line, which indicates the status for posting.

6.  On the **General** tab, in the **Account type** field, select the account type as **Bank**.

7.  In the **Payment account** field, select the bank account for payment.

8.  Select the **Bridging Posting** check box.
    
    > [!NOTE]
    > You can enter information in the **Bridging account** field only after you select the **Bridging Posting** check box.

9.  In the **Bridging account** field, select the account number for posting in the ledger.

10. In the **Bank transaction type** field, select the bank transaction type.

11. On the **File formats** tab, click **Setup** to open the **File formats for methods of payment** page.

12. Transfer formats from the **Available** field to the **Selected** field to generate a list of accessible formats for exporting payment orders.

13. Close the form and return to the **File formats** tab in the **Methods of payment** page.

14. In the **Export format** field, select the format for exporting payment orders for the specified method of payment.
    

    > [!NOTE]
    > When using the customer-bank, the **Export format** field should show the class that handles the export of data for the payment journal to an external file in a format that corresponds to the customer-bank of the actual bank.



15. On the **Payment control** tab, select the control for the method of payment from the following list:
    
      - **Payment reference is mandatory** – Checks that the essential details for the payment are filled in.
    
      - **Payment note is mandatory** – Checks that the note for the payment is filled in.
    
      - **Payment ID is mandatory** – Checks that the ID for the payment is filled in.
    
      - **Payment specification is mandatory** – Checks that the payment specification is filled in.
    
      - **Check number is mandatory** – Checks that the check number is filled in.
    
      - **Offset account has the type bank** – Checks that the type of corresponding account is **Bank**.
    
      - **Bank transaction type is mandatory** – Checks that a type of bank operation is selected.

16. Press CTRL+S or close the page.


## Set up to generate a payment order in rubles 


1.  Click Click **Cash and bank management** \> **Common** \> **Bank accounts**. Select a bank account. On the **Action Pane**, click **Edit**.

2.  On the **Currency management** tab, in the **P/O numeration** field, select a number sequence for numbering payment orders in a single account.
    

    > [!NOTE]
    > If the number sequence is not set up, the number for the payment order will be retrieved from the Accounts payable parameters setup.



3.  Press CTRL+S or close the form.

4.  Click **Accounts payable** \> **Setup** \> **Payment** \> **Methods of payment**.

5.  On the **File formats** tab, in the **Export format** field, select **Payment order in RUB** for export of payments.For more information, see [Set up a method of payment](./rus-payment-order-settings-processing.md).
    
6.  Press CTRL+S or close the form.


## Set up a method of payment for currency transactions 


Use the **Methods of payment - vendors** form to set up a method of payment for currency transactions.

1.  Click **Accounts payable** \> **Setup** \> **Payment** \> **Methods of payment**.

2.  Press CTRL+N to create a new method of payment.

3.  On the **General** FastTab, in the **Bank transaction type** field, select the type of bank transaction.
    
    > [!NOTE]
    > This field is available only when you select **Bank** in the **Account type** field.

4.  In the **Payment account** field, select the ID of the bank account.

5.  On the **File formats** FastTab, click **Setup** to open the **File formats for methods of payment** page.

6.  On the **Export** tab, in the **Available** list, select **Currency transfer order**.

7.  Click **\<** to move the selected export file format to the **Selected** list.

8.  Close the **File formats for methods of payment** page.

9.  In the **Methods of payment - vendors** page, in the **Export format** field, select **Currency transfer order** as the format for the export of payments.


## Set up an intermediate bank account for a foreign vendor 

You can use the **Vendor bank accounts** form to set up a foreign bank account for a vendor, so that you can make payments by using payment orders or payment requests. This bank account is registered with the foreign bank that is linked to the vendor account. For more information, see [Set up a foreign bank](../rus-local-settings-requisites-bank-module.md).

You can also set up an intermediate Russian bank account to link to the vendor payments that are made to the foreign bank. You can specify a bank code, an account number, and a Society for Worldwide Interbank Financial Telecommunication (SWIFT) code for the foreign bank that the payments are made to.

1.  Click **Accounts payable** \> **Common** \> **Vendors** \> **All vendors**.

2.  Select the vendor account that is linked to the foreign bank, and then click **Set up** \> **Bank accounts** to open the **Vendor bank accounts** page.

3.  Create a bank account for the vendor.

4.  On the **General** FastTab, in the **Foreign bank** field group, in the **Bank groups** field, select the code of the foreign bank with which the vendor bank account is registered.

5.  In the **Bank account number** field, enter the bank account number of the vendor.

6.  In the **SWIFT** field, enter the SWIFT code of the bank.


 

## Generate a payment order in rubles 


1.  Click **Accounts payable** \> **Journals** \> **Payments** \> **Payment journal**.

2.  On the **Overview** tab, press CTRL+N to create a new line.

3.  In the **Date** field, select the date of payment.

4.  In the **Account** field, select the vendor account.

5.  In the **Transaction text** field, enter text that describes the transaction.

6.  In the **Debit** field, enter the sum of the payment.

7.  In the **Offset account type** field, select the account type for the selected account.

8.  In the **Offset account** field, select the offset account for the transaction.

9.  In the **Currency** field, select the currency code.

10. In the **Purpose text** field, enter any text that must be reflected in the payment order.
    
    > [!NOTE]
    > If you click **VAT in payment order**, the text, including the VAT amount in the **Purpose text** field, will be entered.


11. In the **Method of payment** field, select the method of payment to the vendor.

12. On the **General** tab, in the **Contracts group** field, select the contract group.

13. In the **DVR** field, select the registration number of the contract.

14. In the **Sales tax group** and the **Item sales tax group** fields, select the tax groups for VAT calculation.

15. On the **Bank** tab, in the **Bank transaction type** field, select the transaction type.

16. In the **Account identification** field, select the bank account of the recipient.
    
    > [!NOTE]
    > If the payment order is being generated for a legal representative of the vendor, the code must be entered in the **Payment documented on** field. Along with this, the payment order slip will refer to the bank of the vendor that is specified in the **Payment documented on** field, but the transaction will be performed for the vendor that is specified in the **Account** field.

17. On the **Payment order** tab, in the **Order of payment** field, specify the order of payment.

18. In the **Number status** field, specify the number status of the payment.

19. In the **Origin payment** field, specify the origin of the payment.

20. In the **Payment type** field, specify the type of payment.

21. Click **Functions**, and then select **Generate payments** to open the **Generate payments** form.

22. In the **Method of payment** field, select the method of payment.

23. In the **Export format** field, select **Payment order in RUB**.

24. In the **Bank account** field, select the bank account from which the payment is to be made.

25. Select the **Show format dialog** check box.

26. Click **OK**. The **Payment order setup** form opens.

27. Select the **Document** check box to print the payment document.

28. Select the **Warrant text** check box to print the warrant text.

29. Click **OK**. The payment order is generated, and the payment status of the appropriate payment journal line is changed to **Sent**.

30. Click **Functions**, and then select **Void payment order** to void a payment order from the payment journal lines. The value for the voided payment order in the **Payment status** field is **None** after the voided payment order is deleted from the registry of payment orders.

31. To post a payment journal, click **Post**. A transaction is generated for the bank account, vendor, and accounting transactions to reflect the outgoing payment.
    

    > [!NOTE]
    > If the method of payment is **Bridging Posting**, the payment will be posted to the bridging accounts. You can view the transactions in the **Journal voucher** page, **Bank transactions** page, and **Vendor** page.</P>

    
    The payment journal can also be used to register an outgoing payment for a cash refund to a customer. In the **Journal voucher** form, select **Customer** in the **Account type** field, the customer code in the **Account** field, and the payment type of the customer in the **Method of payment** field. Click **Accounts receivable** \> **Setup** \> **Payment** \> **Methods of payment**.

32. To reprint a payment order:
    
      - Click **Print**, and then click **Print payment order** in the **Journal voucher** form.
    
      - Payment orders can also be reprinted from the **Bank transactions** form. Select the voucher for the payment order, click **Print**, and then click **Payment order** to print the document.

## Registry of payment orders

Generated payment orders are available in the **Registry of payment orders** form.

1.  Click **Accounts payable** \> **Inquiries** \> **Payment order register**.

2.  View the information in all the fields.

3.  On the **Essential elements** tab, view the attributes of the payer and the recipient.

## Payments to foreign bank accounts 


Payments that are made to vendors by using payment orders or payment requests must include additional information about the vendor bank account if the vendor uses a foreign bank to receive payments. This bank account can include the bank code, the bank name, the Society for Worldwide Interbank Financial Telecommunication (SWIFT) code of the foreign bank, the foreign bank account number of the vendor, and the address of the payer.

When you make payments to the foreign bank account of a vendor, the vendor must register a bank account with a Russian bank. This bank account can be assigned as an intermediate bank account between the payer and the vendor. You can generate a payment order for the payments, and then enter the details of the vendor bank account and the vendor account that the payments are made to.

For transactions that involve payment returns to a foreign customer, you can set up a customer bank account to receive the returned payments, and then generate a customer payment order that includes the bank and address of the payer.

### Setting up payments to foreign bank accounts

You must complete the following tasks if you want to generate a payment order for payments to a foreign vendor bank account, or to send a payment return to a foreign customer bank account:

  - Set up a bank account in the **Bank accounts** page. 
  - Set up a vendor account in the **Vendors** page.
  - Set up a customer account in the **Customer** page. 
  - Set up payment journals for a vendor account and a customer account in the **Ledger journal** page.



## Generate a payment order for a foreign vendor
   
You can use the **Generate payments** form to generate a payment order for payments that are made to the foreign bank account of a vendor. Before you generate a payment order, you can use the **Journal voucher** form to register a line in the payment journal to record the vendor payments.

1. Click **Accounts payable** > **Journals** > **Payments** > **Payment journal**.
2. Select a vendor payment journal, and then click **Lines** to open the **Journal voucher** page.
3. In the **Method of payment** field, select the payment method for the current payment.
4. Click the **Bank** tab, and then, in the **Account identification** field, enter the foreign bank account of the vendor.
5. In the **Payment documented on** field, select the vendor account that the payments are made to.
6. Click **Functions** > **Generate payments** to open the **Generate payments** form. For more information, see "Generate a payment order in rubles".
7. Click **OK** to generate the payment order.

## Set up a customer bank account for payment returns from a foreign vendor 

For transactions that involve payment returns to a foreign customer, you can set up a customer bank account to receive the payments that are returned. You can then generate a customer payment order that includes the bank and address of the payer. Use the following procedure to set up a customer bank account for payment returns.

1.  Click **Accounts receivable** \> **Common** \> **Customers** \> **All customers**.
2.  Select a customer account, and then click **Set up** \> **Bank accounts** to open the **Customer bank accounts** page.
3.  Create a bank account for the customer to receive payment returns from a foreign vendor.
4.  Click the **General** tab.
5.  In the **Foreign bank** field group, in the **Bank name** field, select the code of the foreign bank with which the customer bank account is registered.
6.  In the **Bank account number** field, enter the foreign bank account number for the account that receives payment returns from the vendor.
7.  In the **SWIFT** field, enter the Society for Worldwide Interbank Financial Telecommunication (SWIFT) code of the bank that receives payment returns from the vendor.

## Generate a customer payment order for a payment return 

When you send a payment return to the foreign bank account of a customer, you can generate a payment order to make the payment. You can use the **Journal voucher** form to register a line in the payment journal to record the customer payment.

1.  Click **Accounts receivable** \> **Journals** \> **Payments** \> **Payment journal**.
2.  Select a customer payment journal, and then click **Lines** to open the **Journal voucher** page.
3.  In the **Method of payment** field, select the payment method for the current payment.
4.  Click the **Bank** tab, and then, in the **Account identification** field, enter the bank account number of the customer account that receives the payment return.
5.  In the **Payment documented on** field, select the customer account that receives the payment return.
6.  Click **Functions** \> **Generate payments** to open the **Generate payments** page. 
7.  Click **OK** to generate the payment order.

## Register an incoming bank payment from a customer 

1.  Click **Accounts receivable** \> **Journals** \> **Payments** \> **Payment journal**. Click **Lines**.
2.  Create a new journal line.
3.  In the **Date** field, select the date of the payment.
4.  In the **Account** field, select the customer code.
    
    > [!NOTE]
    > If a vendor payment, such as a refund, is being made, select **Vendor** in the **Account type** field on the **General** tab. On the **Overview** tab in the **Account** field, select the vendor code.</P>

5.  In the **Transaction text** field, enter or select the transaction text.
6.  In the **Credit** field, enter the sum of the payment.
7.  In the **Offset account type** field, select **Bank**.
8.  In the **Offset account** field, select the bank account.
9.  In the **Currency** field, select the payment currency.
10. On the **General** tab, in the **Contracts group** field, select the contract group.
    
    > [!NOTE]
    > If the payment is a prepayment, select the **Prepayment** check box on the **Payment** tab. The **Sales tax group**, **Item sales tax group**, and **Posting profile** fields will be entered automatically to calculate VAT for prepayment.

11. Click **Post**, and then click **Post** again to post the incoming payment.
    
    When the journal is posted, transactions will be generated for the bank account, customer account, and ledger. The debit account will be the account in the ledger configured for the bank account. The credit account will be determined by the posting profile that is selected for the customer.


## Transit account function 

Use the **Transit account** function to change the date of a posted transaction. The banking operation type must be created, and a transaction account must be set. This function is applied to transactions of the types **Bank-Bank**, **Cash account-Bank**, and **Ledger-Bank**.

You cannot post incoming or outgoing payments if the selected bank account is inactive, or if the receipt date of the banking operation is outside the period when the account is active.

