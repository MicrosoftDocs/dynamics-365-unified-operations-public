---
# required metadata

title: Purchasing cards
description: This topic explains how to setup and track purchasing card transactions.
author: velofog
ms.date: 09/03/2019
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
ms.search.region: Global
ms.search.industry: public sector
ms.author: kfend
ms.search.validFrom: 2019-9-03
ms.dyn365.ops.version: 10.0.7

---

# Purchasing cards

[!include [banner](../includes/banner.md)]


Agencies use purchasing cards so that employees can procure goods and services without using the standard purchase requisition process. The pages and fields that are related to purchasing cards provide a mechanism for tracking purchases. Each purchase that an employee makes by using a purchasing card is recorded on a vendor invoice. However, the invoice isn't paid by using a check or electronic payment to the vendor that provided the goods or services. Instead, each invoice of this type is associated with another vendor invoice that is created to pay the vendor that provides the purchasing card services (that is, the financial institution). The card purchases are paid off when the balance that is owed to the purchasing card services provider is paid each month.

## Enable purchasing card pages and fields

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Invoice** tab, set the **Activate Purchasing cards** option to **Yes**.

## Enter purchasing card records for employees

You must enter information about the purchasing cards that have been issued to employees so that they can purchase goods or services. This information will appear on vendor invoices. When a purchasing card is added to a bank account, vendor invoices can recognize the credit card as valid during invoice processing.

1. Go to **Cash and bank management** \> **Common** \> **Bank accounts**.
2. On the list page, select the bank account for the purchasing card services provider.
3. On the Action Pane, on the **Set up** tab, select **Purchasing cards**.
4. On the **Bank purchasing card** page, select **New** to create a purchasing card record.
5. Enter the following information about the purchasing card:

    - In the **Purchasing card reference number** field, enter the reference number for the credit card. For example, enter the last four digits.

        > [!NOTE]
        > After you've saved the purchasing card reference number, you can't change it.

    - In the **Card holder name** field, enter the cardholder's name as it appears on the purchasing card.
    - In the **Employee** field, select the employee that the card was issued to.
    - Optional: In the **Valid from** field, enter the date when the card was issued to the employee.
    - Optional: In the **Expiry date** field, enter the date when the card expires.
    - Optional: In the **Credit limit** field, enter the maximum amount that can be charged to the card.

## Set up a posting definition for vendor invoices that track employee purchases

You must create a posting definition for the vendor invoices that you enter to record purchases that are made by using a purchasing card. When these invoices are posted, balancing entries for the expenditure are created in General ledger. When a vendor invoice is settled, it's moved to the history, but a payment to the vendor isn't generated. You use this posting definition when you import invoices from an external file and when you manually enter vendor invoices for employee purchases.

Optional: You can set the posting definition so that it's used by default when you create vendor invoices to record purchasing card transactions.

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Invoice** tab, in the **Default posting definition for record purchase** field, select the posting definition that you want to use as the default posting definition.

## Overview: Processing invoices for purchasing card transactions

After you've set up your system for purchasing cards, you can create an invoice for a vendor, or financial institution, that provides purchasing card services. You can also create other invoices to track the purchases that are made by cardholders. After you receive the monthly purchasing card statement from your financial institution, you can distribute it to employees who made purchases during the billing period. Typically, these employees will verify the transactions, and provide receipts or invoices that support their purchases.

1. Create a vendor invoice to pay the purchasing card services provider. You will generate a check for this vendor invoice to pay the balance on the purchasing card statement.
2. Create other vendor invoices to record purchases that have been made by cardholders.

> [!NOTE]
> Typically, you will use the vendor invoice data entities to publish vendor invoice data in the system.

## Create a vendor invoice for a purchasing card statement

Use this procedure to create a vendor invoice to record the periodic statement balance for a purchasing card statement that has been received from a purchasing card services provider.

1. Go to **Accounts payable** \> **Common** \> **Vendor invoices** \> **Open vendor invoices**.
2. On the Action Pane, select **Invoice** \> **Vendor invoice**.
3. On the **Vendor invoice** page, in the **Invoice account** field, enter the account number for the vendor that sent the purchasing card statement.
4. In the **Number** field, enter the invoice number.
5. In the **Lines** grid area, select **Add line**, and then enter information about the line.
6. To specify additional information about the line, select the **Line details** FastTab, and enter the information.
7. Select **Financials** to add or change the financial distribution information for the invoice line.
8. On the Action Pane, select **Header** to enter additional information for the invoice header.
9. On the Action Pane, on the **General** tab, in the **Purchasing card invoice** field, select **Balance payoff** to specify that you're paying off your agency's purchasing card balance.
10. Optional: Submit the invoice to the workflow system for review and approval, and then post the invoice.

    > [!NOTE]
    > Before you create a Purchasing card invoice, you must post the Balance payoff invoice to the purchasing card services provider. All the Purchasing card invoices will be posted against this invoice.

11. To save the invoice without posting it, close the page. You can view the invoice on the **Pending vendor invoices** list page.

## Create a vendor invoice to record a purchasing card transaction

Use the following procedure to create a vendor invoice to record a purchase that was made by using a purchasing card. This invoice will be settled, but not paid, to the vendor who provided the purchased goods or services.

> [!NOTE]
> The invoice for the statement that is set as the Balance payoff invoice must be posted to the vendor account before you create a Purchasing card invoice.

1. Go to **Accounts payable** \> **Common** \> **Vendor invoices** \> **Open vendor invoices**.
2. On the Action Pane, select **Invoice** \> **Vendor invoice**.
3. On the **Vendor invoice** page, in the **Invoice account** field, enter the account number for the vendor that sent the invoice for the goods or services.
4. In the **Number** field, enter the invoice number.
5. On the Action Pane, select **Header** to enter additional information for the invoice header.
6. In the **Purchasing card invoice** field, select **Record purchase** as the type of purchasing card transaction that you're entering the invoice for.

    > [!NOTE]
    > A value of **Balance payoff** indicates that the invoice will pay off a balance that is owed to the purchasing card services provider. A value of **N/A** indicates that the invoice doesn't involve a purchasing card.

7. On the **Setup** FastTab, in the **Posting definition** field, select the posting definition of the purchasing card if a default value wasn't selected on the **Accounts payable parameters** page.

    > [!NOTE]
    > The posting definition that you select must be set up to record the purchase, but not to post to Accounts payable. Otherwise, a payment will be made to the vendor who provided the goods or services that were procured by using the purchasing card.

8. On the **Payment** FastTab, view or enter information about the purchasing card that was used to make the purchase:

    - In the **Purchasing card reference number** field, enter the reference number of the card.
    - View the name of the bank that issued the card. This value appears after you've entered the reference number.
    - View the name of the cardholder. This value is based on the reference number that you entered.
    - In the **Account** field, enter the account number for the vendor that provides the purchasing card services.
    - View the name of the purchasing card services provider. This value is based on the account number that you entered.
    - In the **Purchasing card invoice** field, enter the vendor invoice number of the related Balance payoff invoice that was created to pay the purchasing card statement that included this purchase. This field must be set to the invoice number of the posted invoice that is designated as the Balance payoff invoice. This invoice number will appear in the list if the invoice was marked in the appropriate manner.

9. On the Action Pane, select **Line view** to enter information about the purchase amount.
10. In the **Lines** grid area, select **Add line**, and enter information about the line.
11. To specify additional information about the line, select the **Line details** FastTab, and enter the information.
12. Optional: Submit the invoice to the workflow system for review and approval, and then post the invoice.
13. To save the invoice without posting it, close the page. You can view the invoice on the **Pending vendor invoices** list page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]