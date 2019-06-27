# Purchasing cards

Purchasing cards are used by agencies to allow employees to procure goods and services outside of the standard purchase requisition process. The purchasing card pages and fields provide a method for tracking purchases. Each purchase made by an employee with a card is recorded with a vendor invoice, but the invoice is not paid out with a check. Each of these invoices is associated with another vendor invoice, which is created to pay off the vendor that provides the purchasing card service (that is, the financial institution); the card purchases are paid off when the balance owed to the card service provider is paid each month.

## Enable purchasing card pages and fields
1. Go to **Accounts payable > Setup > Accounts payable parameters**.
2. On the Invoice tab, select the Activate purchasing cards option to **Yes** to enable the functionality.

## Enter purchasing card records for employees
Enter information about the purchasing cards that have been issued to employees to purchase goods or services. This information will appear on vendor invoices. Adding a purchasing card to a bank account enables vendor invoices to recognize the credit card as valid during invoice processing.

1. Go to **Cash and bank management > Common > Bank accounts**.
2. On the list page, select the bank account for the purchasing card services provider.
3. On the Action Pane, click the **Set up** tab, and then click **Purchasing cards**.
4. In the **Bank purchasing card** page, click **New** to create a new purchasing card record.
5. In the **Bank purchasing card** page, enter information about the purchasing card. 
- In the **Purchasing card reference number** field, enter reference number for the credit card, for example the last four digits.
  [Note!] that you cannot change this number after you have saved the purchasing card reference number.
- In the **Card holder name** field, enter the card holder's name as it appears on the purchasing card.
- In the **Employee** field, select the employee whom the card is issued.
6. Optional: For the record you entered, enter additional information about the purchasing card: 
- In the **Valid from** field, enter the date the card was issued to the employee.
- In the **Expiry date** field, enter the date when the card expires.
- In the **Credit limit** field, enter the maximum amount that can be charged to the card.


## Set up a posting definition for vendor invoices that track employee purchases

Create a new posting definition for the vendor invoices that you enter to record purchases made with a purchasing card. When these invoices are posted, balancing entries for the expenditure are created in General ledger. When the vendor invoice is settled, the invoice is moved to history, but checks are not created. Use this posting definition when you import invoices from an external file and when you manually enter vendor invoices for employee purchases.

## Overview: Processing invoices for purchasing card transactions

Once you have set up your system for purchasing cards, you can create an invoice to a vendor that provides purchasing card services (that is, a financial institution) and other invoices to track the purchases made by card holders.
After receiving the monthly purchasing card statement from your financial institution, you may distribute it to card users who made purchases during the billing period. Typically, users will verify the transactions and provide receipts or invoices that support their purchases.
1. Create a vendor invoice to pay the purchasing card providor. You will generate a check for this vendor invoice to pay off the balance on the purchasing card statement. 
2.  Create other vendor invoices to record purchases made by card users.  

[NOTE!] Typically, you will use the vendor invoice data entities to publish vendor invoice data to the system, the steps below are to input the transactions online.

## Create a vendor invoice for a purchasing card service statement

Create a vendor invoice to record the periodic statement balance for a purchasing card statement that has been received from a purchasing card services provider (financial institution).
1. Go to **Accounts payable > Common > Vendor invoices > Open vendor invoices**.
2. On the **Action Pane, click Invoice > Vendor invoice**.
3. In the **Vendor invoice** page, in the **Invoice account** field, enter the account number for the vendor that sent the purchasing card statement.
4. In the **Number** field, enter the invoice number.
5. In the **Lines** grid area, click **Add line**, and then enter information about the line. 
6. To view or specify additional information about the line, click the **Line details** FastTab, and enter the information.
7. In the Action strip, click **Financials** to add or modify the financial distribution information for the invoice line.
8. On the Action Pane, click **Header** view to enter additional information for the invoice header.
9. On the Action Pane, on the **General** tab, in the **Purchasing card invoice** field, select **Balance payoff** to specify that you are paying off your agency's purchasing card balance.
10. Optional: Post the invoice. On the Action Pane, click **Post**.

[NOTE!] Before you create a Purchasing card invoice, you must post the “Balance payoff” invoice to the purchasing card services vendor. All of the Purchasing card invoices will be posted against this.

11. To save the invoice without posting, close the page. You can view the invoice on the **Pending vendor invoices** list page.

## Create a vendor invoice to record a purchasing card transaction

Create a vendor invoice to record a purchase that was made with a Purchasing card. This invoice will be settled, but not paid, to the vendor who supplied the purchased goods or service.

[NOTE!] The invoice for the statement that is set as “Balance payoff” must already be posted to the vendor account prior to your creating a PCARD invoice.

1. Go to **Accounts payable > Common > Vendor invoices > Open vendor invoices**.
2. On the **Action Pane, click Invoice > Vendor invoice**.
3. In the Vendor invoice page, in the Invoice account field, enter the account number for the vendor that sent the invoice for the goods or services.
4. In the Number field, enter the invoice number.
5. On the Action Pane, click Header view to enter additional information for the invoice header.
6. In the **Purchasing card invoice** field, select **Record purchase** as the type of Purchasing card transaction you are entering the invoice for. 

[Note!] **Balance payoff** indicates an invoice that will pay off a balance owed to the Purchasing card services vendor (financial institution). **N/A** indicates an invoice that does not involve a Purchasing card.

7. On the Setup FastTab, in the Posting definition field, select the purchasing card-specific posting definition. The posting definition you enter must have been set up to record the purchase but not post to Accounts payable. For more information, see Setting up to track purchasing card transactions.
8. On the Payment FastTab, enter information about the purchasing card used to make the purchase: 
9. Enter the last four digits of the card.
10. The name of the bank that issued the card appear once you enter the card number.
11. The card holder name that will appear, based on the card number entered.
12. The account number for the vendor that provides the Purchasing card service.
13. The name of the Purchasing card services provider.
14. In the Purchasing card invoice field, enter the vendor invoice number of the related “Balance payoff” invoice that was created to pay off the purchasing card statement that included this purchase. This field must be the posted invoice number designated as the “Balance payoff” invoice. It will appear in the list if the invoice was marked appropriately.
15. On the Action Pane, click Line view to enter information about the purchase amount.
16. In the Lines grid area, click Add line, and enter information about the line. If you enter an item number, lines that are not for a purchase order must have a product type of Item or Service, and must not be stocked.
17. To specify additional information about the line, click the Line details FastTab, and enter the information. 
18. Optional: Submit the invoice to workflow for review and approval process, and then post the invoice. On the Action Pane, click Post, and then click Post in the page that appears.
19. To save the invoice without posting, close the page. You can view the invoice on the Pending vendor invoices list page.




