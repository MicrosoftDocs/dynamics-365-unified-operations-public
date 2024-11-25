--- 
title: Set up bank facilities and posting profiles for letter of credit
description: Learn how to create a Bank facility and posting profile required to process Letters of credit. 
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 06/16/2024
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

This article describes how to set up bank facilities and posting profiles which are required to process letters of credit.

## Cash and bank management parameters
1. To enable import and export of letter of credit, go to **Cash and bank management > Setup > Cash and bank management parameters**.
2. Expand the **Bank document** section.
3. Select **Yes** for the **Enable import letter of credit** option.
4. Select **Yes** the **Enable export letter of credit** option.
5. Click **Save**.

## Create Bank facility
1. To create a bank facility, go to **Cash and bank management > Setup > Bank facilities**.
2. Click **New**.
3. In the **Facility group** field, enter the bank facility group name.
4. In the **Description** field, enter the bank facility group description.
5. Click **Save**.
6. Click the **Facility types** tab.
7. Click **New**.
8. In the **Facility type** field, enter a unique code.
9. In the **Description** field, type a value.
10. In the **Facility group** field, click the drop-down button to open the lookup and select a desired facility group record.
11. In the **Facility nature** field, select the nature of the bank facility.
12. Click **Save**.

## Bank posting profile
1. To configure a bank posting profile, go to **Cash and bank management > Setup > Bank documents posting profile**.
2. Click **New**.
3. In the **Account code** field, select **Group** to define a posting profile for a facility group, or **Table** to create a posting profile for a specific facility type.
4. In the **Account/Group number** field, click the drop-down button to see the lookup values and select required record.
5. Select the main account for settlement in the **Settle account** field. This account is used when calculating cash flow forecast.
6. In the **Charges account** field, select the account for expense transactions.
7. In the **Margin account** field, select the account for margin transactions. This account is debited when the opening margin is posted and credited when the payment is posted.
8. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
