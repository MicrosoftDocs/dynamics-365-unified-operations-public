--- 
# required metadata 
 
title: Set up bank facilities and posting profiles for letter of credit
description: This procedure walks through creating a Bank facility and posting profile required to process Letters of credit. 
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
# Set up bank facilities and posting profiles for letter of credit

[!include [banner](../../includes/banner.md)]

This procedure walks through creating a Bank facility and posting profile required to process Letters of credit. 

This tasks uses the demo company 'USMF'.


## General ledger parameter
1. Go to **Cash and bank management > Setup > Cash and bank management parameters**.
2. Expand the **Bank document** section.
3. Select the **Enable import letter of credit** option.
4. Select the **Enable export letter of credit** option.
5. Click **Save**.
6. Close the page.

## Create Bank facility
1. Go to **Cash and bank management > Setup > Bank facilities**.
2. Click **New**.
3. In the **Facility group** field, enter the bank facility group name.
4. In the **Description** field, enter the bank facility group description.
5. Click **Save**.
6. Click the **Facility types** tab.
7. Click **New**.
8. In the **Facility type** field, enter a unique code.
9. In the **Description** field, type a value.
10. In the **Facility group** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the list, click the link in the selected row.
13. In the **Facility nature** field, select the nature of the bank facility.
14. Click **Save**.
15. Close the page.

## Bank posting profile
1. Go to **Cash and bank management > Setup > Bank documents posting profile**.
2. Click **New**.
3. In the **Account/Group number** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Select the main account for settlement.
    * This account is used when calculating cash flow forecast.  
7. In the **Charges account** field, select the account for expense transactions.
8. In the **Margin account** field, select the account for margin transactions.
    * This account is debited when the opening margin is posted and credited when the payment is posted.  
9. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
