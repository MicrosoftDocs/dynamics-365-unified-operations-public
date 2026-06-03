--- 
title: Set up bank facilities and posting profiles for letter of credit
description: Learn how to create a Bank facility and posting profile required to process Letters of credit. 
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 05/27/2026
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

This article describes how to set up bank facilities and posting profiles that you need to process letters of credit.

## Cash and bank management parameters

1. To enable import and export of letter of credit, go to **Cash and bank management > Setup > Cash and bank management parameters**.
1. Expand the **Bank document** section.
1. Select **Yes** for the **Enable import letter of credit** option.
1. Select **Yes** for the **Enable export letter of credit** option.
1. Select **Save**.

## Create bank facility

1. To create a bank facility, go to **Cash and bank management > Setup > Bank facilities**.
1. Select **New**.
1. In the **Facility group** field, enter the bank facility group name.
1. In the **Description** field, enter the bank facility group description.
1. Select **Save**.
1. Select the **Facility types** tab.
1. Select **New**.
1. In the **Facility type** field, enter a unique code.
1. In the **Description** field, enter a value.
1. In the **Facility group** field, select the drop-down button to open the lookup and select a desired facility group record.
1. In the **Facility nature** field, select the nature of the bank facility.
1. Select **Save**.

## Bank posting profile

1. To configure a bank posting profile, go to **Cash and bank management > Setup > Bank documents posting profile**.
1. Select **New**.
1. In the **Account code** field, select **Group** to define a posting profile for a facility group, or **Table** to create a posting profile for a specific facility type.
1. In the **Account/Group number** field, select the dropdown button to see the lookup values and select the required record.
1. Select the main account for settlement in the **Settle account** field. Use this account when calculating the cash flow forecast.
1. In the **Charges account** field, select the account for expense transactions.
1. In the **Margin account** field, select the account for margin transactions. This account is debited when the opening margin is posted and credited when the payment is posted.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
