--- 
# required metadata 
 
title: Import letter of credit
description: This procedure walks through the process of importing a letter of credit. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendTable, VendBankAccounts, PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, BankLCImport,  PurchEditLines, VendEditInvoice, SrsReportViewerForm, LedgerJournalTable, LedgerJournalTransVendPaym, VendOpenTrans, SysQueryForm, BankAccountTableLookUp   
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
# Import letter of credit

[!include [banner](../../includes/banner.md)]

This procedure walks through the process of importing a letter of credit. The following must be set up before completing this procedure: bank facilities, posting profiles, a bank facility agreement and vendor bank details.

This procedure uses the USMF demo company.


## Create a Purchase order with Letter of credit
1. Go to **Accounts payable > Purchase orders > All purchase orders**.
2. Click **New**.
3. In the **Vendor account** field, enter or select a value.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Expand the **General** section.
7. In the **Site** field, enter or select a value.
8. In the list, click the link in the selected row.
9. In the **Warehouse** field, enter or select a value.
10. In the list, click the link in the selected row.
11. In the **Accounting date** field, enter a date.
12. In the **Delivery date** field, enter a date.

>[!Note] 
>The **Bank document type** field should be **Letter of credit**.  

13. Click **OK**.
14. In the **Item number** field, enter or select a value.
15. In the list, find and select the desired record.
16. In the list, click the link in the selected row.
17. Expand the **Line details** section.
18. Click the **Delivery** tab.
19. In the **Delivery date** field, enter a date.
20. In the **Confirmed delivery date** field, enter a date.
21. In the **Unit price** field, enter a number.
    * Define the Letter of credit details.  
22. On the Action Pane, click **Manage**.
23. Click **Letter of credit/import collection**.
24. In the **Application date** field, enter a date and time.
    * Verify that the **Bank account** field has the default active Bank account, which is based on the application date.  
25. In the **Bank document number** field, type a value.
26. In the **Date of receipt** field, enter a date and time.
27. Expand the **Bank document** section.
28. In the **Expiration date** field, enter a date and time.
29. Expand the **Bank details** section.
30. In the **Advising bank** field, enter or select a value.
31. In the list, click the link in the selected row.
32. Click **Save**.
33. Click **Fetch purchase order shipments**.
34. Close the page.
35. On the Action Pane, click **Purchase**.
36. Click **Confirm**.
37. On the Action Pane, click **Manage**.
38. Click **Letter of credit / import collection**.
39. Click **Process**.
40. Click **Confirm**.
    * Verify that the Facility balance reduces the purchase order amount. In this example, Purchase amount = 500.00,  Facility limit = 10000.00,  therefore, Facility balance = 9500.00.  
41. Close the page.
42. In the **Unit price** field, enter a number.
43. Click **Save**.
44. On the Action Pane, click **Purchase**.
45. Click **Confirm**.
    * Amend the letter of credit, due to the change in Unit price.  
46. On the Action Pane, click **Manage**.
47. Click **Letter of credit / import collection**.
    * Amend the letter of credit, due to the change in Purchase unit price.  
48. Click **Process**.
49. Click **Amend**.
50. Click **Remove**.
51. Click **Yes**.
52. Click **Fetch purchase order shipments**.
53. Click **Process**.
54. Click **Confirm**.
    * Verify that the Facility balance reduces the purchase order amount. In this example, edited Purchase amount = 600.00,  Facility limit = 10000.00,  therefore, Facility balance = 9400.00.  
55. Close the page.

## Post Packing slip
1. On the Action Pane, click **Receive**.
2. Click **Product receipt**.
3. In the **PurchParmTable_Num** field, type a value.
    * Select the **Shipment number** created with reference to the Letter of credit.  
4. In the list, click the link in the selected row.
5. In the **Product receipt date** field, enter a date.
6. Click **OK**.
7. Close the page.
8. Close the page.

## Verify Import letter of credit status
1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * Verify the **Import letter of credit status**.     
4. Close the page.
5. Close the page.

## Post purchase invoice
1. Go to **Accounts payable > Purchase orders > All purchase orders**.
    * Select the purchase order that was created with letter of credit.  
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. On the Action Pane, click **Invoice**.
5. Click **Invoice**.
6. In the **Number** field, type a value.
7. In the **Shipment number** field, enter or select a value.
8. In the list, click the link in the selected row.
9. In the **Invoice date** field, enter a date.
10. Click **Update match status**.
11. Click **Post**.
12. Close the page.
13. Close the page.

## Verify Import letter of credit status and printing

1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * Verify the Import letter of credit2.  
    * Validate:  **Shipment status** = **Invoiced**  Bank facility details  
4. Click **View**.
5. Click **Print application**.
6. Click **OK**.
    * Verify that the Letter of credit application gets printed.  
7. Close the page.
8. Close the page.
9. Close the page.

## Post Vendor payment journal for the created purchase invoice with letter of credit
1. Go to **Accounts payable > Payments > Payment journal**.
2. Click **New**.
3. In the **Name** field, enter or select a value.
4. In the list, click the link in the selected row.
5. Click **Lines**.
6. In the **Date** field, enter a date.
7. In the **Account** field, specify the desired values.
8. Click **Settle transactions**.
9. Expand the **Totals** section.
10. In the **Show** field, select an option.
    * Verify that the **Bank document number** and **Shipment number** fields have been updated.  
11. Select the **Mark** checkbox.
12. Click **OK**.
13. Click the Payment tab.
    * Verify that the **Bank document number** and **Shipment number** fields have been updated.  
14. Click **Post**.
15. Close the page.
16. Close the page.

## Verify Import letter of credit status after Invoice paid
1. Go to **Cash and bank management > Letters of credit > Import letter of credit and import collection**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
    * Verify the **Import letter of credit status**.   
4. Close the page.

## Verify the Bank facility limit and utilization report
1. Go to **Cash and bank management > Inquiries and reports > Letters of credit or guarantee > Bank facilities and utilization report**.
2. Expand the **Records to include** section.
3. Click **Filter**.
    * Define the **Criteria** field with the required bank account.  
4. In the **Criteria** field, enter or select a value.
5. In the list, click the link in the selected row.
6. Click **OK**.
7. Click **OK**.
    * Verify the report which lists the transactions.  
    * Verify the report lists the transactions with Bank document number, Facility limit, utilized amount and the facility balance amount.  
8. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
