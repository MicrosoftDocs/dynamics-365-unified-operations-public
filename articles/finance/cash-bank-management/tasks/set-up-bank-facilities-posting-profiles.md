--- 
# required metadata 
 
title: Set up bank facilities and posting profiles for letters of guarantee
description: This task creates a Bank facility and posting profile that is needed to process a letter of guarantee. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BankParameters, DefaultDashboard, BankDocumentSetup, BankDocumentPosting   
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
# Set up bank facilities and posting profiles for letters of guarantee

[!include [banner](../../includes/banner.md)]

This task creates a Bank facility and posting profile that is needed to process a letter of guarantee.



This task uses the USMF demo company. 




## General ledger parameter
1. Go to **Cash and bank management > Setup > Cash and bank management parameters**.
2. Expand the **Bank document** section.
3. Select the **Enable letter of guarantee** option.
4. In the **Transaction journal** field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
6. In the list, click the link in the selected row.
7. Click the **Number sequences** tab.
    * Define number sequence code for Letter of guarantee number and Letter of guarantee transaction references  
8. Click **Save**.
9. Close the page.

## Create Bank facility
1. Go to **Cash and bank management > Setup > Bank facilities**.
2. Click **New**.
3. In the **Facility group** field, enter the bank facility group name for the letter of guarantee transaction.
4. In the **Description** field, type a value.
5. Click **Save**.
6. Click the **Facility types** tab.
7. Click **New**.
8. In the **Facility type** field, enter the name of the bank facility type that is related to the bank facility agreement.
9. In the **Description** field, type a value.
10. In the **Facility group** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the list, click the link in the selected row.
13. In the **Facility nature** field, select an option.
14. Click **Save**.
15. Close the page.

## Bank posting profile
1. Go to **Cash and bank management > Setup > Bank documents posting profile**.
2. Click **New**.
3. In the **Account/Group number** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the **Settle account** field, select the main account for settlement.
7. In the **Charges account** field, select the account for expense transactions.
8. In the **Margin account** field, select the account for the margin transaction.
9. In the **Liquidation account** field, select the liquidation account for the letter of guarantee transaction. 
10. Click **Save**.
11. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
