--- 
title: Set up bank facilities and posting profiles for letter of credit
description: Learn how to create a Bank facility and posting profile required to process Letters of credit, including multiple step-by-step processes. 
author: kweekley
ms.author: kweekley
ms.topic: how-to
ms.date: 06/06/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: BankParameters, DefaultDashboard, BankDocumentSetup, BankDocumentPosting
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up bank facilities and posting profiles for letter of credit

[!include [banner](../../includes/banner.md)]

This document below explains the process of setting up bank facilities and posting profiles which are required to process letters of credit.

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
3. In the **Account code** field select **Group** if you would like to define a posting profile for a facility group, or **Table** to create a posting profile for a specific facility type.
4. In the **Account/Group number** field, click the drop-down button to see the lookup values.
5. In the list, find and select the desired record.
6. Select the main account for settlement in the **Settle account** field. This account is used when calculating cash flow forecast.  
8. In the **Charges account** field, select the account for expense transactions.
9. In the **Margin account** field, select the account for margin transactions. This account is debited when the opening margin is posted and credited when the payment is posted.  
10. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
