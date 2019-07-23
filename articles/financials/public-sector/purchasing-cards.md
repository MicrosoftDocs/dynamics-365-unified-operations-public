---
# required metadata

title: Purchasing cards
description: This topic explains how to use cash control to define transaction limits when there is no cash balance or a transaction will cause the cash balance to fall below a predefined amount.
author: velofog
manager: AnnBe
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2019-8-02
ms.dyn365.ops.version: 10.0.5

---

# Purchasing cards

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Purchasing cards are used by agencies to allow employees to procure goods and services outside of the standard purchase requisition process. The Purchasing card pages and fields provide a method for tracking purchases. Each purchase made by an employee with a card is recorded with a vendor invoice. However, the invoice is not paid out with a check or electronic payment to the vendor that provided the goods or service. Each of these invoices is associated with another vendor invoice, which is created to pay off the vendor that provides the Purchasing card service (that is, the financial institution). The card purchases are paid off when the balance owed to the card service provider is paid each month.

## Enable Purchasing card pages and fields

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**.
2. On the **Invoice** tab, set the **Activate Purchasing cards** option to **Yes** to enable the functionality.

## Enter Purchasing card records for employees

Enter information about the Purchasing cards that have been issued to employees to purchase goods or services. This information will appear on vendor invoices. Adding a Purchasing card to a bank account enables vendor invoices to recognize the credit card as valid during invoice processing.

1. Go to **Cash and bank management** > **Common** > **Bank accounts**.
2. On the list page, select the bank account for the Purchasing card services provider.
3. On the Action Pane, select the **Set up** tab, and then select **Purchasing cards**.
4. In the **Bank purchasing card** page, click **New** to create a new Purchasing card record.
5. In the **Bank purchasing card** page, enter the following information about the Purchasing card:

  - In the **Purchasing card reference number** field, enter the reference number for the credit card. For example, the last four digits.

  > [!NOTE] 
  > After you have saved the Purchasing card reference numbers, you can't change it.

  - In the **Card holder name** field, enter the card holder's name as it appears on the Purchasing card.
  - In the **Employee** field, select the employee to whom the card is issued.
  
6. Optional: For the record you entered, enter additional information about the Purchasing card: 

  - In the **Valid from** field, enter the date the card was issued to the employee.
  - In the **Expiry date** field, enter the date when the card expires.
  - In the **Credit limit** field, enter the maximum amount that can be charged to the card.


## Set up a posting definition for vendor invoices that track employee purchases

Create a new posting definition for the vendor invoices that you enter to record purchases that are made with a Purchasing card. When these invoices are posted, balancing entries for the expenditure are created in General ledger. When the vendor invoice is settled, the invoice is moved to history, but a payment to the vendor is not generated. Use this posting definition when you import invoices from an external file and when you manually enter vendor invoices for employee purchases.   

Optional: You can set the posting definition to default when you create vendor invoices to record purchasing card transactions.

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**.
2. On the **Invoice** tab, in the **Default posting definition for record purchase** field select the posting definition you want as the default.

## Overview: Processing invoices for Purchasing card transactions

After you have set up your system for Purchasing cards, you can create an invoice for a vendor, or financial institution, that provides Purchasing card services, and other invoices to track the purchases made by card holders.
After you receive the monthly Purchasing card statement from your financial institution, you may distribute it to card users who made purchases during the billing period. Typically, users will verify the transactions and provide receipts or invoices that support their purchases.

1. Create a vendor invoice to pay the Purchasing card providor. You will generate a check for this vendor invoice to pay off the balance on the Purchasing card statement. 
2.  Create other vendor invoices to record purchases made by card users.  

> [!NOTE] 
> Typically, you will use the vendor invoice data entities to publish vendor invoice data to the system.

## Create a vendor invoice for a Purchasing card service statement

Create a vendor invoice to record the periodic statement balance for a Purchasing card statement that has been received from a Purchasing card services provider.

1. Go to **Accounts payable** > **Common** > **Vendor invoices** > **Open vendor invoices**.
2. On the Action Pane, select **Invoice** > **Vendor invoice**.
3. On the **Vendor invoice** page, in the **Invoice account** field, enter the account number for the vendor that sent the Purchasing card statement.
4. In the **Number** field, enter the invoice number.
5. In the **Lines** grid area, select **Add line**, and then enter information about the line. 
6. To view or specify additional information about the line, select the **Line details** FastTab, and enter the information.
7. Select **Financials** to add or modify the financial distribution information for the invoice line.
8. On the Action Pane, click **Header** to enter additional information for the invoice header.
9. On the Action Pane, on the **General** tab, in the **Purchasing card invoice** field, select **Balance payoff** to specify that you are paying off your agency's Purchasing card balance.
10. Optional: Submit the invoice to workflow for review and approval process, and then post the invoice. 

> [!NOTE] 
> Before you create a Purchasing card invoice, you must post the **Balance payoff** invoice to the Purchasing card services vendor. All of the Purchasing card invoices will be posted against this.

11. To save the invoice without posting, close the page. You can view the invoice on the **Pending vendor invoices** list page.

## Create a vendor invoice to record a Purchasing card transaction

Create a vendor invoice to record a purchase that was made with a Purchasing card. This invoice will be settled, but not paid, to the vendor who supplied the purchased goods or service.

> [!NOTE] 
> The invoice for the statement that is set as **Balance payoff** must already be posted to the vendor account prior to your creating a Purchasing card invoice.

1. Go to **Accounts payable** > **Common** > **Vendor invoices** > **Open vendor invoices**.
2. On the Action Pane, click **Invoice** > **Vendor invoice**.
3. On the **Vendor invoice** page, in the **Invoice account** field, enter the account number for the vendor that sent the invoice for the goods or services.
4. In the **Number** field, enter the invoice number.
5. On the Action Pane, click **Header** to enter additional information for the invoice header.
6. In the **Purchasing card invoice** field, select **Record purchase** as the type of Purchasing card transaction you are entering the invoice for. 

[!NOTE] 
> **Balance payoff** indicates an invoice that will pay off a balance owed to the Purchasing card services vendor. **N/A** indicates an invoice that does not involve a Purchasing card.

7. On the **Setup** FastTab, in the **Posting definition** field, select the posting definition of the Purchasing card if a default value was not selected on the **Accounts payable parameters** page. 

> [!NOTE] 
> The Posting definition you select must have been set up to record the purchase but not post to Accounts payable. Otherwise, a payment will be made to the vendor providing the good or service procured with the purchasing card. 

8. On the **Payment** FastTab, enter information about the Purchasing card used to make the purchase: 

- In the **Purchasing card reference number** field, enter the reference number of the card.
- View the name of the bank that issued the card appear after you have entered the reference number.
- View he card holder name, based on the reference number entered.
- In the **Account** field, enter the account number for the vendor that provides the Purchasing card service.
- View the name of the Purchasing card services provider, based on the account number entered.
- In the **Purchasing card invoice** field, enter the vendor invoice number of the related **Balance payoff** invoice that was created to pay off the purchasing card statement that included this purchase. This field must be the posted invoice number designated as the **Balance payoff** invoice. It will appear in the list if the invoice was marked appropriately.

9. On the Action Pane, click **Line view** to enter information about the purchase amount.
10. In the **Lines** grid area, click **Add line**, and enter information about the line. 
11. To specify additional information about the line, click the **Line details** FastTab, and enter the information. 
12. Optional: Submit the invoice to workflow for review and approval process, and then post the invoice. 
13. To save the invoice without posting, close the page. You can view the invoice on the **Pending vendor invoices** list page.
