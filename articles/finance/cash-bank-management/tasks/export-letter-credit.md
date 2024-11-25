--- 
title: Export letter of credit
description: Learn about creating an export letter of credit, which is an agreement that is issued by a bank, including a step-by-step process. 
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 06/16/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable, CustBankAccounts, DefaultDashboard, SalesTableListPage, SalesCreateOrder, SalesTable, BankLCExport, SalesEditLines,  LedgerJournalTable, LedgerJournalTransCustPaym, CustOpenTrans
ms.dyn365.ops.version: Version 7.0.0 
---

# Export letter of credit

[!include [banner](../../includes/banner.md)]

This article describes exporting a letter of credit. For more information, see [Set up bank facilities and posting profiles for letter of credit](set-up-bank-facilities-posting-profiles-letter-credit.md) to configure and create bank facilities and posting profiles. 

## Create sales order for export letter of credit
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, select a desired record.
4. Expand the **General** section and fill **Site** and **Warehouse** fields.
 -  Select the **Site** and **Warehouse** where the item to be issued is stocked.
5. In the **Bank document type** field, select **Letter of credit**.
6. Expand the **Delivery** section and select **Delivery date control** = **None**.
7. Enter **Requested receipt date** and click **OK**.
8. On the Sales order lines, select an **Item number** which will be issued or sold.
9. Enter a **Unit price**, if it doesn't default from the price trade agreement.
10. Expand **Line details** section and select the **Delivery** tab.
11. Enter **Requested ship date** and **Confirmed ship date**.
12. On the Action pane, click **Manage**
13. Click **Letter of credit**.
14. Enter **Bank document number** and the **Expiration date**.
15. Expand **Bank details** section.
16. In the **Issuing bank** field, select the customer bank account.
17. Select the **Advising bank**.
18. On the **Lines**, click **Fetch sales order shipments**.
19. Click **Issue bank document**.

## Post Packing slip
1. On the **Sales order** page, click **Pick and pack**.
2. Click **Post packing slip**.
3. Expand the **Parameters** section and in the **Quantity** field, select **All**.
4. Enter a **Packing slip date** field.
5. Select the **Shipment number** and click **OK**.

## Post sales invoice
1. On the Action Pane, click **Invoice**.
2. Click **Invoice**.
3. Select the corresponding **Shipment number**.
4. In the **Setup** section, fill in the **Invoice date** and click **OK**.

## Shipment document submitted status
1. On the **Sales order**, click **Manage**.
2. Click **Letter of credit**.
3. Expand the **Lines** section.
>[!NOTE]
> The **Document submitted** field should be set to **Yes**.  

## Verify Export letter of credit
1. Go to **Cash and bank management > Letters of credit > Export letter of credit and import collection**.
2. Verify that the **Export letter of credit** has a **Shipment status** of **Invoiced** on the **Lines** section.

## Customer payment
1. Go to **Accounts receivable > Payments > Payment journal**.
2. Click **New**.
3. In the **Name** field, select customer payment journal name and click **Lines**.
4. Enter a **Date**.
5. In the **Account** field, select customer account number. Click **Save**.
6. Click **Settle transactions** and select an invoice to pay. Check **Bank document number** and **Shipment number**.
7. Select the **Mark** checkbox next to the invoice to pay. Click **OK**.
8. Click the **Payment** tab on the customer journal and verify the **Bank document number** and **Shipment number** details are filled.
9. Click **Post**.

## Verify Export letter of credit after payment
1. Go to **Cash and bank management > Letters of credit > Export letter of credit and import collection**.
2. Verify that the **Shipment status** = **Payment received** and **Balance amount** = **0.00**.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
