--- 
# required metadata 
 
title: Export letter of credit
description: This procedure walks through the process of the Export letter of credit. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, CustBankAccounts, DefaultDashboard, SalesTableListPage, SalesCreateOrder, SalesTable, BankLCExport, SalesEditLines,  LedgerJournalTable, LedgerJournalTransCustPaym, CustOpenTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Export letter of credit

[!include [banner](../../includes/banner.md)]

This procedure walks through the process of the Export letter of credit.

A letter of credit is an agreement that is issued by a bank, in which the bank agrees to ensure payment on behalf of the buyer, if the terms of the agreement between the buyer and seller are met.



Run the **Set up bank facilities and posting profiles** procedure and the **Letter of Credit_Create a bank facility agreement** procedure prior to this procedure. The USMF demo company must be selected in order to run this procedure successfully.


## Create Sales Order for Export letter of credit
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Expand or collapse the **General** section.
7. In the **Site** field, click the drop-down button to open the lookup.
    * Select the **Site** where the item to be issued is stocked.  
8. In the list, click the link in the selected row.
9. In the **Warehouse** field, click the drop-down button to open the lookup.
    * Select the **Warehouse** where item to be issued is stocked.  
10. In the list, click the link in the selected row.
    * Note: The **Bank document type** field should be selected with **Letter of credit**.  
11. In the **Bank document type** field, select **Letter of credit**.
12. Expand or collapse the **Delivery** section.
    * Select **Delivery date control** = **None**.  
13. In the **Requested receipt date** field, enter a date.
14. Click **OK**.
15. In the **Item number** field, click the drop-down button to open the lookup.
    * Select the required item to be Issued/Sold.  
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. In the **Unit price** field, enter a number.
19. Expand or collapse the **Line details** section.
20. Click the **Delivery** tab.
21. In the **Requested ship date** field, enter a date.
22. In the **Confirmed ship date** field, enter a date.
23. On the Action Pane, click **Manage**.
24. Click **Letter of credit**.
25. In the **Bank document number** field, type a value.
26. In the **Expiration date** field, enter a date and time.
27. Expand or collapse the **Bank details** section.
28. In the **Issuing bank** field, click the drop-down button to open the lookup.
29. In the list, click the link in the selected row.
30. In the **Advising bank** field, click the drop-down button to open the lookup.
31. In the list, find and select the desired record.
32. In the list, click the link in the selected row.
33. Click **Fetch sales order shipments**.
34. Click **Issue bank document**.
35. Close the page.

## Post Packing slip
1. On the Action Pane, click **Pick and pack**.
2. Click **Post packing slip**.
3. Expand or collapse the **Parameters** section.
4. In the **Quantity** field, select **All**.
5. Expand or collapse the **Setup** section.
6. In the **Packing slip date** field, enter a date.
7. Select the Shipment number.
8. In the list, click the link in the selected row.
9. Click **OK**.
10. Click **OK**.

## Post sales invoice
1. On the Action Pane, click **Invoice**.
2. Click **Invoice**.
3. Expand or collapse the **Overview** section.
4. Select the **Shipment number**.
5. In the list, click the link in the selected row.
6. Expand or collapse the **Setup** section.
7. In the **Invoice date** field, enter a date.
8. Click **OK**.
9. Click **OK**.

## Shipment document submitted status
1. On the Action Pane, click **Manage**.
2. Click **Letter of credit**.
3. Expand or collapse the **Lines** section.
    * Note: The **Document submitted** field should be set to **Yes**.  

## Verify Export letter of credit
1. Go to **Cash and bank management > Letters of credit > Export letter of credit and import collection**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * Verify that the **Export letter of credit** has a **Shipment status** of **Invoiced**.  

## Customer payment
1. Go to **Accounts receivable > Payments > Payment journal**.
2. Click **New**.
3. In the list, mark the selected row.
4. In the **Name** field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. Click **Lines**.
7. In the **Date** field, enter a date.
8. In the **Account** field, specify the desired values.
9. Click **Settlement**.
10. Select the check box on the header of Totals.
    * Note: Set the **Show** field to **Letter of credit**.  
11. In the list, find and select the desired record.
12. Select or clear the **Mark** check box.
13. Click **OK**.
14. Click the **Payment** tab.
    * Verify the Bank document number and Shipment number details  
15. Click **Post**.

## Verify Export letter of credit after payment
1. Go to **Cash and bank management > Letters of credit > Export letter of credit and import collection**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * Verify that the **Shipment status** = **Payment received** and **Balance amount** = **0.00**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
