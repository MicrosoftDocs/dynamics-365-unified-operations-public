--- 
title: Import letter of credit
description: Learn about the procedure for importing a letter of credit, including a step-by-step process for creating a purchase order with a letter of credit. 
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 06/06/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: VendTable, VendBankAccounts, PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, BankLCImport,  PurchEditLines, VendEditInvoice, SrsReportViewerForm, LedgerJournalTable, LedgerJournalTransVendPaym, VendOpenTrans, SysQueryForm, BankAccountTableLookUp
ms.dyn365.ops.version: Version 7.0.0 
---

# Import letter of credit

[!include [banner](../../includes/banner.md)]

The steps below describes the process of importing a letter of credit. Bank facilities, posting profiles, a bank facility agreement and vendor bank details have to be configured before starting this process. For more details, see [Set up bank facilities and posting profiles for letter of credit](set-up-bank-facilities-posting-profiles-letter-credit.md) and [Create a vendor bank account](../../../supply-chain/procurement/tasks/create-vendor-bank-account.md).

## Create a Purchase order with a Letter of credit
1. To create a Purchase order with a letter of credit, go to **Accounts payable > Purchase orders > All purchase orders**.
2. Click **New**.
3. Select a vendor value in the **Vendor account** field.
4. Expand the **General** section.
5. Select values for **Site** and **Warehouse** fields.
6. Enter dates in the **Accounting date** and **Requested receipt date** fields.
    
>[!Note] 
>The **Bank document type** field should be **Letter of credit**.

7. Click **OK**.
8. In the purchase order lines, select **Item number**.
9. Expand the **Line details** section.
10. Click the **Delivery** tab.
11. In the **Confirmed receipt date** field, enter confirmed delivery date.
12. Check the purchase order lines again and add **Unit price** value. This value might already default from purchase trade agreement or item setup.
13. To define the Letter of credit details, on the action pane, click **Manage** > **Letter of credit/import collection**.
14. In the **Application date** field, enter a date and time. Verify the **Bank account** field has the default active bank account, which is based on the application date.
15. In the **Bank document number** field, type a value.
16. In the **Date of receipt** field, enter a date and time.
17. Expand the **Bank document** section.
18. In the **Expiration date** field, enter a date and time.
19. Expand the **Bank details** section.
20. In the **Advising bank** field, enter or select a value.
21. Click **Save**.
22. On the **Lines**, click **Fetch purchase order shipments**.
23. Return back to the **Purchase order**.
24. On the Action Pane, click **Purchase**.
25. Click **Confirm**.
26. On the Action pane, click **Manage**.
27. Click **Letter of credit / import collection**.
28. Click **Process**.
29. Click **Confirm**. 
After re-confirmed, verify the facility balance reduced by the purchase order amount in the **Bank facility agreements** page. 
For example, Purchase amount = 500.00, Facility limit = 10000.00, therefore, Facility balance = 9500.00.

## Amend the price on the Purchase Order line
1. Open the purchase order and update the **Unit price** field on the purchase order line.
2. Click **Save**.
3. Confirm the purchase order by clicking **Purchase > Confirm** on the Action pane.
4. Due to the Unit price changes, you should amend the letter of credit by clicking **Manage > Letter of credit / import collection** on the Action pane.
5. Click **Process > Amend**.
6. Click **Remove > Yes**.
7. Click **Fetch purchase order shipments** on the **Lines** on the Letter of credit / import collection.
8. Click **Process > Confirm**. 
Verify the facility balance reduced by the updated purchase order amount in the **Bank facility agreements** page.
For example, edited Purchase amount = 600.00, Facility limit = 10000.00, therefore, Facility balance = 9400.00
9. Close the page.

## Post Packing slip
1. On the Action Pane, click **Receive**.
2. Click **Product receipt**.
3. In the **Product receipt** field, enter a product receipt number.
4. Select the **Shipment number** created with reference to the Letter of credit.
5. Enter a **Product receipt date**.
6. Click **OK**.

## Verify Import letter of credit status
1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. Verify the **Import letter of credit status**.     

## Post purchase invoice
1. Go to **Accounts payable > Purchase orders > All purchase orders**. Select the purchase order that was created with letter of credit.
2. On the Action Pane, select **Invoice**.
3. Click **Invoice**.
4. Type in the Invoice number in the **Number** field.
5. Select the corresponding **Shipment number**.
6. In the **Invoice date** field, enter an invoice date.
7. Click **Update match status**.
8. Post the invoice by pressing **Post**.

## Verify Import letter of credit status and printing
1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. In the list, find and select the desired record.
3. Verify the Import letter of credit details.
4. Validate **Shipment status** = **Invoiced**.
5. To print the **Letter of credit**, Click **View** on the Action pane, and then select **Print application**.

## Post Vendor payment journal for the created purchase invoice with letter of credit
1. Go to **Accounts payable > Payments > Payment journal**.
2. Click **New**.
3. In the **Name** field, select vendor payment journal name.
4. Click **Lines**.
5. In the **Date** field, enter a date.
6. In the **Account** field, select the vendor account from the Purchase Order. Click **Save**.
7. Click **Settle transactions**.
8. Select an invoice to pay. Verify that the **Bank document number** and **Shipment number** fields are correct.
9. Select the **Mark** checkbox for the invoice to pay. Click **OK**.
10. Select the **Payment** tab and verify that the **Bank document number** and **Shipment number** fields have been updated.
11. Click **Post**.

## Verify the Import letter of credit status after Invoice paid
1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. In the list, find and select the record.
3. Go to the **Lines** and verify the **Import letter of credit status** is **Confirmed** and **Shipment status** is **Paid**.
   
## Verify the Bank facility limit and utilization report
1. Go to **Cash and bank management > Inquiries and reports > Letters of credit or guarantee > Bank facilities and utilization report**.
2. Expand the **Records to include** section.
3. Click **Filter** and define the **Criteria** field with the required bank account.
4. Click **OK** and run the report.
5. Verify the report lists the transactions with Bank document number, Facility limit, utilized amount and the facility balance amount. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
