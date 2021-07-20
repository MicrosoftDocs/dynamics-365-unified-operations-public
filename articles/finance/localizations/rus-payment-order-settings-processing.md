---
# required metadata
title: Set up and process payment orders for Russia
description: This topic explains how to set up and process payment orders for Russia.
author: ShylaThompson
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia # ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up and process payment orders for Russia

[!include [banner](../includes/banner.md)]

## Setup for generating payment orders

Before you can generate payment orders, you must complete the following setup:

- Set up banks and bank accounts for the company. For more information, see [Local settings and requisites for Bank module](rus-local-settings-requisites-bank-module.md).
- Set up vendor bank accounts and customer bank accounts:

    1. In the All customers or All vendors page, select **Bank accounts** on **VENDOR** tab.
    2. Create a bank account, and fill in all the required information.
    3. For foreign customer or vendor bank accounts, on the **General** FastTab, in the **Foreign bank** section, in the **Bank groups** field, select the code of the foreign bank that the customer bank account is registered with. In the **Bank account number** field, enter the foreign bank account number for the account that receives payments. Finally, in the **SWIFT** field, enter the Society for Worldwide Interbank Financial Telecommunication (SWIFT) code of the bank that receives payments.

    ![Vendor bank account.](media/rus-vendor-bank-account-screenshot-5.jpg)

- To generate payments to vendors, set up a method of payment at **Accounts payable \> Payment setup \> Methods of payment**. To generate payment returns to customers, set up a method of payment at **Accounts receivable \> Payment setup \> Methods of payment**.
- To print payment orders in Russian rubles according to the paper format, on the **Methods of payment** page, on the **File formats** FastTab, in the **Export format** field, select **Payment order in RUB**. To print payment orders in a foreign currency according to a bank-specific template, in the **Export format** field, select **Payment order in currency**. (The bank-specific template is defined in the bank account.)

## Generate a payment order in Russian rubles for a payment to a vendor

### Create payment order lines
Before you can generate a payment order, you must create payment order lines.

1. Select **Accounts payable \> Payments \> Payment journal**.
2. Create a journal, and then, on the Action Pane, select **Lines** to open the **Vendor payments** page.
3. Create a vendor payment line.
4. In the **Date** field, select the date of payment.
5. In the **Account** field, select the vendor account.
6. In the **Transaction text** field, enter text that describes the transaction.
7. In the **Debit** field, enter the sum of the payment.
8. In the **Currency** field, select the currency code.
9. In the **Offset account type** field, select the account type for the selected account.
10. In the **Offset account** field, select the offset account for the transaction.
11. In the **Currency** field, select the currency code.
12. In the **Method of payment** field, select the method of payment to use for the vendor.
13. In the **Agreement ID** field, select the registration number of the contract.
14. In the **Sales tax group** and **Item sales tax group** fields, select the tax groups for the calculation of value-added tax (VAT).
15. On the **Bank** tab, in the **Bank transaction type** field, select the transaction type.
16. In the **Account identification** field, select the bank account of the recipient.

    > [!IMPORTANT]
    > If you're generating a payment order for a legal representative of the vendor, you must enter the vendor account in the **Payment documented on** field. In this case, the payment order slip will refer to the bank of the vendor that is specified in the **Payment documented on** field. However, the transaction will be performed for the vendor that is specified in the **Account** field.

17. On the **Payment order** tab, in the **Purpose text** field, enter any text that must be reflected on the payment order.

    If you select **VAT in payment order**, the text will be entered. This text includes the VAT amount in the **Purpose text** field.

19. Set the following fields: **Order of payment**, **Number status**, **Budget revenue code**, **Origin payment**, **Payment type**, **UCI**, and the fields in the **Period** section (**Period code**, **Period number**, **Year**, **Period date**). The values will be printed in the corresponding boxes on the payment order for the vendor or tax authority.

    ![Vendor payments.](media/rus-vendor-payments-screenshot-4.jpg)

### Generate a payment order
After you've created payment order lines, you can generate the payment order.

1. On the **Vendor payments** page, on the Action Pane, select **Generate payments** to open the **Generate payments** dialog box.
2. In the **Method of payment** field, select the method of payment. Alternatively, in the **Export format** field, select **Payment order in RUB**.
3. In the **Bank account** field, select the bank account that the payment should be made from.
4. Select **OK** to open the **Payment order setup** dialog box. 
5. Set the **Document** option to **Yes** to print the payment order, and set the **Proxy text** option to **Yes** to print the text.
6. Select **OK**. The payment order is generated, and the payment status of the appropriate payment journal line is changed to **Sent**.

### Void a payment order

You can void a payment order in the payment journal. On the **Vendor payments** page, on the Action Pane, select **Functions \> Void payment order**. The payment status of the payment journal line for the voided payment order is changed to **None**, and the voided payment order is deleted from the registry of payment orders.

### Reprint a payment order

You can reprint a payment order. On the **Vendor payments** page, on the Action Pane, select **Print \> Print payment order**. You can also reprint payment orders from the **Bank transactions** page. Select the voucher for the payment order, and then select **Print \> Payment order** to print the document.

### View generated payment orders

You can review generated payment orders on the **Registry of payment orders** page (**Accounts payable \> Inquiries and reports \> Payment \> Payment order register**). On the **Essential elements** tab, review the information about the payer and the recipient.

## Generate a payment order for a payment return to a customer

You can generate a payment order for a money return to a customer.

1. Select **Accounts receivable \> Payments \> Payment journal**.
2. Create a journal, and then, on the Action Pane, select **Lines** to open the **Customer payments** page.
3. Create a customer payment line. Enter information as you did when you created a vendor payment line earlier in this topic.
4. On the **Bank** tab, in the **Account identification** field, enter the bank account number of the customer account that should receive the payment return.
5. In the **Payment documented on** field, select the customer account that should receive the payment return.
6. On the Action Pane, select **Functions \> Generate payments** to generate a payment order.

You can review generated payment orders for customers on the **Registry of payment orders** page (**Accounts receivable \> Inquiries \> Payment \> Payment order register**). 


## Review Registry of payment orders

The registry of payment orders report contains the list of payment orders for a bank account in a period. This report includes the following data for each payment order:

- Number and date
- Name and bank account number of counteragent
- Payment purpose
- Payment amount and currency code
- Status of payment
- Note indicating if the payment is electronic

To run the report, complete the following steps.
1. Go to **Accounts payable > Inquiries and reports > Payment > Payment order register** or **Accounts receivable > Inquiries > Payment > Payment order register**.
2. Click **Print > Registry of payment orders**.
3. Select the **From date** and **To date**.
4. Define the following filters for payment orders: **Payment order status**, **Curreny code**, **Bank account** and **Electronic payment** remark (All, Electronic, Printout form).
5. Click **OK** to generate the report.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]