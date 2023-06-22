--- 
# required metadata 
 
title: Letter of guarantee transaction
description: This procedure walks through the Letter of guarantee process. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Reasons, SalesTableListPage, SalesCreateOrder, SalesTable, BankLGRequestForm, BankLGRequestFormRequest, BankLGGuarantee, BankLGFormSubmitToBank, BankDocumentAgreementLineLookup, BankLGFormReceiveFromBank, LedgerJournalTable, LedgerJournalTransDaily, BankLGRequestFormGiveToBeneficiary, BankLGFormGiveToBeneficiary, BankLGRequestFormIncreaseValue, BankLGFormIncreaseValue, BankLGRequestFormLiquidate, BankLGFormLiquidate   
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
# Letter of guarantee transaction

[!include [banner](../../includes/banner.md)]

This procedure walks through the Letter of guarantee process.



The following tasks must be complete before completing this procedure:

- Set up bank facilities and posting profiles for a letter of guarantee.

- Create a bank facility agreement for a letter of guarantee.



This procedure uses the USMF demo company.


## Create Sales Order with Letter of Guarantee
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, enter or select a value.
4. Expand the **General** section.
5. In the **Site** field, enter or select a value.
6. In the list, click the link in the selected row.
7. In the **Warehouse** field, enter or select a value.
8. In the list, click the link in the selected row.
9. In the **Bank document type** field, select **Letter of guarantee**.
10. Click **OK**.
11. In the **Item number** field, enter or select a value.
12. In the **Unit price** field, enter a number.
13. Expand the **Line details** section.
14. Click the **Delivery** tab.

>[!Note] 
>Select **Delivery date control** = **None**  

15. In the **Requested ship date** field, enter a date.
16. In the **Confirmed ship date** field, enter a date.

## Process letter of guarantee_Request
1. On the Action Pane, click **Manage**.
2. Click **Letter of guarantee**.
3. On the Action Pane, click **Letter of guarantee**.
4. Click **Request** to open the drop dialog.
5. In the **Type** field, enter or select a value.
6. In the list, click the link in the selected row.
7. In the **Value** field, enter a number.
8. In the **Expiration date** field, enter a date and time.
9. Click **OK**.
10. Close the page.

## Process letter of guarantee_Submit to bank
1. Go to **Cash and bank management > Letters of guarantee > Letters of guarantee**.
2. In the list, find and select the desired record.
3. Click **Submit to bank** to open the drop dialog.
4. In the **Bank account** field, enter or select a value.
5. In the list, click the link in the selected row.
6. Click **OK**.

## Process letter of guarantee_Receive from bank
1. Click **Receive from bank** to open the drop dialog.
2. In the **Bank number** field, type a value.
    * Verify the values in the calculated **Margin** and **Expense** fields.  
3. Click **OK**.
4. Expand the **Actions** section.
    * Verify the 'Receive from bank' record.  
5. Click to follow the link in the **Journal batch number** field.
6. Click **Lines**.
    * Verify the posting of journal entries.  
7. Close the page.

## Process letter of guarantee_Give to beneficiary
1. Go to **Accounts receivable > Orders > All sales orders**.
2. In the list, click the link in the selected row.
3. On the Action Pane, click **Manage**.
4. Click **Letter of guarantee**.
5. On the Action Pane, click **Letter of guarantee**.
6. Click **Give to beneficiary** to open the drop dialog.
7. Click **OK**.
8. Go to **Cash and bank management > Letters of guarantee > Letters of guarantee**.
9. In the list, find and select the desired record.
10. Click **Give to beneficiary** to open the drop dialog.
11. Click **OK**.
12. Expand the **Actions** section.
    * Validate the 'Give to beneficiary' record.  

## Process letter of guarantee_Increase value
1. Go to **Accounts receivable > Orders > All sales orders**.
2. In the list, click the link in the selected row.
3. On the Action Pane, click **Manage**.
4. Click **Letter of guarantee**.
5. On the Action Pane, click **Letter of guarantee**.
6. Click **Increase value** to open the drop dialog.
7. In the **Value to add** field, enter a number.
8. Click **OK**.
9. Go to **Cash and bank management > Letters of guarantee > Letters of guarantee**.
10. In the list, find and select the desired record.
11. Click **Increase value** to open the drop dialog.
12. Click **OK**.
13. Expand the **Actions** section.
    * Verify the 'Increase value' record.  
14. In the list, find and select the desired record.
15. Click to follow the link in the **Journal batch number** field.
16. Click **Lines**.
    * Verify the posted journal entries.  

## Process letter of guarantee_Liquidate
1. Go to **Accounts receivable > Orders > All sales orders**.
2. In the list, click the link in the selected row.
3. On the Action Pane, click **Manage**.
4. Click **Letter of guarantee**.
5. On the Action Pane, click **Letter of guarantee**.
6. Click **Liquidate** to open the drop dialog.
7. Click **OK**.
8. Go to **Cash and bank management > Letters of guarantee > Letters of guarantee**.
9. In the list, find and select the desired record.
10. Click **Liquidate** to open the drop dialog.
11. Click **OK**.
12. Expand the **Actions** section.
    * Verify the 'Liquidate' record.  
13. In the list, find and select the desired record.
14. Click to follow the link in the **Journal batch number** field.
15. Click **Lines**.
    * Verify the posted journal entries.  
16. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
